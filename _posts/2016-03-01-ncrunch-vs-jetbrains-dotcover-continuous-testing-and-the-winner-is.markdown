---
published: true
title: NCrunch vs. JetBrains dotCover Continuous Testing - and the winner is ...
layout: post
tags: [BDD, TDD, ReSharper, VisualStudio, NCrunch]
---
Agile software development is all about shortening the feedback cycle: the sooner you receive feedback whether you are on the right track, the sooner you can correct and the smaller the costs of the correction. Scrum and Kanban do this on an organizational level, and Test Driven Development does it on a technical level. You write a failing unit test (that defines the direction you want to go), you write some code to make it pass (you receive feedback that you did in fact go into the right direction), and you clean up. You know the mantra: red, green, refactor.

[NCrunch by Remco Software Ltd](http://www.ncrunch.net/) and [dotCover by JetBrains](https://www.jetbrains.com/dotcover/)  are two plugins for Visual Studio that will help you go through red-green-refactor feedback cycle faster. And that's a good thing, because faster feedback directly leads to less waste.

So what do they do? They enable you to run unit tests in Visual Studio. "But wait", you say, "Visual Studio already does that itself. Why do I need a plugin?" True, but both these plugins do something more than Visual Studio: they continuously run the unit tests in the background. You don't need to compile and you don't need to start the test run. They even figure out which tests are affected by the code you just changed and run only those tests. That means you get feedback even faster. And faster feedback ... yes, you get it by now ;-)

In this post, I'm pitting NCrunch against dotCover: I will list their pros and cons, and tell you which one I prefer. I will not talk about [TestDriven.NET by Mutant Design Limited](http://www.testdriven.net/) because I have no real hands-on experience with it.

## dotCover by JetBrains

dotCover is the new kid on the block when it comes to running unit tests continuously in Visual Studio. dotCover has been around for several years, but the ability to run unit tests continuously wasn't added until fall 2015. The `Continuous Testing Session` tool window should look familiar to anyone who has used ReSharper's unit test runner.

![dotCover Continous Testing Session](/public/img/2016-03-01_dotCover.png)

The big advantage of dotCover is that you may already have it: it is part of ReSharper Ultimate. Many, many .NET developers use ReSharper, and a good many of those have ReSharper Ultimate. If you do, then there's nothing more to install. Simply expand the `Unit Tests` submenu in the `ReSharper` menu in Visual Studio, and click on `Continuous Testing Session`.

The big disadvantage of dotCover's Continuous Testing mode for me is that it steals the keyboard focus. If you use lots of keyboards shortcuts like I do and touch the mouse only seldomly, you will come to rely on the fact that after saving (by pressing `ctrl+s`) you can type on where you left off. When dotCover detects a change (when you save the current document), dotCover compiles your code, and the focus jumps to the `Output` tool window that shows the output of MSBuild. You need to press `ESC` to return focus to the code window, and to me that breaks the flow.

Additionally: if your solution does not compile, you cannot run your tests. Obvious, I know, but what is not obvious is that dotCover does not alert you when the solution does not compile. It happened repeatedly to me that I happily continued coding without noticing that I'd forgotten a `;` somewhere. Only when I started wondering why the test didn't change status did I notice the compiler error. That means I cannot trust the flow when I do achieve it.

dotCover is much, much better than nothing, and you get it for free if you already have a Resharper Ultimate subscription. But there is definite room for improvement.

## NCrunch by Remco Software Ltd

NCrunch has been along for several years, and found the "way to the heart" of Roy Osherove in the second edition of his book [The Art of Unit Testing](http://artofunittesting.com/). After installing NCrunch and running a short configuration wizard for your solution, you are presented with the `NCrunch Tests` tool window.

![NCrunch Tests](/public/img/2016-03-01_ncrunch.png)

The `NCrunch Tests` tool window shows ... not much. That's intentional: you will only see something if you need to take action. A unit test is red? You will see it. A project does not compile? You will see it. Everything green? You will see nothing. You see nothing? That means everything compiles and is green. That way, NCrunch establishes a trustworthy flow without need for much interpretation.

NCrunch never changes the focus while it is running tests, so I never have to press any extra keys in order to continue editing. In fact, I don't need to save my code for NCrunch to start running tests: NCrunch detects in-memory changes, makes a shadow-copy of those changes, and runs the affected tests. That means I can start a flow of writing test code and writing production code without needing any extra steps to account for NCrunch.

## The Verdict

I like to work in a flow with as few distractions as possible. NCrunch delivers seamless and trustworthy support for that flow; dotCover does not. For that reason I prefer NCrunch over dotCover, and I happily pay the extra money for NCrunch in addition to what I pay for ReSharper.