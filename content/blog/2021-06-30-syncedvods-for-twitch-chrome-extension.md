---
title: Chrome Extension - Synced VODs for Twitch
date: 2021-06-30T22:16:05.896Z
description: Developing a Chrome extension to help you sync Twitch VODs with your friend.
code:
  code: ""
  lang: javascript
---
### Introduction

Have you ever had a problem where you and your friend are watching a VOD on Twitch but you just don't know where exactly he's at and have to continuously ask him to tell you the time so you can watch the VOC in sync? This chrome extension aims to solve this problem by letting you see which VOD your friend is watching and the exact timestamp he's at.

Below you can see the architecture and data flow between multiple extensions and an instance of Node.js server:

![Architecture - data flow](/img/schema.png "Architecture - data flow")

1. User is watching Twitch VOD and has Synced VODs extension installed
2. Extension is sending data about VOD's current timestamp to the server
3. Server receives information through Websocket connection
4. Server sends information to all other Synced VODs extensions connected to it

### Implementation

#### Basic extension

First thing I decided to do was make a basic extension that can detect site URL and just display it in the console. I made a background script for that in `background.js`:

```javascript
chrome.tabs.onUpdated.addListener( function (tabId, changeInfo, tab) {
    if (changeInfo.status == 'complete') {
        console.log('Site URL ', tab.url)
    }
})
```

This uses `tabs` API to get an active tab and then if tab is fully loaded, displays tab URL in the console. Now let's make an actual extension to use this background script on. We'll need another file, `manifest.json`:

```json
{
    "name": "Synced VODs for Twitch",
    "description": "Sync Twitch VODs with your friends!",
    "version": "1.0",
    "manifest_version": 3,
    "background": {
        "service_worker": "background.js"
    },
    "permissions": ["tabs"]
}
```

Here we defined extension name, description, version, witch script to use for background script and also specified permissions. Because we used `chrome.tabs` API, we'll need `tabs` permission.

Now we need to add the extension to chrome and we do that by opening chrome and going to `Settings -> Extensions -> Developer Mode ON -> Load unpacked` then select the extension folder that includes the above files. You will now see your extension on the list and can inspect service workers. This will open the console which will display the URL of any site we visit.

![Chrome extension panel](/img/extension.jpg "Chrome extension panel")

#### Node.js server

First we're going to implement a basic Node.js server that sends current time to all connected clients through **Websocket**. It will be hosted on [Heroku](heroku.com), which is a free hosting service.

The server code that initializes Websocket, listens for connections on port 3000 and sends current time to all connected clients every second:

```javascript
const express = require('express');
const { Server } = require('ws');

const PORT = process.env.PORT || 3000;

const server = express()
    .listen(PORT, () => console.log(`Listening on ${PORT}`));

const wss = new Server({ server });

wss.on('connection', (ws) => {
    console.log('Client connected');
    ws.on('close', () => console.log('Client disconnected'));
});

setInterval(() => {
    wss.clients.forEach((client) => {
        client.send(new Date().toTimeString());
    });
}, 1000);
```

We can simply add this to a git repo and then in Heroku dashboard, add App from this repo. This will deploy the code and Heroku provides us with the dedicated URL this server is reachable at.

Back in our extension code, we add the below code to the `background.js` script:

```javascript
let HOST = "wss://" + herokuAppUrl
let ws = new WebSocket(HOST);

ws.onmessage = (event) => {
    console.log('Recieved data ',  event.data)
};
```

If we run the extension, it should log time returned from server every second:

![Websockets intro](/img/sockets.jpg "Extension receives server response")

#### Sending the data

Now that we have Node.js server and chrome extension that connect using Websockets, we need to make sure we send the correct data.

If user is watching a Twitch VOD, chrome extension needs to send timestamp and url parameters to Node.js every second. This can be done with a **content script**, which is a script that is injected in the webpage. Consequentially,  it has access to the webpage's DOM, so we can get the element that contains the timestamp, read it and send it to background script which then sends it to Node.js.

First we make `content.js` file:

```javascript
setInterval(() => {
    let element = $('*[data-a-target="player-seekbar-current-time"]');
    // Check if element exists
    if (element.length > 0) {
        // Send timestamp to background.js
        chrome.runtime.sendMessage({ timestamp: element.text() });
    }
}, 1000)
```

And include it in `manifest.json`, along with **jQuery**:

```javascript
"content_scripts": [{
    "matches": ["https://*.twitch.tv/*"],
    "js": ["jquery-3.6.0.min.js", "content.js"]
}],
```

In `background.js`, we need to make sure it will receive the timestamp, so we add the listener:

```javascript
chrome.runtime.onMessage.addListener(request => {
    chrome.tabs.query({active: true, currentWindow: true}, tabs => {
        ws.send(JSON.stringify({ url: tabs[0].url, timestamp: request.timestamp }))
    })
});
```

See how we not only send the timestamp of the VOD to the Node.js, but url of the VOD too, which we get from `chrome.tabs`.

On the server side, we adjust on-connection script to send the received data to all clients except the one that is sending it:

```javascript
wss.on('connection', (ws, req) => {
    console.log('Client connected: ', req.socket.remoteAddress);
    ws.on('close', () => console.log('Client disconnected'));
    ws.on('message', data => {
        wss.clients.forEach(client => {
            if (client !== ws) client.send(data);
        });
    });
});
```

In `background.js`, we need to change `ws.onmessage` to send the received data to **popup**, which will display it to the user:

```javascript
ws.onmessage = (event) => {   
    // Send message to popup
    chrome.runtime.sendMessage({type: "popup_data", data: JSON.parse(event.data)});
};
```

#### Popup

For the popup, we make a simple HTML `popup.html` that displays the url and the timestamp we get from Node.js:

```html
<!DOCTYPE html>
<html>
    <head>
        <link rel="stylesheet" href="button.css">
    </head>
    <body>
        <span id="url"></span>
        <span id="timestamp"></span>
        <script src="popup.js"></script>
    </body>
</html>
```

And in `popup.js`, we receive the data from `background.js` and inject it into HTML:

```javascript
chrome.runtime.onMessage.addListener(
    function(request, sender, sendResponse) {
        if (request.type === "popup_data") {
            document.getElementById("url").innerHTML = request.data.url;
            document.getElementById("timestamp").innerHTML = request.data.timestamp;
        }
    }
);
```

And thats it! When another user that has the extension installed is watching a Twitch VOD, our extension will display url and timestamp of it and will be updating it every second:

![Finalized extension](/img/ext.jpg "Finalized extension")

### Conclusion

This is just a basic version of the extension, possible additional features include:

* Support for more than 2 users, possibly with usernames for identification
* Popup styling and a button that opens the VOD with at a the correct time directly
* Include other information of what a user is doing on Twitch

Thanks for reading and see you in the next one 😊