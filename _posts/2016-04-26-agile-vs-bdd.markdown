---
published: true
title: Agile vs. BDD
layout: post
tags: [Agile, Scrum, BDD, SpecificationByExample, OutsideInDevelopment]
---
Earlier today, I received an email with this question:

    I am trying to understand the difference between Agile and BDD. Where do they both fit in the picture? I thought doing 10 minutes standups, sprint planning, demos and retrospectives where a way to implement BDD in a team. [...] I'm getting a little lost here.
Let’s see if I can explain some of the differences between Agile and Behaviour Driven Development (BDD). First – and this is probably the reason you got confused – Agile and BDD work really well together. You can do Agile without BDD, and you can even use BDD without Agile, but in my opinion you will get the best from both if you use them together. So if you were afraid you were doing something wrong by doing standups, sprint planning, demos and retrospectives: have no fear, those are excellent practices and you will benefit from them.

<!--more-->

## Agile

Now to the differences. What is “agile”? Agile is a way of managing projects that allows you to react more rapidly to change than in traditional project management. In traditional project management, often called “waterfall”, you start a project and (for example) three years later you finish it. That’s fine if you are building rockets, but if you are building software you will find that the market or the business environment have changed so much that your software is now useless. From the moment you started, it took you three years before you knew that you were building the right thing, before you knew if your investment would pay off. It also means that it takes three years before you can adapt to changes in the business environment.

Agile aims to make this timespan of three years shorter. It aims to enable you to adapt to change after (for example) three weeks instead of three years. As you get more proficient with this faster process, you will be able to reduce this timespan to three days, or even three hours. I’m not joking! You will know in a matter of weeks (days/hours) whether you are building the right thing, and will be able to change course if you are going in the wrong direction.

So how does “agile” achieve that? In general, by limiting the number of things that are worked on. In traditional project management, you first specify all features. Then you develop all features, then you test all features and then you release all features. If you are using V-Model instead of Waterfall you will specify all test cases while you are specifying all features, but still you are working on *all* features. Agile imposes a limit: you will specify only a small number of features, develop a small number of features, test a small number of features and release a small number of features.

There are different ways to do Agile and they will impose the limit in different ways. What you describe sounds a lot like Scrum, and one way of describing Scrum is “waterfall compressed to three weeks”: you agree on a set of features that will be worked on (during the Sprint Planning meeting), then you specify the features in detail, develop and test them. Then you release those features (during the Sprint Demo meeting), and finally you do a project post-mortem (during the Retrospective meeting). Because three weeks is really a short time you cannot afford to let things slip, so you need to be in very close contact with everybody on the team – that’s what the daily standup meetings (\*) are for.

(\*): those meetings should be brief, 10 to 15 minutes max. People tend to talk longer when they are sitting comfortably, so making people stand is one way of helping the meetings to be short. If some members of the team are unable to stand they can still participate, provided they speak briefly like the people who are standing.

So in summary: Agile is about limiting the amount of work in process, with the goal of being able to react to changes in the business environment faster.

## BDD

Now on to BDD: BDD is a solution to a different problem. Does it take a long time to develop a feature, from the first time the feature is mentioned until the time the feature is released? When a feature is released, do you get many bug reports that the feature does not solve the business problem? If you answer “yes” to one or both of those questions, then BDD can help you. BDD is about making everybody in the team truly understand the requirements, about finding hidden assumptions that are obvious to business people but a total mystery to developers, about finding technical uncertainties that would make a feature very costly to develop.

BDD solves this problem with a two-fold approach: the first part (corresponding to “Side A” of Aslak Hellesøy’s [“Kind of Green” keynote at CukeUP! London 2016](https://skillsmatter.com/skillscasts/7361-keynote-kind-of-green)) is “Specification By Example”: representatives from all disciplines in the project team (at a minimum someone who knows the business domain, someone who will do the coding and someone in charge of testing) sit together and discuss the requirements. They come up with a number of examples to illustrate the requirements.

The second part of BDD (“Side B” of “Kind of Green”) is “Outside-In Development”. The examples that came out of the “Specification By Example” meetings will be automated so that they can be used to validate that the software is working correctly. You will very likely need more test cases than there are examples, but remember that the examples are there primarily to help you understand the system, and only secondarily to test the system. If you need to modify the examples, always make sure that they still fulfill the job of helping you understand the system. The developers will first automate the scenarios, and then design a domain model that answers the business need (perhaps through [Modelling By Example](http://stakeholderwhisperer.com/posts/2014/10/introducing-modelling-by-example)). Once they have a domain model, the developers can then implement it in code using techniques like Test Driven Development.

So in summary: BDD is about making sure that you build the right software.

## One or the other? Both!

Now back to Agile vs. BDD. Agile is about setting a fast pace with software delivery, and BDD is about building the right software. If you use only Agile, you will release software fast and often but  risk delivering software that does not answer the business needs. If you only use BDD, you will release the right software but it can still take you three years to do it. If you combine Agile and BDD, you will release the right software fast and often.

I hope I was able to clarify the differences between Agile and BDD and how you can combine them.  Feel free to sound off in the comments!
