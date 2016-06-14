---
published: true
title: Example Mapping
layout: post
tags: [BDD, SpecificationByExample, Cucumber, SpecFlow]
---
As I've [blogged about](http://blog.picklespro.com/2016/05/24/three-amigos-or-three-musketeers.html) before, the collaboration between all roles in a project team is an essential part of BDD. It therefore stands to reason that we try to find ways to make this collaboration as engaging as possible. After all, if you have a planning meeting where all roles are present but most of the participants are zoned out, then you still won't have a productive collaboration.

In December last year, Matt Wynne wrote a blog entry "[Introducing Example Mapping](https://cucumber.io/blog/2015/12/08/example-mapping-introduction)" where he talks about a technique he has been using to make planning meetings both more interesting to attend and more effective in their outcome.

<!--more-->

I have had the opportunity to try it out twice so far, once at [CukeUP! London 2016](http://blog.picklespro.com/2016/04/19/impressions-from-cukeup-2016-london-day-one.html), and once during [Gáspár Nagy's Developing with SpecFlow](https://skillsmatter.com/courses/539-gaspar-nagy-s-developing-with-specflow) course. I think it's a technique with great potential, but it will require practice to get the most out of it.

If you are new to Example Mapping, I recommend you read Matt's article. For those in a hurry, I will summarize my understanding of the technique and its results.

* Example Mapping uses index cards. Whenever you discuss something that is not on an index card yet, you write it on an index card and arrange the new index card with the existing ones.
* There are four colours of index cards
  * Yellow is for a story. For Example: Order pizza with six different slices.
  * Blue is for rules of a story. For Example: Apply a discount if the customer selects only two different kinds of slices.
  * Green is for examples. For Example: Customer orders half a pepperoni and half a margharita pizza.
  * Red is for questions. For Example: Can the order of slices be changed to optimize preparation of the pizza?
* In the beginning, it's good to have a dedicated person writing down things. As people get more fluent with the technique, everybody will end up writing things.
* It's tempting to write lots of blue cards, or even lots of yellow cards. If that happens, the facilitator should suggest to move some of the yellow and blue cards to a later discussion and to focus on a few cards by coming up with examples for them.
* By having a physical token for the idea you are discussing, you tend to stay more focused on this idea.
* People are more engaged when they are talking about concrete things rather than abstract things. The physical token helps again, and people will usually point to the card they are currently talking about.

## But I want feature files, not index cards!

Practice has shown that is is not effective to write feature files during a planning meeting: feature files put a lot of constraints on the language and phrases. Those constraints take a lot of time to fulfill, and you don't want your senior business representatives waiting impatiently until you have written the scenario just so. They have better things to do, and could give you more valuable input during that time.

Example Mapping address this concern by limiting the discussion to the index cards and not writing feature files during the meeting. You write the feature files afterwards, following this heuristic:

* Yellow cards tend to map to user stories.
* Blue cards tend to map to feature files.
* Green cards tend to map to a scenario in a feature file
* Red cards: you probably have some todo-tracking system in place to deal with questions that need answers.
* When all cards are processed, you can throw them away.

It's of course a good idea to have the feature files reviewed by the business representatives, to make sure they really capture the intent of the discussion.

## Summary

I think that Example Mapping is a very useful technique that - provided you practice it often enough - can be a real help in making the planning meetings more effective and engaging. Communication is the main bottleneck in most projects, and Example Mapping can improve this communication.