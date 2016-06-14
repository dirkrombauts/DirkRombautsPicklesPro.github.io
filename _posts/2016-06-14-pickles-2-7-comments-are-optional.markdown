---
published: true
title: Pickles 2.7 - Comments are optional
layout: post
tags: [SpecFlow, BDD, SpecificationByExample, Pickles, LivingDocumentation, Gherkin]
---
Earlier today, I released version 2.7 of Pickles. One of the features introduced in [version 2.6](/2016/04/12/pickles-2-6-the-cukeup-edition.html) of Pickles in April was the inclusion of #-style comments in the living documentation. The reaction to that feature was mixed: people liked the ability to include #-style comments in principle, but some people would like to decide whether to include them for themselves.

Version 2.7 of Pickles now offers that ability, thanks to the work of [William C. Smith](https://github.com/ocsurfnut). In the command line version of Pickles, you can use the `enableComments` argument to control inclusion of #-style comments. The default value is `true`, so if you do nothing, the #-style comments will be included as in version 2.6. See the [documentation](http://docs.picklesdoc.com/en/latest/ArgumentsEnableComments/) for the other runners.

Happy Pickling!