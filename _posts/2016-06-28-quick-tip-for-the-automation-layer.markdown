---
published: true
title: Quick Tip for the Automation Layer
layout: post
tags: [BDD, SpecFlow, Code, AutomationLayer]
---
Automation Layer code is just like any other piece of code. That means all the same rules apply to make it "good" code: SOLID Principles, refactoring, and good naming of variables to name just a few. Today's post is about the latter: good naming of variables.

<!--more-->

It is important that the names of variables express the purpose of the variables. Nowhere is this more important than when comparing values. Consider this snippet:

{% gist DirkRombautsPicklesPro/b0aa2883f8232e2b6d91415d9fae98a3 UnclearVariables.cs %}

What does `p0` mean? An integer called `i` is just about understandable, but rather lazy. `i` expresses the actual result, and `p0` expresses the expected result. That gives us:

{% gist DirkRombautsPicklesPro/b0aa2883f8232e2b6d91415d9fae98a3 ClearVariables.cs %}

Thanks to the clearer variable names, we now notice that we made an error when calling the assertion: `Assert.AreEqual` takes the expected value as the first argument and the actual value as the second argument. That's very confusing, see my post about [using assertion libraries](http://blog.picklespro.com/2016/05/11/using-assertion-libraries.html) for a better way of writing this.

After correcting the order of the parameters, we end up with:

{% gist DirkRombautsPicklesPro/b0aa2883f8232e2b6d91415d9fae98a3 CorrectOrder.cs %}

But again, consider using an assertion libraries to more clearly express your intention when writing assertions.