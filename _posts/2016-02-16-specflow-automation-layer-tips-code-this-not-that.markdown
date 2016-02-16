---
published: false
title: SpecFlow Automation Layer Tips - Code This, Not That
layout: post
tags: [SpecFlow, Tips, AutomationLayer]
---
I read an interesting article about SpecFlow tips called "[Code This, Not That - Specflow Edition](http://joebuschmann.com/code-this-not-that-specflow-edition/)" by Joe Buschmann the other day. Go read it, it is well worth your time - I especially like his thoughtful use of regular expressions in the "When passing binding parameters (part 1)" section.

In this post, I will enhance one of Joe's tips and add one of my own.

## Working with Tables

In his first section, "When working with tables..." Joe tells us to use the `CreateInstance<T>` and `CreateSet<T>` extension methods from the `TechTalk.SpecFlow.Assist` namespace. I encourage you to take this one step further and use a step argument transformation.

{% gist DirkRombautsPicklesPro/886adcb97cd06cb56e3d StepArgumentTransformation.cs %}

A step argument transformation is a binding method with the `StepArgumentTransformation` attribute. Normally SpecFlow would throw an error when it encounters `GivenTheFollowingAddress`, because that step method has a parameter of a non-standard type. However, if there are is a step argument transformation that creates an instance of that non-standard type, then SpecFlow will call that step argument transformation and use its result as an argument for the step method.

The advantage of this technique is that it keeps the logic for creating an `Address` out of a SpecFlow `Table` in one place, instead of copying that bit of code in every step method that uses an `Address`.

## Argument Values: To Quote or Not To Quote (and How)

Often, your steps will contain argument values. In fact, the very first step in the example scenario that SpecFlow adds to a new `.feature` file contains an argument: 50. I like to surround argument values with quotes in order to make it more explicit that this is something that can vary.

{% gist DirkRombautsPicklesPro/886adcb97cd06cb56e3d QuotesOrNoQuotes.feature %}

Whether you do this is probably a matter of taste, but I prefer to make things explicit so that there is less room for misunderstandings.

Once you've taken the decision to surround your argument values with quotes, you may ask yourself whether to use single quotes or double quotes.

{% gist DirkRombautsPicklesPro/886adcb97cd06cb56e3d SingleQuotesOrDoubleQuotes.feature %}

Readability of the scenario is fine either way, so in order to decide let's turn to the step definition methods. The respective attributes for those steps look like this:

{% gist DirkRombautsPicklesPro/886adcb97cd06cb56e3d SingleQuotesOrDoubleQuotes.cs %}

The single quote version looks much more readable.

So I prefer to quote argument values and to use single quotes for it.

## Summary

In this post I showed you how to make the automation layer code for dealing with tables even more DRY (Don't Repeat Yourself) than Joe Buschmann's version. And I explained that I quote argument values in order to increase explicitness in the scenario and that I use single quotes in order to increase readability in the automation layer.