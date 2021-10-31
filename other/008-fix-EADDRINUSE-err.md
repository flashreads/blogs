---
id: 008-fix-EADDRINUSE-err
title: How to fix EADDRINUSE error
tags: 
    - EADDRINUSE
    - nodejs
    - server errors
date: 2021-10-24 19:58:00 +0200 
keywords: EADDRINUSE, nodejs, server error
categories: 
    - other
author: ElizabetYessiien
meta-description: How to kill a port and fix the EADDRINUSE err
cover: ../../images/categories/other.png
---

Here's an interesting error you can come across when working with nodejs servers:

Error: listen EADDRINUSE: address already in use :::5000

at Server.setupListenHandle [as \_listen2] (net.js:1318:16)

at listenInCluster (net.js:1366:12)

at Server.listen (net.js:1452:7)

Emitted 'error' event on Server instance at:

at emitErrorNT (net.js:1345:8)

at processTicksAndRejections (internal/process/task\_queues.js:80:21) {

code: 'EADDRINUSE',

errno: -4091,

syscall: 'listen',

address: '::',

port: 5000

}

[nodemon] app crashed - waiting for file changes before starting...

I know for a fact that port 5000 was only in use for this app.

My question was, what is EADDRINUSE(which I hurriedly read as ear in use). It simply means that you have multiple instances of your server running or multiple node.

As easy fix for this before you go on to read multiple confusing stack overflow posts is to find your PID. Nope, that is not the pelvic inflammatory disease. It is referring to your process identifier.

Each process can be identified and to find it, you need the following command:

netstat -ano | findstr :5000

5000 is the problem port in my case, but it could be 3000 for you. So, the port number is basically what you need to type immediately after the colon.

netstat -ano | findstr :portnumberhere

Then, you need to kill what will be displayed in your terminal for that port. In mine, I was shown this:

$ netstat -ano | findstr :5000

TCP 0.0.0.0:5000 0.0.0.0:0 LISTENING 7440

TCP [::]:5000 [::]:0 LISTENING 7440

the number 7440 is the PID, so the command to kill it after identifying it is:

tskill 7440

You can also use taskkill 7400(remember, 7400 is the PID for you), although it might not work sometimes.

Everything is now running and problem solved:)
