---
id: 016-curl-post-json-data.md
title: Post JSON data with curl
tags: 
  - linux
  - curl
  - rest
  - json
author: Pavle Jonoski
meta-description: Learn how to post JSON data with curl
date: 2022-10-29 21:00:00 +0200 
keywords: linux, curl, rest, json
template: post
categories:
  - linux
image: assets/images/transfer.svg
---

# Post JSON data with curl

[`curl`](https://theflashreads.com/curl-howto) is a very convenient command line tool to send HTTP (and [many others](https://curl.se/) types of) requests to a server.

Sending JSON data is very easy with curl. You can send the JSON data itself as a command line parameter or you can load it from a file.

To send it directly from the command line, use the `--data` (or `-d`) parameter:

```bash
curl \
    -H "Content-Type: application/json" \
    --data '{"message": "Hello World!"}' \
    http://example.com
```

**Don't forget** the `Content-Type` header, as many server will deny the parsing of JSON when the content type header is missing.

**Note:** Also note that by default when setting `-d` (or `--data`) the HTTP request is actually a `POST` request.

## Load the JSON data from a file

You can also load the JSON request body from a file.

First create the file (let's call it `data.json`):

```json
{
    "message": "Hello World!"
}
```

Then send it using `@` before the file name in the `--data` parameter:

```bash
curl \
    -H "Content-Type: application/json" \
    --data @data.json \
    http://example.com
```
