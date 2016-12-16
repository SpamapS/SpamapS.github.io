---
layout: post
status: publish
published: true
title: OpenStack's nova-compute's border is porous - We need to build a wall
author: clint
categories:
- OpenStack
tags:
- openstack
- architecture
- nova
- neutron
- cinder
- microservices
---
In the beginning there was Nova. It included volumes, networking,
hypervisors, and scheduling.  Since then, Nova components have either
been replaced (nova-network with Neutron) or forklifted out and enhanced
(Cinder). In so doing, interfaces were defined for how Nova would
continue to make use of these now-external services, but nova-compute,
the place where the proverbial rubber meets the road, was left inside
Nova. This meant that agents for Cinder and Neutron had to interact with
nova-compute through the high level message bus, despite being right
on the same physical machine in many (but not all) cases. Likewise,
some cases take advantage of that, and require operator cooperation in
configuring for certain drivers.


This has led to implementation details leaking all over the API's that
these services use to interact. Neutron and Nova do a sort of haphazard
dance to plug ports in, and Cinder has drivers which require locking files
on the local filesystem a certain way. These implementation details are
leaking into public API's because it turns out nova-compute is actually
a shared service that should not belong to any of the three services,
and which should define a more clear API which Nova, Cinder, and Neutron,
should be able to use to access the physical resources of machines from
an equal footing.

[We're starting a discussion in the OpenStack Architecture Working Group](https://review.openstack.org/#/c/411527/)
around whether this is creating real problems, and how we can address it.

What I think we need to do is build a wall around nova-compute, so we can
accurately define what goes in or out, and what belongs specifically in
nova-compute's code base. That way we can accept the things that should
live and work permanently inside its borders vs. what should come in
through an API port of entry and declare its intentions there.

But before we can build that wall, we need nova-compute to declare its
independence from Nova.  That may be as much a social challenge as a
technical one. However, I think once we complete some analysis, and
provide a path toward a more sustainable compute service, we'll end up
with a more efficient, less error-prone, more optimizable OpenStack.

If you're interested in this, I recommend you come to the next IRC
meeting for the [Architecture WG](https://wiki.openstack.org/wiki/Meetings/Arch-WG)
, on January 12, 2017.
