---
title: Making your own music streaming server with Node.js and Next.js for free
date: 2023-04-18T14:37:32.111Z
description: Tired of paying for music? Let's dive into detailed guide about
  writing your own music streaming service which will take care of that for
  free!
---
# Introduction

I﻿f you are like me and got tired of ads and ever more expensive music streaming providers like Spotify, YouTube Music or Apple Music then you are in the right place. In this blog, I will describe in detail how to write your own music streaming server using Next.js on the frontend and Node.js on the backend.

First, let's start with the backbone of our application, which is Node.js server.

# N﻿ode.js

Node.js is a popular runtime environment for server-side applications that allows developers to build scalable and high-performance servers. In this blog, we'll be building a simple streaming server using Node.js, lowdb, and Express that will allow us to serve MP3 files and return a list of songs stored in a JSON database. It will also store all the songs as MP3 files on the server itself.

## Prerequisites

Before we dive into coding, let's make sure you have the following prerequisites:

1. Node.js and NPM installed on your computer.
2. Basic understanding of JavaScript and Node.js.
3. Basic understanding of HTTP and RESTful APIs.

## Getting Started

To get started, create a new directory for your project and navigate into it. Then, initialize your project using npm by running the following command:

```
npm init -y
```

This will create a new package.json file with default values. Next, install the following packages:

```
npm install express lowdb multer morgan cors
```

Here's what each package does:

* Express: A web application framework for Node.js that provides a set of features for building web applications.
* lowdb: A lightweight JSON database for Node.js that provides a simple way to store and retrieve data.
* multer: A middleware for handling file uploads in Express.
* morgan: A logging middleware for Express that logs HTTP requests to the console.
* cors: A middleware for enabling CORS (Cross-Origin Resource Sharing) in Express.

Once you've installed these packages, create a new file called `server.js` and add the following code: