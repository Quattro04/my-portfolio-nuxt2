---
title: YouTube music streaming Node.js server
date: 2023-04-20T14:05:37.911Z
description: Want a node.js server that will stream music from YouTube on
  request for free and without the need of Google API? Look no further.
---
# I﻿ntroduction

W﻿e will make a simple Node.js server that gets YouTube video id on request and returns an audio stream of that video. So let's get started.

# A﻿pplication

## Prerequisites

F﻿or this Node.js application, we will need 

To get started, create a new directory for your project and navigate into it. Then, initialize your project using npm by running the following command:

```
npm init
```

This will create a new package.json file with default values. Next, install the following packages:

```
npm install express ytdl-core fluent-ffmpeg stream fs
```

Here's what each package does:

* [express](https://www.npmjs.com/package/express): A web application framework for Node.js that provides a set of features for building web applications.
* [ytdl-core](https://www.npmjs.com/package/ytdl-core): YouTube downloading module - to get video from YouTube.
* [fluent-ffmpeg](https://www.npmjs.com/package/fluent-ffmpeg): Easy to use Node.js friendly ffmpeg module - to get audio from video.
* [stream](https://www.npmjs.com/package/stream): Module for streaming.
* [fs](https://www.npmjs.com/package/fs): File system module.