---
published: true
title: How To Name Your Scenario Outlines
layout: post
tags: [BDD, SpecificationByExample, SpecFlow]
---
Last week, I attended [Gaspar Nagy's Developing with SpecFlow](https://skillsmatter.com/courses/539-gaspar-nagy-s-developing-with-specflow) course, and in this article I'm sharing one of my concrete learnings: how to name a scenario outline.

There are are a couple of schools of thought on how to name a scenario, but they all agree on this: the name of the scenario should reflect what the scenario is about, and should help you to grasp what business requirement was likely not met if the scenario fails.

For example, "Scenario 1" is not a good title, but "Suggest a long break after the 4th work block" is good.

This is all well and good for scenarios, but for a scenario outline things get more complicated.

<!--more-->

Consider the following scenario outline:

{% gist DirkRombautsPicklesPro/833bc8ded21f82fc4a02591bde20460a ScenarioOutline.feature %}

Now suppose one of the scenarios fails. The title "Suggest either a long break or a short break after the nth work block" doesn't help me to figure out what might have gone wrong. It's difficult to make the title more concrete, because if I make the title better for one of the examples, then the title will be bad for the other examples.

Scenario Outlines have a peculiarity that we can exploit: the examples table can contain more columns than are required in the outline. So we can add an additional column with information about what makes each example unique:

{% gist DirkRombautsPicklesPro/833bc8ded21f82fc4a02591bde20460a ScenarioOutlineWithCaseColumn.feature %}

If we write this additional column as the first column, then the SpecFlow code generator will use the value from that column to name the test method. This means that the name of the test in the Test Explorer tool window will consist of both the title of the scenario outline and the value in the case column. Compare the names of the tests in the screenshot:

![Test Names for Scenario Outlines](/public/img/2016-05-31_ScenarioOutlineTestNames.png)

When one of the `SuggestEitherALongBreakOrAShortBreakAfterTheNthWorkblock_*` scenarios fails, I don't know what business rule might have been broken. If one of the `SuggestABreakAfterAWorkBlock_*` scenarios fails, I have a clear indication of what might be wrong.