---
title: Chrome Extension - Synced VODs for Twitch
date: 2021-06-30T22:16:05.896Z
description: Developing a Chrome extension to help you sync Twitch VODs with your friend.
---
# Introduction

Have you ever had a problem where you and your friend are watching a VOD on Twitch but you just don't know where exactly he's at and have to continuously ask him to tell you the time so you can watch the VOC in sync? This chrome extension aims to solve this problem by letting you see which VOD your friend is watching and the exact timestamp he's at.

Below you can see the architecture and data flow between multiple extensions and an instance of Node.js server:

![Architecture - data flow](/img/schema.png "Architecture - data flow")

1. User is watching Twitch VOD and has Synced VODs extension installed
2. Extension is sending data about VOD's current timestamp to the server
3. Server receives information through Websocket connection
4. Server sends information to all other Synced VODs extensions connected to it

# Implementation

## Basic extension

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

## Node.js server

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

Back in our extension code, we add the below code to the` background.js` script:

```javascript
let HOST = "wss://" + herokuAppUrl
let ws = new WebSocket(HOST);
let el;

ws.onmessage = (event) => {
    console.log('Recieved data ',  event.data)
};
```

If we run the extension, it should return server time every second:

![Websockets intro](/img/sockets.jpg "Extension receives server response")