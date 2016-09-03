---
datePublished: '2016-08-31T23:43:39.759Z'
inFeed: true
authors: []
hasPage: true
keywords: []
author: []
dateModified: '2016-08-31T23:43:38.992Z'
title: ''
publisher: {}
description: >-
  Ran into an issue where I could not start nginx. The error "[emerg] listen()
  to 0.0.0.0:80, backlog 511 failed (98: Address already in use)" would show up
  in the error log. To combat this I took advantage of the "fuser" command.
inLanguage: null
inNav: false
via: {}
starred: false
sourcePath: _posts/2016-04-13-000080-address-already-in-use-wtf.md
url: 000080-address-already-in-use-wtf/index.html
_type: Article

---
Ran into an issue where I could not start nginx. The error "**\[emerg\] listen() to 0.0.0.0:80, backlog 511 failed (98: Address already in use)**" would show up in the error log. To combat this I took advantage of the "**fuser**" command.

To check what process is using port 80 you can try this: "**fuser -u -n tcp 80**". If something has gobbled up that port before nginx had a chance then you can also user fuser with the -k option to kill it "**sudo fuser -k 80/tcp**".

All you have left to do now is to start nginx with this command: "**service nginx start**".