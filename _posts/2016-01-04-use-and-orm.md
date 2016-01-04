---
inFeed: true
hasPage: true
inNav: false
inLanguage: null
starred: false
keywords: []
description: 'My take on the best way to do unit testing in Sitecore, this idea could be use with other CMS systems also. '
datePublished: '2016-01-04T06:03:42.986Z'
dateModified: '2016-01-04T06:03:34.269Z'
author: []
title: "Use and ORM\_"
authors: []
publisher:
  name: gravypower.net
  domain: blog.gravypower.net
  url: null
  favicon: null
sourcePath: _posts/2016-01-04-use-and-orm.md
published: true
url: use-and-orm/index.html
_context: 'http://schema.org'
_type: Article

---
![](http://blog.gravypower.net/content/images/2015/Jun/Potato.jpg)

I am a big advocate of TDD and would love to see interfaces on all of the Sitecore types, this is a big ask to the product team as they have new a wonderful features to work on.

There are a few methods that help you Test Drive your application when using Sitecore, I will start with my least preferred option, (please note that some of this rant won't directly relate to Sitecore) 

# Use and ORM 

In the past I have heavily used libraries such as Entity Framework and Glass, but the more I learn about Software design principles that more I don't like them. This is not, by far, a recommendation not to use them as they can speed up development significantly, the question I am asking my self is what is the speed costing me? Have a look at this Wikipedia article [Object-relational impedance mismatch][0], this blog article[ORM is an anti-pattern][1] and last but definitely not least have a read of Uncle Bobs rant on the subject [Dance you Imps!][2] (These arguments may not be applicable to Sitecore). 

# Use something like Microsoft Fakes or TypeMock 

As Martina pointed out you can use things like TypeMock, I have not used that personally but I have used Microsoft Fakes for some SharePoint development in the past. See [TDD, Unit testing and Microsoft Fakes with Sitecore Solutions][3]. 

# Abstract the Sitecore API 

You can take advantage of the Facade design pattern to help with abstracting away the Sitecore API. I have used this a lot in my code in the past and find it very nice to use in TDD when building functionality on top of Sitecore but it does have its limitations. 

# Unit Test directly against the Sitecore 

Mike Edwards, the creator of Glass, blogged a while ago about[Unit Testing Sitecore in the NUnit GUI][4], and I liked and used this a lot for a long time, it was simple and you did not have to mock anything as you just created items with the values you wanted as input for your tests. This is a very similar idea to [Custom ASP.NET NUnit Test Runner][5]. Now I don't strictly think that these methods are unit testing, I see them more of integration testing, your code is not running in isolation as Sitecore is backing everything. 

Now my current preferred option, "Don't think about unit testing and Sitecore at the same time" ;) bear with me please. 

We use TDD to help us prove that the code that we are writing is "Correct" and we should still do that my only thought (and this could be completely incorrect and would love to hear what others think) is why we need to test Sitecore when proving that our code is "Correct"? Do we test that a REST endpoint is working? Now I am not saying we don't need to test that our code correctly talks to Sitecore, it's just we can assume that that SItecore API is working as it should. Testing that our code is talking to Sitecore correctly is more in the realm of integration testing and should be treated as such. 

We can use the Template Method Pattern to help us write logic that does not know about Sitecore that we completely control and mock and then create implementations that can talk to Sitecore. In our abstract class you only use POCO classes to build up our functionality using TDD so you can mock to your heart's content, and then all our implementation does is map Sitecore items to those POCOs. 

On the other Side of the fence is displaying values from items on pages, I am inclined to access these directly using controls like field renderers etc and only use the above method when actually creating business logic that uses these values as input. 

To complete the equation you will need a nice suite of Integration Tests along with your Unit Tests, a good thing in my opinion.

[0]: http://en.wikipedia.org/wiki/Object-relational_impedance_mismatch
[1]: http://seldo.com/weblog/2011/08/11/orm_is_an_antipattern
[2]: http://blog.8thlight.com/uncle-bob/2013/10/01/Dance-You-Imps.html
[3]: https://www.sitecore.net/learn/blogs/technical-blogs/navinder-marwaha/posts/2014/09/01102014.aspx
[4]: http://www.experimentsincode.com/?p=232
[5]: http://www.codeflood.net/testrunner/