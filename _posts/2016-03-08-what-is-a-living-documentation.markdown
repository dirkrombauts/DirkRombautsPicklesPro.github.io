---
published: true
title: What Is a Living Documentation?
layout: post
tags: [SpecFlow, Pickles, BDD, LivingDocumentation, SpecificationByExample]
---
When you are working with *Behaviour Driven Development*, *Specification By Example*, or *Acceptance Test Driven Developments*, sooner or later you are likely to run into the concept of a *Living Documentation*. And you might well ask yourself: "what is a Living Documentation? What makes is *living*?"

<!--more-->

## Board Games and Living Rulebooks

Let me make an excursion into another passion of mine: board games. If you are not into board games, that's fine: just picture computer games instead. These days, many board games (and very many computer games) are not done when the original game is over, but rather they have expansions. One of my current favourites is [*Twilight Imperium Third Edition*](https://www.fantasyflightgames.com/en/products/twilight-imperium-3rd-edition/) by Fantasy Flight Games. There is the game itself, and there are 2 boxed expansions (as of early 2016).

Right now, you are probably thinking "That's all very well and I'm glad you enjoy your board game hobby so much, but what has this got to do with Living Documentation?" You see, board games come with a rule book. The expansions add more rules, and over time the publisher may publish errata and answers to frequently asked questions. So that means that for any given situation in a game, you may have to consult multiple rulebooks and online PDFs to find the answer to your question.

Wouldn't it be convenient if you had just one rulebook that was always up to date, that contained all the rules and incorporates all errata and FAQs? Such a rulebook is called a "living rulebook": it is alive and evolving and always contains the current rules of the game. It is your single source of the truth, and is always up to date.

(*Twilight Imperium* does indeed have a living rulebook, and you can find it on [Board Game Geek](https://boardgamegeek.com/filepage/75151/twilight-imperium-living-rulebook) - think Wikipedia for Boardgames).

## Living Documentation

So now we know what makes a document a living document: it is a single source of truth, and is always up to date. How does this apply to documentation? We have all seen documentation that is spread across different systems: a Word document with requirements, an Excel sheets with change requests, a list of user stories with the latest acceptance criteria that often contradict the original requirements, ... There's no single source of truth, and the documentation is not up to date. Not "living" at all.

The good news is that using *Behaviour Driven Development*, you can create a living documentation of your software with only a small amount of additional effort. *BDD* implies that you describe the behaviour of your software using Features and Scenarios &ndash; they are the single source of truth. If you follow the Gherkin syntax when writing your scenarios, then there are software tools that can automatically convert those Features and Scenarios from a simple text format into a web site, a Word document or other formats &ndash; no human intervention is needed so the web site or the Word document are always up to date. Those tools are called *Living Documentation generators*.

[Pickles](http://www.picklesdoc.com/) is one of the leading Living Documentation generators (full disclosure: I am the maintainer of Pickles). [Relish](https://relishapp.com/) is another one, created by the people behind [Cucumber](https://cucumber.io/). While Relish is closed-source, appears to be stalled and forces you to host your living documentation in the cloud, Pickles is open source, is actively being developed and leaves you in full command of where your living documentation ends up.

## Summary

A Living Documentation is a documentation that is the single source of truth for the system it documents, and that is always kept up to date. Using BDD and a Living Documentation generator, you can automatically create such a Living Documentation from your Features and Scenarios. I will show how in my next blog post.