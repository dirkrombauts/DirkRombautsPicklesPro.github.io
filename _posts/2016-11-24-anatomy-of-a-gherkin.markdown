---
published: true
title: Anatomy of a Gherkin
layout: post
tags: [BDD, SpecificationByExample, SpecFlow, Gherkin, Cucumber, Pickles]
---
In this post I will show you around the Gherkin syntax that you will use to write `.feature` files. I will discuss the first few lines of a `.feature` file, and then dive into scenarios, the different kinds of steps, ways of including data, how to add comments and tags, what the Background part is for, what a Scenario Outline is and when to use it. 

<!--more-->

## The beginning

The first line in a `.feature` file usually specifies the name of the feature. It consists of the keyword `Feature` followed by a colon (':'), a space and then the name of the feature.

```feature
Feature: My first SpecFlow Feature
```

You can use the next lines to give some information about the feature, like background information of business rules. You can use as few or as many lines as you like. Gherkin treats the description as plain text, so you can use your own conventions to provide structure. Since [MarkDown](https://daringfireball.net/projects/markdown/) is increasingly becoming the Lingua Franca of software development documents, I recommend using MarkDown to format your descriptions. If you use a living documentation generator like [Pickles](http://www.picklesdoc.com), the MarkDown sections will be rendered as formatted text.

```feature
Feature: My first SpecFlow Feature
    In order to avoid silly mistakes  
    As a math idiot  
    I want to be told the sum of two numbers
    
    Using [Reverse Polish Notation](https://en.wikipedia.org/wiki/Reverse_Polish_notation),
    we first enter the two operands of a calculation. The calculation is then performed
    immediately when we enter the operation.
```

## A Scenario

Next comes the first scenario. A scenario has a name, and you should take some care when choosing it. It should tell at a glance you what the scenario is about. Feel absolutely free to change it when you don't like it, and change it again until it feels right.

```feature
Scenario: Addition of Two Positive Numbers
```

You can use the next lines to give some information about the scenario, just like with the Feature. Some information you should consider writing down:

- Why did you choose this particular scenario or example? What makes it special?
- What business rules are involved in this scenario?
- What is the reason for the expected result of the scenario?

```feature
Scenario: Addition of Two Positive Numbers
    The addition of two positive numbers is the easiest case of addition.
    The result will always be greater than the two numbers so we don't need to deal
    with negative numbers here.
```

## Steps

A scenario without steps is boring, not to mention pointless. The best name in the world or the best description in the world can only help so much. They are not going to do much good if we don't provide some actual information on what is going on in the scenario. We do that with steps. There are three kinds of steps: Given, When and Then steps.

### Given Steps

Given steps set the stage for the scenario. You can use them to provide data, or to describe the state of your system under description. You can also use them to describe actions that lead up to the action that we are to specify. It is very common to use multiple Given steps in a scenario.

```feature
    Given I entered '50' into the calculator
    Given I entered '70' into the calculator
```

Given steps tend to be written in the past tense. When you consider the timeline of the steps in a scenario, the When step is usually the one where you say "now". All that comes before "now" is in the past, so the Given steps happened in the past.

### The When Step

The When step is where the action happens. It is the place where you push the metaphorical button to see what will happen. Technically you can write multiple When steps, but it is good practice to write only one. Doing so keeps your scenario focused on a single thing, and that makes it easier to understand.

```feature
    When I press the Add button
```

The When step is usually written in the present tense. Within the timeline of the steps in a scenario, the When step carries the feeling of "now".

### Then Steps

The Then steps express the expected outcome of the When step. You can record any observable behaviour and data here. Since a scenario is a relatively large unit of work, it is perfectly alright to write multiple Then steps.

```feature
    Then the display should read '120'
```

Then steps are usually written so they express an expectation: "should", "must", and "have to" are common verbs here.

### And Steps and But Steps

There are two more kinds of steps you can use: And and But. I don't consider them proper step types because they only make the scenario easier to read. They do not affect the scenario in any other way.

For example: when you write multiple Given steps, the scenario will sound "forced" when reading or speaking it. You can write the second (and third, …) Given as And steps, resulting in better readability.

```feature
    Given I entered '50' into the calculator
    And I entered '70' into the calculator
```

I regularly use And steps, but I can't remember ever using a But step. Please let me know if you encounter a scenario where you can use a But step to improve readability.

### The Complete Scenario

The complete scenario now reads:

```feature
Scenario: Addition of Two Positive Numbers
    The addition of two positive numbers is the easiest case of addition.
    The result will always be greater than the two numbers so we don't need to deal
    with negative numbers here.
    
    Given I entered '50' into the calculator
    And I entered '70' into the calculator
    When I press the Add button
    Then the display should read '120'
```

## Step Arguments

Sooner or later you are going to want to use data in your scenarios. After all, many software applications are about processing data! There are three ways to use data in a `.feature` file: inline, table and document string.

### Inline

You can use data in the text of a step. You already saw this in the previous sections:

```feature
    Given I entered '50' into the calculator
```

You can consider any part of the step text as data. I like to surround data by single quotes, but that is a matter of preference. The following example is just as valid as the previous one:

```feature
    Given I entered 50 into the calculator
```

I like to be clear about which parts of a step text are just text and which parts are data, and for that reason I surround data in single quotes.

### Table

When describing complex entities, scenarios tend to become verbose and tedious to read. Imagine a book shop with a book in its catalogue:

```feature
    Given I have a book
    And that book is titled 'Bridging the Communication Gap'
    And the author is Gojko Adzic
    And the book's ISBN number is '0955683610'
    And the book has '284' pages
    And the book costs '29' Euro
```

Now imagine the catalogue contains several books - this will get out of hand quickly. Tables can make this more readable:

```feature
    Given I have this book
    	| Title                          | Author      | ISBN       | Pages | Price |
	    | Bridging the Communication Gap | Gojko Adzic | 0955683610 | 284   | 29    |
```

The first line of the table contains the column headers that tell us what the data in the columns mean. The next line contains one set of data. You can of course have multiple lines of data in a table:

```feature
    Given I have these books
	    | Title                          | Author      | ISBN       | Pages | Price |
	    | Bridging the Communication Gap | Gojko Adzic | 0955683610 | 284   | 29    |
	    | Specification By Example       | Gojko Adzic | 1617290084 | 296   | 35    |
```

It is up to you how the data in the table is interpreted. Usually, one line in a table represents one entity: in the above table, each line represents one book.

### Document String

Sometimes your data does not fit on a singe line, for example when you are describe a mass mailing merge. For that kind of data, you can use a document string argument. On the line after the step you write three double quotes (`"`) to begin the document string. Another line with three double quotes marks the end of the document string.

```feature
Given I have this text in the mail template
    """
    Dear Madam, dear Sir,
    
    Lorem ipsum dolor sit amet, consectetur adipiscing elit,
    sed do eiusmod tempor incididunt ut labore et dolore
    magna aliqua. Ut enim ad minim veniam, quis nostrud
    exercitation ullamco laboris nisi ut aliquip ex ea commodo
    consequat. Duis aute irure dolor in reprehenderit in
    voluptate velit esse cillum dolore eu fugiat nulla pariatur.
    Excepteur sint occaecat cupidatat non proident, sunt in
    culpa qui officia deserunt mollit anim id est laborum.
    """
```

## Comments

There are two places in a `.feature` file where you can write a free-text description: after the Feature line, and after each Scenario line. These descriptions should capture information that is relevant from a business point of view.

Sometimes you may want to include additional information that is relevant from a technical point of view. For example about particular ways of automating a step. You can write that kind of information as a comment.

A comment is a line that starts with a `#` sign. Everything on that line will be considered a comment.

```feature
# this is some technical information
```

I hardly ever use comments. I use the free-text descriptions with business-relevant information a lot, but almost never the `#`-style comments.

## Tags

Anybody who uses Twitter will be familiar with tags. They are a convenient way of categorising tweets, and you can use them to perform a thematic search. You can do the same thing in a `.feature` file, except that tags are not prefixed by a `#` but rather by a `@`.

```feature
@underSpecification @ui
Scenario: Addition of a Small Positive Number and a Large Negative Number
```

You can add tags before any line in a scenario, even before a single step. I have not needed that particular behaviour yet, though. I most often use tags before scenarios. If you add a tag before the Feature line, it is as if you add that tag to each scenario in the `.feature` file.

```feature
@thisTagAppliesToEachScenario
Feature: This Feature Has a Tag

Scenario: The first scenario, it is considered to have the 'thisTagAppliesToEachScenario' Tag

Scenario: The second scenario, it is considered to have the 'thisTagAppliesToEachScenario' Tag Too
```

## Background

If you use Visual Studio to edit your `.feature` files, you will notice a "Background" keyword in the IntelliSense list. It is tempting to think that this is an element where you can write some background information about the Feature. Tempting, but misleading. If you want to provide additional information, simply use the Description area.

The Background element can contain one or more steps that are considered to be part of all scenarios in the `.feature` file. The steps in the Background element come before the steps in the scenarios. These two notations are equivalent:

```feature
Feature: With Backgrounds
Background:
    Given I perform a first step

Scenario: First Scenario
    Given I perform a second step

Scenario: Second Scenario
    Given I perform a second step
```

```feature
Feature: Without Backgrounds

Scenario: First Scenario
    Given I perform a first step
    Given I perform a second step

Scenario: Second Scenario
    Given I perform a first step
    Given I perform a second step
```

Personally, I don't use Backgrounds often. I like to have all information about a scenario in a single place. If there are steps both in the Background and in the Scenario itself, I am forced to look in two places in order to understand the scenario.

Another, more practical, argument against Backgrounds is this: if you want to move a Scenario to a different Feature file, you need to remember to copy the Background steps as well. If the destination Feature file contains Background steps as well, you then need to take care that the moved Scenario fits in with those steps too.

## A Scenario Outline

It often happens that you have a lot of similar scenarios, especially if you are describing calculations. Instead of producing a number of scenarios that have the same steps with different values, you can use a Scenario Outline.

```feature
Scenario: Addition With Two Positive Numbers
    Given I entered '50' into the calculator
    And I entered '70' into the calculator
    When I press the Add button
    Then the display should read '120'

Scenario: Addition With a Smaller Positive and a Larger Negative Number
    Given I entered '50' into the calculator
    And I entered '-70' into the calculator
    When I press the Add button
    Then the display should read '-20'
```

You can write this using a Scenario Outline:

```feature
Scenario Outline: Addition
    Given I entered '<first argument>' into the calculator
    And I entered '<second argument>' into the calculator
    When I press the Add button
    Then the display should read '<result>'
    
    Examples:
        | case                                        | first argument | second argument | result |
        | two positive numbers                        | 50             |  70             | 120    |
        | smaller positive and larger negative number | 50             | -70             | -20    |
```

You use placeholders in the steps, like `<first argument>`. The Examples table then needs a column that is called `first argument` exactly. Each column in the table represents a placeholder in the Scenario Outline, and each row in the table represents a Scenario.

You can add additional columns to the table, that do not correspond to a table in the Scenario Outline. It is good practice to provide a column named "case" (or similar) that describes what this particular line is about.

Scenario Outlines can save you a lot of repetitive scenarios, but they come at the cost of decreased readability. You have to switch between the steps and the line in the Examples table in order to get the full picture of the Scenario you are currently reading.

A word of warning: experience shows that people tend to over-use Scenario Outlines. I have seen Scenario Outlines with just one line in the Example table. I have also seen Scenario Outlines with tens of lines in the Examples table where people went overboard and specified every possible combination of inputs. Always keep in mind that the goal is to keep the scenarios readable. Sometimes that goal is best served by using a Scenario Outline, but sometimes that goal is served better by duplicating scenarios.

## Sprechen Sie Deutsch? Parlez-Vous Français? Spreekt U Nederlands?

The goal of the scenarios is to improve the communication among all parties in a software project. If your business representatives work in a non-English environment, giving them scenarios in English is counterproductive. Fortunately you can write scenarios in languages other than English.

You can use a special comment at the beginning of your feature file: `# language:` followed by a two-letter code for the language of the feature file.

```feature
# language: de
Funktionalität: Addition

Szenario: Addition Von Zwei Positiven Zahlen
	Gegeben sei dass ich '50' eingegeben habe
	Und dass ich '70' eingegeben habe
	Wenn ich auf 'Plus' drücke
	Dann soll auf dem Display '120' stehen
```

The list of supported languages can be found [on GitHub](https://github.com/cucumber/gherkin/blob/master/gherkin-languages.json), where you can check out the keywords for specific languages as well.

## Summary

Now you know everything you need to know in order to start writing Features and Scenarios. In addition to showing the mechanics of each individual part, I also gave some advice on how and when to use them. That advice is based on my experience, so take it with a grain of salt and think whether it applies to your situation too!