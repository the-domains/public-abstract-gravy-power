---
inFeed: true
hasPage: true
inNav: false
inLanguage: null
starred: false
keywords: []
description: "Ran into an issue with where I could not start nginx. The error \"[emerg] listen() to 0.0.0.0:80, backlog 511 failed (98: Address already in use)\" would show up in the error log. \_To combat this I took advantage of the \"fuser\" command."
datePublished: '2016-04-13T23:55:15.022Z'
dateModified: '2016-04-13T23:54:32.879Z'
title: ' 0.0.0.0:80 Address already in use WTF?!'
author: []
authors: []
publisher:
  name: null
  domain: null
  url: null
  favicon: null
sourcePath: _posts/2016-04-13-000080-address-already-in-use-wtf.md
published: true
url: 000080-address-already-in-use-wtf/index.html
_type: Article

---
Ran into an issue where I could not start nginx. The error "**\[emerg\] listen() to 0.0.0.0:80, backlog 511 failed (98: Address already in use)**" would show up in the error log.  To combat this I took advantage of the "**fuser**" command.

To check what process is  using port 80 you can try this: "**fuser -u -n tcp 80**". If something has gobbled up that port before nginx had a chance  then you can also user fuser with the -k option to kill it "**sudo fuser -k 80/tcp**".

All left to do now is to start nginx with "**service nginx start**".