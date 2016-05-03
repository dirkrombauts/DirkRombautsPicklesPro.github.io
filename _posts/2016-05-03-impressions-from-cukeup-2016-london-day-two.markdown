---
published: true
title: Impressions from CukeUP! 2016 London - Day Two
layout: post
tags: [SpecFlow, BDD, SpecificationByExample, Pickles, LivingDocumentation, Cucumber]
---
Last month, I attended
[CukeUP! 2016 London](https://skillsmatter.com/conferences/7606-cukeup-2016),
the definitive BDD conference in Europe. It was a fantastic experience: I got
to meet many interesting people, to learn (and try out) new insights and
techniques. Here are my thoughts from day two!

## Keynote: A BDD Manifesto

The keynote of day two was delivered by 
[Jenny Martin](https://jennyjmar.com/). She invited us to think beyond the techniques of
agile and BDD, and to think about why we are doing all this: to discover the business goals,
and deliver value early. She discussed an outside-in model for doing this, called OOPSI for
Outcomes Outputs Process Scenarios Inputs. You need to begin with the end in mind,
because if you do it the other way around it ISPOO. As we explore the examples,
we need to looking for dragons, otherwise we will get burnt (again).

## CHEESECAKE – The story of Typeform's automatic test suite

By Aida Manna and Gloria Hornero of [TypeForm](http://www.typeform/). They
described their road of discovery of using test automation effectively. Not much
new information for me but it did confirm that I am not alone in facing
the problems I had with test automation in the past.

## Workshop: Workshop: Modelling by Example

Moderated by [Konstantin Kudryashov](https://twitter.com/everzet) and
[Ciaran McNulty](https://twitter.com/ciaranmcnulty). We used scenarios about
an airline offering a "miles programme" to design a domain model. We went
through a couple of iterations of talking to a business representative,
writing down our insights in the form of examples, and using those examples
to drive the design of the classes in our domain model. Konstantin and Ciaran
repeatedly stressed the importance of using the scenarios as a help to
understand the workings of a system, and not as test cases.

## Workshop: Bringing User Stories to Life

This workshop was my highlight of the second day of the conference. Led by
[Gemma Cameron](https://twitter.com/ruby_gem), this workshop was all about
transforming boring (and often meaningless) user stories into something you
can identify with. User stories are called stories for a reason: there is
a story behind a feature request, a story that explains how people who
use the software will benefit from it.

Gemma asked us to write a user story in the classic "as a ... I want to ... so that ..."
format. For one story per 4-person table we elaborated on the story behind it,
and finally we made the story come to life by drawing a little comic
that tells the story. Going through this process builds empathy with the
people in the story, and motivates you to actively want to build this
software and to do a stellar job of it.

## BDD in Moderation - A talk from the Trenches 

By [Keith Salisbury](https://twitter.com/ktec) and [Joe James](http://joejames.io/).

Keith and Joe talked about their journey toward effective use of BDD. They evolved
from having many small scenarios that each tested a small aspect of the system
to having a few large scenarios that showed a journey through the system
to having a few small and concise scenarios that explained the behaviour of the system.

Some of the techniques they used to achieve this was having a few sets of well-known
data for the scenarios that were set up in the background.

## Behaviour-Driven Development: The Bigger Picture

By [Paul Rayner](http://thepaulrayner.com/). He answers some common questions like
"If [BDD] is a collaboration tool, [then] why is it used to automate tests?" and
"who writes the gherkin files?" by giving a big picture overview of the different
stages in the flow of using BDD in a team. I recommend people who are new to BDD
to watch the [recording of his presentation](https://skillsmatter.com/skillscasts/7589-behaviour-driven-development-the-bigger-picture).

## Lightning talks

### BDD for 8 year olds B-D robotics

By [Colin Deady](https://www.linkedin.com/in/colindeady) where he talks about
using BDD to control robots (Behaviour Driven Robotics). He uses those
to introduce 8 year old kids to BDD.

### Fixed mindset is sabotaging for you and your team

Another talk by [Ulrika Malmgren](https://twitter.com/ulrikama). A very personal
introspection about how having a fixed mindset - a mindset where everything is
set in stone, where you are either perfect at something or no good at all - will
hinder or even prevent you from accomplishing anything significant. It is only
when letting go of that, when allowing yourself to go through the intermediate
stages of learning, that you can grow and evolve beyond your current state.

As someone who suffered from a fixed mindset myself, I can very much
relate to Ulrika's tale, and I admire her courage in getting up
in front of 150+ people and talk about this very personal topic.

Thank you, Ulrika!

### Simple expressions in steps instead of regular expressions 

By Jens Engels, the maintainer of [Behave](http://pythonhosted.org/behave/),
the python implementation of Cucumber. He talks about his efforts
to reduce the usage of regular expressions in step definitions, and to
replace them with placeholder names and types. It does make step
definitions much more readable!


### The Delayed Gratification Principle

By [Stephen Anderson](https://twitter.com/teedor76). The Delayed
Gratification Principle means you code the bits that you don't like
first. First you code the unhappy path, and only then the happy path.
This will help preserve your enthusiasm over the course of a project:
initially you have a lot of enthusiasm, and when the enthusiasm
diminishes, you will be in the happy path phase and derive enthusiasm from that.

### How can a living documentation help me and where do I get one

By yours truly. Of the three goals of BDD (Common Understanding,
Living Documentation and Outside-In Development), the first and the third
receive a lot of press. The Living Documentation is sometimes mentioned
in passing but there's not a lot of in-depth info. In my talk I briefly
explain what makes a documentation living, how you can use
[Pickles](http://www.picklesdoc.com) to create one, and why it is
important to have one.

### Property based testing

By [Mathias Verreas](https://twitter.com/mathiasverraes). An excursion
into functional programming, this talk describes how to use properties
of a function to randomly generate some interestingly permutated test
data that verifies the implementation of the function. For example,
a function that doubles its input will always produce a positive output,
so you might feed it some negative inputs to verify this.

## Summary

In summary, I can honestly say that CukeUP! London 2016 has been a 
fantastic and uplifting experience. I had many interesting conversations
with many different people, and listened to some pretty
interesting presentations. I learned a lot, and feel highly motivated
to continue on this new path of being a BDD Coach. I hope
I will be able to return to next year's conference!
