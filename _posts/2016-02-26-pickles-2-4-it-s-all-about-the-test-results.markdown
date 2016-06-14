---
published: true
title: Pickles 2.4 - It's All About the Test Results
layout: post
tags: [SpecFlow, BDD, SpecificationByExample, Pickles, LivingDocumentation]
---
A couple of minutes ago, I pressed the Enter key to start the deployment of version 2.4 of Pickles. The packages should become available soon on [Nuget](http://www.nuget.org/packages?q=pickles) and [Chocolatey](https://chocolatey.org/packages?q=pickles).

<!--more-->

I'm very excited about this release, because I was able to invest a significant amount of time to eliminate some of the biggest thorns in my side with regard to the test result providers:

- All test result providers are now able to give the result of individual examples in a scenario outline: [#285](https://github.com/picklesdoc/pickles/issues/285), [#286](https://github.com/picklesdoc/pickles/issues/286) and [#287](https://github.com/picklesdoc/pickles/issues/287).
- The code has been made more readable, and I removed a lot of "copy-paste inheritance".
- Test coverage is now at the same level for all test result providers, including Cucumber JSON.

Thanks to those improvements, I was able to add (in a reasonable amount of time) support for the test result format that [VsTest.Console.exe](https://msdn.microsoft.com/en-us/library/jj155796.aspx) produces, which is similar by identical to the format that MsTest produces: [#280](https://github.com/picklesdoc/pickles/issues/280). Use `vstest` as parameter for the test results format.

With the recent increase in supported test result formats, the list of radio buttons in the GUI was getting out of hand, and I replaced it with a dropdown list: [#297](https://github.com/picklesdoc/pickles/issues/297).

![Dropdown list with test result formats](/public/img/2016-02-26_PicklesUI.png)

I also included some bug fixes: the Cucumber JSON test result provider now deals correctly with background steps, for both the Ruby and the JavaScript versions of Cucumber: [#293](https://github.com/picklesdoc/pickles/issues/293). And I was able to fix a long-standing bug that resulted in corrupt Word documents: [#261](https://github.com/picklesdoc/pickles/issues/261).

This is not the end of the road for the Test Results - I hope to improve them even further and above all make them more efficient. For now, though, this is a great intermediate stage.
