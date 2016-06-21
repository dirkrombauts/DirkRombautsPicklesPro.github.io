---
published: true
title: The Three Pillars of BDD
layout: post
tags: [BDD, SpecificationByExample, Cucumber, SpecFlow, LivingDocumentation]
---
There are a lot of terms and aspects of Behaviour Driven Development (BDD) flying about, and it may not always be immediately obvious what the benefits of them are. I will attempt to bring some clarity here, and in doing so I will define the **three pillars of BDD**.

![Three Pillars of BDD](/public/img/2016-06-21_ThreePillarsOfBDD.png){: .teaserImages}

<!--more-->

## The First Pillar: Specification By Example

The first and foremost goal of BDD is to *bridge the communication gap* between the technical world of software developers and the non-technical world of business people. It's a bit of a cliché that most software developers agree that business people have little understanding of software development, and that the business people do not understand when software developers explain things. On the other hand, I'm willing to bet that most business people would say the same about software developers! That is of course a recipe for disaster, and BDD aims to rectify that situation.

Through BDD, software developers and business people will establish a *common understanding*: when people speak about the same thing, they will mean the same thing, and the others will understand the same thing. That will significantly reduce the number of misunderstandings.

During these discussions, people will naturally begin to use certain words and expressions for concepts and actions in the business domain. Those words and expressions will build up a pervasive vocabulary for the project. That pervasive vocabulary is also know as the *ubiquitous language*.

During meetings known as *3 Amigos Meetings* or [*Three Musketeers Meetings*](/2016/05/24/three-amigos-or-three-musketeers.html) the different roles on the project will discuss requirements, rules and examples for those rules. We call that process *Specification By Example*.

It is worth repeating here that if you achieve this first pillar of BDD, then you are reaping 90% of the benefits. Most projects fail because of bad communication, and the first pillar of BDD is all about improving communication. The second and third pillars are only a bonus!

## The Second Pillar: Living Documentation

Once you start coming up with examples for features and rules, you will likely start recording and collecting those examples. You are effectively building up a description of how the system works, and the description always reflects the latest understanding of the functionality. We call this kind of description a [Living Documentation](/2016/03/08/what-is-a-living-documentation.html).

If you write your examples in Gherkin, you can create a living documentation using [Pickles](http://www.picklesdoc.com/), the open source Living Documentation generator.

## The Third Pillar: Executable Specification 

You can choose to automate some of your examples, that is: write small bits of code that will connect the phrases from your examples with the business logic of the code. In that way, the example gets converted in a series of interactions with the system. It's as if a user is working with the system and verifying whether the example is fulfilled.

Since the examples are also the specification, you are effectively verifying that the requirements have been fulfilled. This verification is executed automatically. We call this an *Executable Specification*.

The goal of the Executable Specification is to enable a rapid feedback loop for the developer: is the production code that we are working on right now helping us to fulfill the requirements? The faster and more frequent we can verify our progress, the more efficient we will be able to work. *Frequent Validation* tells us if we are still on the right track.

Development then becomes like working through stages. The first stage is that of the examples: in order to fulfill the business requirements, we need to make the example pass the Frequent Verification. In order to do that, we proceed to the next stage, the *Automation Layer*. We need to create several small bits of code (*Step Definitions*) that connects phrases from the examples with the business logic. The phrases tells us which Step Definitions we need. In order for the Step Definitions to become meaningful, we need to proceed to the next stage, the *Business Logic* (or Domain Logic or Production Code). The Step Definitions put very clear requirements on the Business Logic, and thus we can work out the Business Logic with techniques like *Test Driven Development*. When the Business Logic is in place, the Step Definitions will become meaningful and the frequent validation will indicate that the requirement is fulfilled.

Development thus started from the outside of the system (the examples define the system from the outside) and progresses to the inside of the system (the Business Logic defines the system from the inside). We call this *Outside-In Development*.

## Summary

In this post, I have given an overview and explanation of most of the buzzwords associated with Behaviour Driven Development. This knowledge will help you to read more detailed articles and watch presentations that focus on details of part of BDD, and will help you to get a feeling for the benefits of BDD.
