---
layout: post
status: publish
published: true
title: OpenStack needs an Architecture WG - Because we all can't be Gaudi
author: clint
categories:
- Life
- OpenStack
tags:
- communication
- openstack
- summit
- barcelona
- architecture
---
[Antoni Gaudi](https://en.wikipedia.org/wiki/Antoni_Gaud%C3%AD)
designed one of the most beautiful things I have ever seen in my life,
the [Casa Batlló](https://en.wikipedia.org/wiki/Casa_Batll%C3%B3)
in Barcelona. 
![Casa Batlló](/images/Casa-Batllo-Barcelona.jpg)

While touring the site, the audio tour guide explained multiple times
that this entire site, from the basement to the roof, had no written
detailed plans. Gaudi had to supervise every aspect of the construction,
so that it was exactly the perfect masterpiece it is today. Gaudi is
truly a legendary human being, and one of the greatest architectural
minds in history. This means that he produced masterpieces, but it also
means they can never be duplicated, are nearly impossible to improve,
and are even quite difficult to maintain.


And it is now, while I'm stuffed into "The giant metal tube"
(Thanks [Robyn](https://twitter.com/robynbergeron)), that I'm
enjoying a rare moment of very clear thought after an [OpenStack
Summit](https://www.openstack.org/summit/barcelona-2016/) related
to "God's Architect".

The most important session that I attended, and led,
was [a fishbowl to discuss the Architecture Working Group](https://etherpad.openstack.org/p/BCN-architecture-wg).
Even with [mailing list threads](http://lists.openstack.org/pipermail/openstack-dev/2016-June/097657.html),
[review cycles](https://review.openstack.org/#/c/335141/),
[etherpads](https://etherpad.openstack.org/p/architecture-working-group),
and [meetings](https://wiki.openstack.org/wiki/Meetings/Arch-WG)
behind us, it was clear from the discussion that there was some broad
misunderstanding of what we were doing and why we want it to be a part
of the community. We definitely used the time well and I think scraped
away some of the boilerplate "we're a team here we are" boring stuff
and dug down to what it is we want to do.

In a nutshell, we're here to look at the Nova, Neutron, Oslo,
et. al masterpieces, and write down the plans that were never created
before. While there are change specs, and manuals for much of it, quite
a bit has no binding theory of operation. As a result, there is quite a
strong cargo cult inside OpenStack, leading to forward progress without
understanding. This creates an OpenStack where there are more people
writing code than can understand code, which complicates every aspect
of developing and even operating it.

We want to make sure that OpenStack can continue moving forward, and so,
we need to write down how things work now, record the current theory of
operation, and then collaborate on improvements to those theories and
the actual implementations.

Without the Architecture Working Group, I'm sure OpenStack will remain
valuable and even be maintainable. However, I'd like to see it continue
to evolve and thrive even faster, and I'm proud to be working with people
to try and provide a safe place to make that happen.
