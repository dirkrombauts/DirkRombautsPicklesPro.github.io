---
published: true
title: A Pickles Task for FAKE
layout: post
tags: [OSS, Fake, Pickles, LivingDocumentation]
---
Pickles uses [FAKE](http://fsharp.github.io/FAKE/), a DSL for build tasks, to automate large parts of the build process. FAKE is really a quite accessible library for automating build scripts, and the fact that the build scripts are written in F# is rather charming (rather than a distraction).

FAKE naturally contains a lot of tasks, for example for copying files, compiling projects, creating NuGet packages. The other day I learned that FAKE also includes a task for Pickles! That's right, you can generate your Living Documentation as a part of your FAKE build script!

The wonderful thing is that this happened without involvement from myself. This is the result of someone in the OSS community thinking "wouldn't it be cool if Pickles and FAKE would work well together" and then going ahead and implementing it. This kind of recognition and contribution is one of the most sincere gifts that the community can make to an OSS project.

It totally made my day. It shows the strenght of a vibrant OSS community. Thank you!