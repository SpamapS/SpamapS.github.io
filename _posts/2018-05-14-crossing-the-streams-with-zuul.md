---
layout: post
status: publish
published: true
title: Crossing The Streams with Zuul
author: clint
categories:
    - Technology
tags:
    - zuul
    - cicd
    - automation
    - development
    - vcs
    - git
---
You use CI, right? I mean, EVERYBODY has CI. You have a Jenkins, therefore, you do CI?

But do you? Really? I feel that we've lost sight of what the original term [Continuous Integration][ci] means.

Lately when I discuss with developers, they throw the letters around without
thinking about what the words mean. CI is just running tests, right? CI is
maybe building things when you land code. CI. Jenkins does CI. Travis does
CI. That's CI.

But really, the original term's origin had more to do with how your developers
work on their changes, than the testing. The testing and automated building
was just the immediate effect of continuously integrating code into your
trunk/tip/master/etc. It turns out, in the past, people would work on branches
for a long time (except that's not the past) and only integrate those
changes together with other developers' work on mainline periodically.

But wait, that sounds like [git flow][gitflow], or, what most people end up
doing with GitHub. Branch, work work work, merge in master periodically,
then when you're "done", ask to be merged in to master.

The misunderstanding of CI has gotten so bad that people had to clarify what
they mean by calling it "[Trunk based development][trunkdev]". But read the
description of CI, and the descriptions of Trunk Based Dev, and they pretty
much sound the same. There is a difference, however. With CI, you, the developer
stay branched, but merge in changes from mainline constantly. In Trunk Based Dev,
you push your changes to mainline frequently. So with CI, your batch size stays
relatively large, but with TBD, your batch size is "whatever you can land fast".

So, first and foremost, let's accept that many shops do not, in fact, do
CI entirely. Nor do most shops do TBD. What most shops do is [git flow][gitflow]
with a build server.

So, next question: why aren't shops doing CI? Well, most likely because *it is
really hard*. The tools we have don't do a ton to help us.

[ci]: https://en.wikipedia.org/wiki/Continuous_integration
[gitflow]: https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow
[trunkdev]: https://trunkbaseddevelopment.com/
