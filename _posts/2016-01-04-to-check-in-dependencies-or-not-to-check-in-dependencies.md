---
inFeed: true
hasPage: true
inNav: false
inLanguage: null
starred: false
keywords: []
description: An opinion piece on whether to check in your dependencies into source control.
datePublished: '2016-01-04T06:07:57.435Z'
dateModified: '2016-01-04T06:07:42.802Z'
author: []
title: To check in dependencies or not to check in dependencies
authors: []
publisher:
  name: gravypower.net
  domain: blog.gravypower.net
  url: null
  favicon: null
sourcePath: _posts/2016-01-04-to-check-in-dependencies-or-not-to-check-in-dependencies.md
published: true
url: to-check-in-dependencies-or-not-to-check-in-dependencies/index.html
_context: 'http://schema.org'
_type: Article

---
![](http://blog.gravypower.net/content/images/2015/Oct/tennant_hamlet_bower.jpg)

I have been playing around in the world of Drupal and Front End development for the last few months and have come across a topic of discussion that I thought I had heard the last of. Check in dependencies or not? This is something that I have thought about a lot in terms of .NET development and I came to the conclusion in that space that I should not check in my dependencies. Now this all comes down to personal preference but this is what I think. If you are serious about development you would have heard of Continuous Delivery, this is the practice of promoting code through a series of environments (Test, QA, UAT, Production, etc) with a click of a button. If you have not head of it before then head on over to Martin Fowler's Bliki and have a read about it, I see it as the big brother of Continuous Integration. When I practice Continuous Delivery and build a project the output is a package of some kind that can be deployed into any of the environments in my deployment pipeline. This package is built once and contains all dependencies. The arguments for checking in dependences into VCS I have been reading about lately mainly revolve around installing dependencies at deployment time. What happens if the package manager you have been using is no longer there or is having network issues, how can you deploy now?! My response to this is you should never be installing dependencies at deployment time; installing dependencies is part of the build phase of a deployment pipeline, the output of which is an artefact with them included. The only time I check in any dependencies is when there is no pathway to use a package manager. However in cases like this I often will host then in something like a private nugget feed, this way I can control all dependencies in a consistent manner. There is no correct way to manage dependencies, but I side on keeping your VCS clean and rely on your build artefacts to make sure you can deploy at any time.