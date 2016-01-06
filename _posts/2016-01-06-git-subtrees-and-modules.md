---
inFeed: true
hasPage: true
inNav: false
inLanguage: null
starred: false
keywords: []
description: Managing Drupal Modules with Git SubTree
datePublished: '2016-01-06T03:01:20.839Z'
dateModified: '2016-01-06T03:01:07.170Z'
title: Git SubTrees and MOdules
author: []
authors: []
publisher:
  name: null
  domain: null
  url: null
  favicon: null
sourcePath: _posts/2016-01-06-git-subtrees-and-modules.md
published: true
url: git-subtrees-and-modules/index.html
_type: Article

---
![Baobab Tree](https://the-grid-user-content.s3-us-west-2.amazonaws.com/81764708-f69c-457d-bfca-ae087d8b4c79.jpg)

I have been working with Drupal for about 4 months now and have started to forget things.  Today is the start of a series of posts for me to google my brain later, and if someone else gets use out of it that's great.

Currentley [pantheon.io][0] does not support Drush Make files so I needed to find another way to manage modules, welcome to the wold of Git SubTrees.

First we need to create a git remote, this will help keep the SubTree up to date later on.

> git remote add --f \[remote name\] \[repository url\]

In other blogs I have read they create the SubTree from a branch, I feel that this is not good practice.  My reason for this is one of version management,the ability to reliably know what release of the module is in use is important for a wide range of reasons which I wont go into today. Luckily modules that are hosted on git.drupal.org are tagged with their releases, /poolparty.

To create a SubTree from a tag use:

> git subtree add --prefix=\[path to module\] \[remote\] \[tag\] --squash

If you would like to see what SubTrees you have in the Repo run the following:

> git log | grep git-subtree-dir | tr -d ' ' | cut -d ":" -f2 | sort | uniq

SubTrees are stored as commit messages so you need to effectively do a search through the output of git log.

All is needed now is a git push to get it into your remote repo.

All done

[0]: https://pantheon.io/