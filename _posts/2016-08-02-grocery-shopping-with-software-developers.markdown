---
published: true
title: Grocery Shopping with Software Developers
layout: post
tags: [BDD, SpecFlow, Business]
---
There's a joke about a Software Developer who goes grocery shopping. It goes like this: suppose you send a Software Developer to buy groceries in the nearby store. You tell the Software Developer: "Buy a liter of milk. If they have eggs, buy six". The store does have eggs, so what does the Software Developer buy? The answer to that question, the punch line of the joke, illustrates the need for Behaviour Driven Development.

![Groceries](/public/img/2016-08-02_Groceries.png){: .teaserImage }

<!--more-->

So what does the Software Developer buy? 6 liters of milk - after all, the store has eggs!

Like all things humorous, this joke is only humorous because it is recognizable. Nearly every Business Person has been in this situation where their (in their opinion) clearly articulated wishes were misunderstood.  And most Software Developers I've consider it a matter of pride that their understanding of language is much more exact than the (in their opinion) amorphous statements of Business People.

The problem here is that the specification for the shopping trip was given in the form of a rule: "Buy a liter of milk. If they have eggs, buy six". Thanks to the ambiguities of the English language, this rule leaves things open to (mis)interpretation.

A different way to write the specification is using a behaviour (also known as a scenario):

Given the store has eggs  
When I go shopping  
Then I buy 1 liter of milk  
And I buy 6 eggs

The desired outcome is now unambiguous - there's no room for misinterpretation. Business People can be confident that the Software Developers understand the requirement, and Software Developers receive requirements that can be easily verified.

This approach to specification is called "Behaviour Driven Development": in Behaviour Driven Development, we define Behaviours first. The knowledge of these Behaviours then drives the development work.