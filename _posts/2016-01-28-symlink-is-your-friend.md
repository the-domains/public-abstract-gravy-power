---
inFeed: true
hasPage: true
inNav: false
inLanguage: null
starred: false
keywords: []
description: 'I love Symlink but I always forget the syntax, and find myself googling it all the time. This is to put a stop to that.'
datePublished: '2016-01-28T23:41:47.668Z'
dateModified: '2016-01-28T23:41:35.916Z'
title: Symlink is your friend
author: []
authors: []
publisher:
  name: null
  domain: null
  url: null
  favicon: null
sourcePath: _posts/2016-01-28-symlink-is-your-friend.md
published: true
url: symlink-is-your-friend/index.html
_type: Article

---
[In computing, a symbolic link (also symlink or soft link) is the nickname for any file that contains a reference to another file or directory in the form of an absolute or relative path and that affects pathname resolution.][0]

Since I started developing in Linux I have use symlink extensively, and wanted to add a post so I did not have to go looking for the exact syntax every time I wanted to use it.

Linking a repo to my www root for the site I am working on:

> sudo ln -s source destination

So for example:

sudo ln -s /home/projects/website/ /var/www/website/

[0]: https://www.google.com.au/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cad=rja&uact=8&ved=0ahUKEwiIsL620M3KAhXC3aYKHd5RABMQFggeMAE&url=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FSymbolic_link&usg=AFQjCNHKXH-kM-_5J2NdkfDOz3TTue8WPg&bvm=bv.113034660,d.dGY