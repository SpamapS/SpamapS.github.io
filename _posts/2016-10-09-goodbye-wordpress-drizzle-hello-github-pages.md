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
    was insane enough to attempt this. It required patching ~~Drizzle~~WordPress to support
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
[Drizzle](http://drizzle.org) as the backend database. As far as I know, I'm the only person who
was insane enough to attempt this. It required patching ~~Drizzle~~WordPress to support
valid dates (MySQL allows 0000-00-00 in some cases, wordpress uses this
heavily), and that patching has just gotten too difficult to keep up with.<sub>[1](#wordpress-drizzle-plugin)</sub>

This also included running on a *t1.micro* at Amazon. This helped me
learn how AWS works, and that was useful, but at this point, I think
the $17/month or so that I'm paying for it isn't really worth it, and
I don't login enough to learn much anymore.

So I've decided to make the jump to GitHub pages. I like the idea of
having a nice static page for my blog. Comments can happen on social
media.

Thanks GitHub for giving us coders a place to drop a static web page.

And, so long Drizzle, and thanks for all the fish.

<a name="wordpress-drizzle-plugin">Edit 1, October 10, 09:27 PDT</a>: *I also wrote a [wordpress
drizzle plugin](https://launchpad.net/wordpress-drizzle) to handle
the more straight forward elements of Drizzle's more strict SQL dialect,
but that never gave me any trouble once written. The issue with 0000-00-00
is that it is used all over WordPress as a string literal and there's no
single place to change that.*
