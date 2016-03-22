---
published: true
title: Giving up on TDD? And what about BDD?
layout: post
tags: [SpecFlow, BDD, SpecificationByExample, AcceptanceTestDrivenDevelopment, TDD]
---
Last week, I read an article by Ian Sommerville where he explains why he is [giving up on test-first development](http://iansommerville.com/systems-software-and-technology/giving-up-on-test-first-development/). I also read Robert C. Martin's answer to it, titled [Giving Up on TDD](http://blog.cleancoder.com/uncle-bob/2016/03/19/GivingUpOnTDD.html). 

This post is an answer to the former, from a point of view that is slightly different from the latter. And of course, since this is a blog about Behaviour Driven Development, I will tell you what BDD has got to do with it. :-)

## I have given up on TDD, too!

Here's my dirty little secret: I have given up on TDD any number of times. I have lost track of the number of times when I threw my hands up in the air and returned to the tried-and-(not-so)-tested approach of code-first and tests-later-if-at-all. But here's the thing: I have come back to TDD just as many times. Because I believe it's worthwhile.

Yes, TDD is hard. If you start with TDD, everything will slow to a crawl, and you'll feel like an idiot for creating tests for obvious cases. TDD is one of things that easy to learn, but hard to master. The technique is simple: slap some attributes on certain classes and methods and call an assert method. But there's an [art to unit testing](http://artofunittesting.com/) that takes time to dig.

TDD is one of those cases where it really pays off to pay for training. I took [Roy Osherove's TDD Master Class](http://osherove.com/storage/The%20Art%20of%20Unit%20Testing%20in%20.NET%20Masteclass.pdf) and ever since then I have been consistently able to solve the kind of unit testing problems that had me give up on TDD in the past.

Invest in training, come back to TDD again and again. And one day you will experience the benefits when all those tests you spent so much time and effort on mean you can [release a minor upgrade that adds support for v2 of an important component on the same day](http://blog.picklespro.com/2016/01/27/specflow-v2-is-available.html). Or when all those scenarios that made you feel like an idiot suddenly mean that you can deal with a changed requirement by changing a single line of production code.

## Sometimes, the best design is a design that is hard to test ...

... or so Ian Sommerville claims. I disagree, and so does Robert C. Martin (quite emphatically so, in fact). If you claim "sometimes a design that is easily testable is not elegant", or "not immediately obvious", then: yes, I grant that this is sometimes true. I do not see this as a problem, though. In my experience, elegant code is often difficult to understand by anyone except the original writer, or by anyone at all a couple of weeks after it was written.

But as to the claim "the best design is one that’s hard to test": what is a good design? Code is written only once, but maintained and changed many times. So I argue that a good design is one that supports maintaining and changing the code. Code that is hard to test is automatically hard to maintain. Thus code that is hard to test cannot be a good design.

## What's BDD got to do with it?

One of the perceived problems with TDD is that it increases the amount of code that is written, decreasing developer productivity. If you don't know what it is you are supposed to program, chances are high you'll code the wrong thing and will have to change it later or even throw it away. If you wrote unit tests as well, you'll be throwing away even more code; you'll have wasted even more time.

BDD can help here, because BDD will help you to determine what you need to code. In a nutshell: Using BDD, you establish a common understanding with the stake holders. You record that common understanding in a set of examples, or behaviours of the system. When you create the automation layer for those examples, that will set the shape of the API that your production code needs to support those scenarios. Once you have the shape of an API, you are pointed in the right direction and you can implement that API using TDD.

This approach is called "outside-in development" and it is the reason that BDD and TDD complement each other very well. When used together, BDD and TDD can help to bring out the best in each other and prevent the bad aspects of the other to surface.

## Summary

TDD is a development practice that can reap significant benefits in terms of maintainability and changeability of code. It is also a development practice that demands a lot of skill. Invest in training, and look to BDD to complement and enhance TDD.