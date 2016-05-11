---
published: true
title: Using Assertion Libraries
layout: post
tags: [SpecFlow, AutomationLayer, Code]
---
Code needs to be well-readable. After all, you will read a set of lines of code far more often than you write them. When it comes to expressing assertions in test code, the usual ways fall somewhat short of the mark. Assertion libraries can improve matters, and as a side effect reduce vendor lock-in.

## Setting the stage

Consider the traditional `.feature` file in SpecFlow:

{% gist DirkRombautsPicklesPro/79020b90fac0604190369e1146174c4c Addition.feature %}

When implementing the automation layer, you will write a method like this one:

{% gist DirkRombautsPicklesPro/79020b90fac0604190369e1146174c4c AutomationLayer-Basic.cs %}

The above gist assumes that you are using NUnit. It also assumes that you are writing assertions in the old `Assert.AreEqual(expected, actual)` style.

The first problem occurs right there. Do you write `actual` as the first argument of `Assert.AreEqual`? Or is it the second one? The correct answer is the second one, but I've seen this mixed up in code more times than I can remember.

The second problem occurs when the assertion fails: the error messages are somewhat Spartan. I myself don't find this too much of a problem but I know it is an issue for some people.

## NUnit offers an alternative

NUnit offers an alternative syntax:

{% gist DirkRombautsPicklesPro/79020b90fac0604190369e1146174c4c AutomationLayer-NUnit.cs %}

The assertion now reads like an English sentence: "assert that actual is equal to expected." There is less potential for mixing up actual and expected. NUnit presumably generates nicer error messages.

This alternative is a definite improvement, but I don't like it too much. It seems unnatural to me to have a fluent expression (`Is.EqualTo`) as argument for a method call.

## Should and Shouldly

[Should](https://github.com/erichexter/Should) and [Shouldly](http://shouldly.readthedocs.io/en/latest/) are two similar assertion libraries. Both offer a set of extension methods for expressing assertions. These two gists show the result:

{% gist DirkRombautsPicklesPro/79020b90fac0604190369e1146174c4c AutomationLayer-Should.cs %}

{% gist DirkRombautsPicklesPro/79020b90fac0604190369e1146174c4c AutomationLayer-Shouldly.cs %}

The focus lies on the `actual` value, so there's no potential for confusing it with the `expected` values. Both libraries produce good-looking error messages. The disadvantage is that IntelliSense gets overloaded with a lot of extension methods.

Some people don't like the "should" wording, because they feel "should" is too weak. I've heard this argument most often from people whose native language is French.

## NFluent

[NFluent](http://n-fluent.net/) is currently my favorite assertion library. It combines the advantages of all previous libraries without the disadvantages.

Assertions written in NFluent read like natural sentences. They provide a strong wording that leaves no room for argument. The focus lies on the `actual` value. NFluent provides a proper fluent interface, and does not clutter IntelliSense. NFluent also provides informative error messages.

{% gist DirkRombautsPicklesPro/79020b90fac0604190369e1146174c4c AutomationLayer.NFluent.cs %}

NFluent provides a well-documented way to extend the assertion methods. You can provide an assertion method specific to your business objects and their properties.

NFluent is not perfect. Asserting on large strings is a pain because the error messages truncate the strings. I've been meaning to write my own assertion method for that :-)

### Update 18:20

I withdraw my remarks about asserting on large strings with NFluent. The team behind NFluent have been busy improving the error messages. The error message for strings now states the index where the strings diverge, and quotes that location both in the actual and the expected string.

## Reducing Vendor Lock-In

As a side-effect, using an assertion library reduces your dependency on the unit test framework. If you use an assertion library, you can change the unit test framework with relative ease. All you need to do is do a search-and-replace on the attributes that define test classes and methods. There's no need to port your assertions from the old unit test framework to the new one.

## Summary

Using an assertion library can make your code easier to read and make its intention more clear. Thanks to IntelliSense your code will get easier to write as well.

Do you use an assertion library? Which one is your favourite? Please let me know in the comments!
