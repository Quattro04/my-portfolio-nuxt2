---
title: SyncedVODs for Twitch Chrome Extension
date: 2021-06-30T22:16:05.896Z
description: Developing a Chrome extension to help you sync Twitch VODs with your friend.
---
### Introduction

Have you ever had a problem where you and your friend are watching a VOD on Twitch but you just don't know where exactly he's at and have to continuously ask him to tell you the time so you can watch the VOC in sync? This Chrome extension aims to solve this problem by letting you see which VOD your friend is watching and the exact timestamp he's at.

I will try to describe in detail how I programmed this extension.



### Programming

First thing I decided to do was make a basic extension that can detect site URL and just display it in the console. I made a background script for that in `background.js`:

`chrome.tabs.onUpdated.addListener( function (tabId, changeInfo, tab) {`

`    if (changeInfo.status == 'complete') {`

`        console.log('Got site url: ', tab,url)`

`    }`

`})`