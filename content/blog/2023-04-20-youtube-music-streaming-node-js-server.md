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

F﻿or this Node.js application, we will need ffmpeg executable, which you can get [here](https://www.ffmpeg.org/download.html)

D﻿ownload the correct one for you system, make a new directory which will be this project's root directory, and place it inside.

## G﻿etting started

Navigate to your project dir and initialize your project using npm by running the following command:

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

N﻿ext, create index.js file that will be your main Node.js file and paste the following code inside:

```
// index.js

const express = require('express');
const ytdl = require('ytdl-core')
const FFmpeg = require('fluent-ffmpeg')
const { PassThrough } = require('stream')
const fs = require('fs')
const app = express();

const toAudioStream = (uri, opt) => {
    opt = {
        ...opt,
        videoFormat: 'mp4',
        quality: 'lowest',
        audioFormat: 'mp3',
        filter (format) {
            return format.container === opt.videoFormat && format.audioBitrate
        }
    }

    const video = ytdl(uri, opt)
    const { file, audioFormat } = opt
    const stream = file ? fs.createWriteStream(file) : new PassThrough()
    const ffmpeg = new FFmpeg(video)

    process.nextTick(() => {
        const output = ffmpeg.format(audioFormat).pipe(stream)
    
        ffmpeg.once('error', error => stream.emit('error', error))
        output.once('error', error => {
            video.end()
            stream.emit('error', error)
        })
    })

    stream.video = video
    stream.ffmpeg = ffmpeg

    return stream
}

const streamify = async (url, res) => {
    toAudioStream(url).pipe(res);
}

app.get('/', async (req, res) => {
    const id = req.query.id;

    try {
        await streamify(`https://youtube.com/watch?v=${id}`, res)
    } catch (err) {
        console.error(err)
        if (!res.headersSent) {
            res.writeHead(500)
            res.end('internal system error')
        }
    }
});

app.listen(3000, () => {
    console.log('Server listening on port 3000');
});

```