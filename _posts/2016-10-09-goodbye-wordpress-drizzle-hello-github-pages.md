---
layout: post
status: publish
published: true
title: Goodbye Wordpress+Drizzle+AWS, Hello Github Pages
author: clint
author_login: clint
author_email: clint@fewbar.com
author_url: http://fewbar.com
excerpt: >
    For the past 6 years, my website has been running on WordPress, with
    Drizzle as the backend database. As far as I know, I'm the only person who
    was insane enough to attempt this. It required patching Drizzle to support
    valid dates (MySQL allows 0000-00-00 in some cases, wordpress uses this
    heavily), and that patching has just gotten too difficult to keep up with.

    This also included running on a t1.micro at Amazon. This helped me
    learn how AWS works, and that was useful, but at this point, I think
    the $17/month or so that I'm paying for it isn't really worth it, and
    I don't login enough to learn much anymore.
categories:
- Life
tags:
- jekyll
- wordpress
- drizzle
- aws
- ec2
- github
---

For the past 6 years, my website has been running on WordPress, with
Drizzle as the backend database. As far as I know, I'm the only person who
was insane enough to attempt this. It required patching Drizzle to support
valid dates (MySQL allows 0000-00-00 in some cases, wordpress uses this
heavily), and that patching has just gotten too difficult to keep up with.

This also included running on a t1.micro at Amazon. This helped me
learn how AWS works, and that was useful, but at this point, I think
the $17/month or so that I'm paying for it isn't really worth it, and
I don't login enough to learn much anymore.

So I've decided to make the jump to github pages. I like the idea of
having a nice static page for my blog. Comments can happen on social
media.

Thanks GitHub for giving us coders a place to drop a static web page.

And, so long Drizzle, and thanks for all the fish.
