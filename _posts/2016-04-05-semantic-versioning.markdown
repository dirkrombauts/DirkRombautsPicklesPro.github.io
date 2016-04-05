---
published: true
title: Semantic Versioning
layout: post
tags: [Pickles, SemanticVersioning, SemVer]
---
*Note: this post has no direct relation with Behaviour Driven Development. It has to with programming, and it is a topic where business people like to stake their claim as well. So I think it fits the target audience for my blog.*

There's a saying, usually [attributed](http://martinfowler.com/bliki/TwoHardThings.html) to Phil Karlton, that goes "There are only two hard things in Computer Science: cache invalidation and naming things."  Surely a corollary of that must be "Naming a version is fiendishly hard".

When it comes to naming the version of a software product, business people and marketing people have a track record of doing wild things. Does anybody remember that Microsoft Word went from version 2.0 to 6.0 in one leap so that they could draw level with WordPerfect 6.0? Or Microsoft Windows jumping from 3.11 to 95? Those versions are a marketing vehicle, nothing more.

One could argue: at least they tell me something about the chronological order: surely a version that is marketed with a higher number must come before a version with a lower number? Not quite: Microsoft recently published a preview of what is currently named 'Visual Studio "15"'. The current stable version of Visual Studio is Visual Studio 2015, so there's an amusing number of ways in which versions 2015 and "15" can be confused.

Wouldn't it be great if the version of a software product or library would give us some solid, dependable information? For example, the version might give an indication about the content that we can expect in the new version. It might even tell us something about the compatibility of the new version with other products and libraries. It might, in effect, tell us whether we can safely upgrade to the new version.

There is a way of versioning which does exactly that: [Semantic Versioning](http://semver.org/). By comparing two semantic version numbers, you know at a glance whether this is a major update, a minor update or a patch. A major update says "Caution, things have changed, you will need to invest time and energy to adapt to this new version". A minor update says "There are new things but the old things will work as before". A patch says "Some bugs were fixed, but no new content or things that were changed."

For example: if I have version 1.0.0, then version 1.0.1 will fix some bugs. Everything not affected by the bug fix will work like before, and the area affected by the bug fix will now work as it was supposed to work (hopefully). In practice this means I can upgrade to the new version without spending much thought on it.

When version 1.1.0 comes along, there will be new features. Everything not part of the new features (and optional bug fixes) will behave like it did before. In practice this means I can upgrade to the new version, and I expect to spend a little time to determine whether the new features may benefit me.

When version 2.0.0 comes along, I know that Things Have Changed. The program or library will interact with the outside world in new and sometimes surprising ways. In practice this means I should set aside a considerable amount of time to upgrade to the new version and to adapt my own system to work with the new version.

You might well wonder why I wrote about this. Semantic Versioning is on the rise (which is a good thing) and Nuget closely (thought not perfectly) supports it. During maintenance of [Pickles](http://www.picklesdoc.com) I have come to rely on Semantic Versioning when upgrading the libraries that Pickles depend on. Last week one of those upgrades exploded in my face when I updated [Automapper](http://automapper.org/) from version 4.1.1 to 4.2.1. Based on Semantic Versioning I expected no problems, but I was sadly disappointed when I found out that one of the classes I rely on [was gone](http://stackoverflow.com/questions/35187475/autofac-and-automapper-new-api-configurationstore-is-gone). One needed change led to another and another and I ended up with a number of tests failing in subtle ways. I decided to roll back to version 4.1.1.

Had Automapper used Semantic Versioning and named their new version 5.0.0, then I would have been warned that something like that might happen. Now, it was an unpleasant surprise that cost me time and eventually prevented me from upgrading.

## Summary

So with Semantic Versioning we have a versioning scheme that tells us how compatible the new version is with the old version, and what order of magnitude of time and effort will be needed to upgrade.  Compare that to marketing-driven versioning which tells you nothing much and I'm sure you'll agree that Semantic Versioning is a much richer versioning scheme.
