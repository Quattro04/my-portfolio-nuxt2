---
title: Synced VODs for Twitch Chrome Extension
date: 2021-06-30T22:16:05.896Z
description: Developing a Chrome extension to help you sync Twitch VODs with your friend.
---
### Introduction

Have you ever had a problem where you and your friend are watching a VOD on Twitch but you just don't know where exactly he's at and have to continuously ask him to tell you the time so you can watch the VOC in sync? This Chrome extension aims to solve this problem by letting you see which VOD your friend is watching and the exact timestamp he's at.

I will try to describe in detail how I programmed this extension.

### Programming

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