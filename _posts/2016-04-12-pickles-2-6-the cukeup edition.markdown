---
published: true
title: Pickles 2.6 - The CukeUP Edition
layout: post
tags: [SpecFlow, BDD, SpecificationByExample, Pickles, LivingDocumentation]
---
Earlier today, I released version 2.6 of Pickles, in time for the [CukeUP conference](https://skillsmatter.com/conferences/7606-cukeup-2016) in London this week.. The packages are available now on [Nuget](http://www.nuget.org/packages?q=pickles) and [Chocolatey](https://chocolatey.org/packages?q=pickles).

*Shameless plug: I will hold a lightning talk at the conference on Thursday about "The Dark Side of BDD". I hope to see you there!*

I'm not 100% certain, but I'm fairly positive that this version of Pickles scores a new record of most external contributors in a single release. No less than three people dedicated some of their time toward improving Pickles. A heartfelt "thank you" to (in alphabetical order) [Aaron Rich](https://github.com/aaronjrich), [Daniel Pullwitt](https://github.com/danielpullwitt) and [Ludwig Jossieaux](https://github.com/ludwigjossieaux).

## Search for multiple tags in the dynamic HTML version

One of the attractions of the dynamic HTML version is that it includes a search functionality: you can search by tag or by feature name. This search now got better: it is now possible to search for multiple tags. Adding two tags in the search field will show only those features where a scenario has at least one of those tags.

![Search by multiple tags](/public/img/2016-04-12_SearchByMultipleTags.png)

## Display Comments

In the past, comments in a .feature file (lines starting with a `#` sign) would not be displayed in the output of Pickles. Thanks to the new version of the parser, we can now display those comments.

![Display comments](/public/img/2016-04-12_DisplayComments.png)

## Two Bugfixes

When using the nUnit test provider, certain characters would prevent Pickles from mapping scenarios to results. This has been fixed.

A missing description could sometimes lead to a crash. This has been fixed too.

## Other Changes

I updated several external components, including the brand-new version 4 of the parser.

And last but not least, the packages and the GUI runner now use the new logo.

## Summary

Version 2.6 of Pickles couldn't have happened without contributions from the community. Thanks again to everybody who contributed to this release, and to all past releases as well.