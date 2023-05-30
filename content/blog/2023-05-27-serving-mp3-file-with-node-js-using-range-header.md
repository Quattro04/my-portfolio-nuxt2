---
title: Serving mp3 file with Node.js using Range header
date: 2023-05-27T08:50:09.202Z
description: How to utilize Range header to serve mp3 chunk by chunk so user
  receives it quickly and exactly when needed.
---
# I﻿ntroduction

In today's digital era, where media consumption is at an all-time high, providing a seamless audio experience to users is crucial. One powerful technique for enhancing audio delivery is through the use of Range headers. In this blog post, we'll explore how to leverage the capabilities of Node.js to serve MP3 files efficiently, utilizing Range headers to play audio on user's side with practically no delay while at the same time, not downloading whole song at the beginning, thus preserving downloaded data.

# G﻿etting Started

L﻿et's start with Node.js server which will serve our mp3 files.

## N﻿ode.js

W﻿e'll make a simple Node.js-express server which will serve files in our public folder.

F﻿older structure:

![folder-structure](/img/structure.jpg "Folder Structure")

S﻿o our main server file is server.js, which looks like this:

```javascript
import { join, dirname } from 'node:path'
import { fileURLToPath } from 'node:url'

import express from 'express';
import http from 'http';
import fs from 'fs';

// Set up express app and create HTTP server
const app = express();
app.use(express.json({ extended: true }));

const server = http.createServer(app);
const __dirname = dirname(fileURLToPath(import.meta.url));

app.get('/songs/:name', (req, res) => {
   
    // Here we'll implement logic for handling song requests with Range header

})

server.listen(process.env.PORT || 3000, () => {
    console.log(`Server listening on port ${process.env.PORT || 3000}`);
});
```

W﻿e can see that we have one endpoint: /songs/:name, where request will come in for the song. In our /public/songs folder, we have best-song.mp3 file, which we will send to user in chunks.

Let's implement the endpoint so it will do just that.

```javascript
const name = req.params.name;
const filePath = join(__dirname, `/public/songs/${name}`);
const stat = fs.statSync(filePath);
const fileSize = stat.size; // Whole file size in bytes
const range = req.headers.range;
```

F﻿irst we get name parameter from request params and with file path, get the file's size. We will need it for later.

W﻿e also get the range value, which is set in the headers. This value will be a string and look like this:

```
Range bytes=0-500
```

T﻿he client here wants first 500 bytes of the song instead of the whole song. Let's do that next.

```javascript
const rangeArr = range.split('=')[1].split('-'); // Parse start and end bytes from Range header in an array

const start = rangeArr[0]; // First value in array is start of bytes
const end = rangeArr[1];   // Second value in array is end of bytes

const chunkSize = (end - start); // Size of the chunk to send
const fileStream = fs.createReadStream(filePath, { start, end }); // Actual chunk of the song we'll send
const headers = {
    'Content-Range': `bytes ${start}-${end}/${fileSize}`,
    'Accept-Ranges': 'bytes',
    'Content-Length': chunkSize,
    'Content-Type': 'audio/mpeg',
};

res.writeHead(206, headers); // Write status code and headers to response
fileStream.pipe(res); // Send the chunk over to client
```