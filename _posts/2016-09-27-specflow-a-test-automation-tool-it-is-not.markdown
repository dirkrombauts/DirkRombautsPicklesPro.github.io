---
published: true
title: SpecFlow a Test Automation Tool It Is Not
layout: post
tags: [BDD, SpecificationByExample, Cucumber, SpecFlow, LivingDocumentation, OutsideInDevelopment]
---
In order to grow really proficient at SpecFlow and Behaviour Driven Development, you must unlearn what you have learned. When you first heard of BDD, you were likely seduced by visions of test automation. Voices are calling for you to specify all possible input permutations in a Feature file. Resist them you must. A test automation tool SpecFlow is not.

<!--more-->

## What SpecFlow and BDD are good at

SpecFlow (and Behaviour Driven Development in general) is very good at three things:

1. it helps you to discover and understand the requirements through the discussions you have while writing scenarios and coming up with key examples. This is called "Specification by Example".
2. It keeps a written record of the specification that is always up to date and never grows stale. This is called "Living Documentation".
3. By automating the scenarios, you create an automatic verification of the specification. While writing the automation layer, you determine the logic that the business code needs to support. This is called "Outside-In Development".

Together, these three aspects are the [Three Pillars of BDD](/2016/06/21/the-three-pillars-of-bdd.html).

## What SpecFlow and BDD are not good at

SpecFlow/BDD are not good at testing all possible permutations. When people try to do this, sooner or later they run into these problems:

1. The gherkin language does readily support permutations. There are "Scenario Outlines" but no "Scenario Outline Outlines".
2. When trying to understand the specification by reading the scenarios, you suffer from information overload. You don't see the forest because of all the trees.
3. Execution times go through the roof, and the verification will be run less and less frequently. Developers will lose the support of the verification that tells them when they are done. They will no longer use the automation layer to determine the logic the business code needs to support, opening the door to YAGNI.

I know that there are situation where you do need to test all possible permutations. My advice is this: don't use SpecFlow for those cases. I know that SpecFlow and BDD are often marketed as "Test Automation" tools, but that is not where their main value lies.

So if you do have a genuine need to test all possible permutations, I urge you to consider writing that particular set of test cases using a "traditional" unit testing tool (like NUnit). Using well-established code practices you can arrive at astructure that is maintainable, readable and suited to testing all possible permutations.

## Summary

If you use SpecFlow and BDD in the area of their strengths, you can reap tremendous benefits as business analysts and software developers help each other to discover the true requirements, benefit from an always up-to-date record of the specification, and receive guidance from the automation layer. SpecFlow is a collaboration tool, and helps everyone to work better together and more effectively.

If you try to use SpecFlow and BDD outside of those areas - for instance if you use it as a test automation tool - you will run into problems like unwieldy scenarios, information overload, long test runs and haphazard development tactics. SpecFlow is not a test automation tool.

