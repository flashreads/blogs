---
id: 014-curl-howto.md
title: curl command usage short guide
tags: 
  - linux
  - curl
author: waltherman
meta-description: Curl is data transfer command. This is curl short command guide with examples
date: 2021-10-14 03:40:00 +0300 
keywords: linux, curl, url, data transfer, api testing
template: post
categories:
  - linux
image: assets/images/transfer.svg
---

# Curl

Curl is a tool for data transfer. It supports a variety of protocols - HTTP, HTTPS, FTP, SFTP, TFTP, IMAP, POP3, SCP, SMTP and a bunch of other protocols, full list is available in man output.
It is tiny, flexible, could provide verbose information, good for automation, since user interaction witch curl is not needed.

## Curl usage

Syntax is simple:
```
$ curl [options] [URL]
```

The basic request to GitHub would be look like:
```
$ curl github.com
```
Downloading files with the same name, as in the URL
```
$ curl -O [URL]
```
Or with specific file name:
```
$ curl -o [filename] [URL]
```
Continue downloading of stopped download is possible with "-C" parameter
```
$ curl -C -O [URL]
```
Verbose output
```
$ curl -v [options] [URL]
$ curl --verbose [options] [URL]
```
Authenticate on remote server
```
$ curl -u {username}:{password} [URL]
```
For example, download FTP file with authentication would look like:
```
$ curl -u ftpuser16:Password111 -O ftp://example.com/bugrep.tgz
```
File upload:
```
$ curl -T -u {username}:{password} [URL]
```

Progress bar:
It is possible to change curl meter to progress bar:
```
$ curl -# [URL]
$ curl --progress-bar [URL]
```

Or disable any progress information:
```
$ curl -s [URL]
$ curl --silent [URL]
```

HTTP and HTTPS:
Include HTTPS headers to output
```
$ curl -i https://github.com
$ curl --include https://github.com
```
Specify HTTP-request type:
```
$ curl --request [request type] [options] [URL]
```
Example
```
$ curl --request GET https://github.com
```
Proxy server also could be specified:
```
curl -x [proxy address]:[port] [URL]
```
If proxy server requires authentication, curl can be used with next command:
```
curl -x [proxy address]:[port] -U [user]:[password] [URL]
curl -x [proxy address]:[port] --proxy-user [user]:[password] [URL]
```

SMTP
If you do not like to send emails via telnet you could use curl 
```
$ curl –url [SMTP URL] –mail-from [sender address] –mail-rcpt [recipient address] -n –ssl-reqd -u {email}:{password} -T [mail text file]
```
