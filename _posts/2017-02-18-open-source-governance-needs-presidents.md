---
layout: post
status: publish
published: true
title: Free and Open Source Leaders -- You need a President
author: clint
categories:
    - Technology
    - Open Source
    - OpenStack
    - CNCF
tags:
    - opensource
    - governance
    - openstack
    - cncf
---
Recently I was lucky enough to be invited to attend the [Linux Foundation
Open Source Leadership Summit][lfosls]. The event was stacked with many
of the people I consider mentors, friends, and definitely leaders in the
various Open Source and Free Software communities that I participate in.
 
I was able to observe the [CNCF][cncf] Technical Oversight Committee meeting
while there, and was impressed at the way they worked toward consensus where
possible. It reminded me of the [OpenStack Technical Committee][ostc] in its
make up of well spoken technical individuals who care about their users and
stand up for the technical excellence of their foundations' activities.

But it struck me (and several other attendees) that this consensus building
has limitations. [Adam Jacob][adamhjk] noted that Linus Torvalds had given
an interview on stage earlier in the day where he noted that most of his role
was to listen closely for a time to differing opinions, but then stop them
when it was clear there was no consensus, and select one that he felt was
technically excellent, and move on. Linus, being the founder of Linux and
the benevolent dictator of the project for its lifetime thus far, has earned
this moral authority.

However, unlike Linux, many of the modern foundation-fostered projects
lack an executive branch.  The structure we see for governance is
centered around ensuring corporations that want to sponsor and rely on
development have influence. Foundation members pay dues to get various
levels of board seats or corporate access to events and data. And this is
a good thing, as it keeps people like me paid to work in these communities.

However, I believe as technical contributors, we sometimes give
this too much sway in the actual governance of the community and the
projects. These foundation boards know that day to day decision making
should be left to those working in the project, and as such allow
committees like the [CNCF][cncf] TOC or the [OpenStack TC][ostc] full
agency over the technical aspects of the member projects.

I believe these committees operate as a legislative branch. They evaluate
conditions and regulate the projects accordingly, allocating budgets for
infrastructure and passing edicts to avoid chaos. Since they're not as
large as political legislative bodies like the US House of Representatives
& Senate, they can usually operate on a consensus basis, and not drive
everything to a contentious vote. By and large, these are as nimble as
a legislative body can be.

However, I believe we need an executive to be effective. At some point,
we need a single person to listen to the facts, entertain theories, and
then decide, and execute a plan. Some projects have natural single leaders
like this. Most, however, do not.

I believe we as engineers aren't generally good at being
like Linus. If you've spent any time in the corporate world you've had
an executive disagree with you and run you right over. When we get the
chance to distribute power evenly, we do it.

But I think that's a mistake. I think we should strive to have executives.
Not just organizers like the [OpenStack PTL][ptl], but more like the
[Debian Project Leader][dpl]. Empowered people with the responsibility
to serve as a visionary and keep the project's decision making relevant
and of high quality. This would also give the board somebody to interact
with directly so that they do not have to try and convince the whole
community to move in a particular direction to wield influence. In this
way, I believe we'd end up with a system of checks and balances similar
to the US Constitution

![Checks and Balances](/images/usgovt.jpg)

So here is my suggestion for how a project executive structure could work,
assuming there is already a strong technical committee and a well defined
voting electorate that I call the "active technical contributors".

1. The president is elected by [Condorcet][condorcet] vote of the active technical
   contributors of a project for a term of 1 year.

2. The president will have veto power over any proposed change to the project's
   technical assets.

3. The technical committee may override the president's veto by a super
   majority vote.

4. The president will inform the technical contributors of their plans for
   the project every 6 months.

This system only works if the project contributors expect their project
president to actively drive the vision of the project. Basically, the
culture has to turn to this executive for final decision making before
it comes to a veto. The veto is for times when the community makes poor
decisions. And this doesn't replace leaders of individual teams. Think
of these like the governors of states in the US. They're running their
sub-project inside the parameters set down by the technical committee
and the president.

And in the case of foundations or communities with boards, I believe
ultimately a board would serve as the judicial branch, checking the
legality of changes made against the by-laws of the group. If there's no
board of sorts, a judiciary could be appointed and confirmed, similar to
the US supreme court or the [Debian CTTE][ctte]. This would also just
be necessary to ensure that the technical arm of a project doesn't get
the foundation into legal trouble of any kind, which is already what
foundation boards tend to do.

I'd love to hear your thoughts on this on Twitter, please tweet
me [@SpamapS][tw] with the hashtag #OpenSourcePresident to get the
discussion going.

[lfosls]: http://events.linuxfoundation.org/events/open-source-leadership-summit
[cncf]: https://www.cncf.io/
[ostc]: https://www.openstack.org/foundation/tech-committee/
[adamhjk]: https://twitter.com/adamhjk
[ptl]: https://docs.openstack.org/project-team-guide/ptl.html
[tw]: https://twitter.com/spamaps
[condorcet]: https://en.wikipedia.org/wiki/Condorcet_method
[dpl]: https://www.debian.org/devel/leader
[ctte]: https://www.debian.org/devel/tech-ctte
