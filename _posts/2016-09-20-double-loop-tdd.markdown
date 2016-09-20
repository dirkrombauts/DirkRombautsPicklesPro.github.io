---
published: true
title: Double Loop TDD
layout: post
tags: [BDD, TDD, Code]
---
While presenting last week's inaugural meetup of the [Vienna BDD Meetup](https://www.meetup.com/Vienna-BDD-Meetup/), a discussion came up on how Behaviour Driven Development (BDD) and Test-Driven Development relate to each other. One of the participants mentioned a buzzword: "Double Loop TDD". I will talk about a bit about Double Loop TDD and how BDD uses it to great effect.

![Groceries](/public/img/2016-09-20_DoubleLoopTDD.png){: .teaserImage }

<!--more-->

Double Loop TDD makes you work from the top down, or from the outside in: you begin by creating an acceptance test. That means you begin by specifying the goal you want to achieve, or that you *begin with the end in mind* as [Stephen Covey puts it](https://www.stephencovey.com/7habits/7habits-habit2.php). That acceptance test will fail because we haven't implemented the desired functionality yet. The first loop (or *outer* loop) in the double loop is the one that goes from a failing acceptance test to working software (with the acceptance test now passing) and to the next failing acceptance test.

Once you know where you are going, you can begin tracing your way to that goal. Or rather: you can begin tracing your way back *from* that goal to your current position.

Let's have an example: we want to be able to sell e-books on the internet. That's our goal. In order to achieve that goal, we will need to (among others) process the payment, and mail a purchase-specific download link. In order to process the payment, we probably need to use some credit card component. We need to pass that component the credit card details we collected from the customer.

At this point we can write a (failing) unit test for dealing with the credit card component. The second loop (or *inner* loop) in the double loop goes from the failing unit test to an implementation that makes the test pass to a refactoring and then on to the next failing unit test.

We will need to write a substantial amount of unit tests in order to get all the pieces of the puzzle in place, and at some point we will have done all the work needed, and the original acceptance test will pass. That means we will be going through the inner loop several times but only once through the outer loop. Until the next feature request, that is ...

A key thing in this process is that everything you do is driven by some goal: we know that we want to sell e-books on the internet, and that drives us towards processing payments, which in turns drives us towards credit card components.

And how does BDD fit in this picture? Quite simple: when we express a scenario in gherkin, that becomes the failing acceptance test. The test will fail because there are no bindings for the steps in the scenario. So in order to bring the test closer to passing, we create bindings that call the domain logic. Once we determine the method calls that the domain logic must support, we can use TDD to implement those methods. TDD as it is understood today is a very powerful aid in creating bug-free implementations of methods and similarly small units of works.

In the outer loop, BDD helps us to determine what methods our domain logic must support, and in the inner loop TDD helps us to implement those methods correctly. Using BDD, we implement the right methods, and using TDD, we implement those methods right.

