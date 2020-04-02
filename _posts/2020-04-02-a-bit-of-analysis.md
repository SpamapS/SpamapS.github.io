---
layout: post
status: publish
published: true
title: A bit of deep analysis
author: clint
categories:
    - Debugging
tags:
    - terminals
    - unix
    - pick
    - joy
---
In case you missed it, [I'm on the job
market](https://www.linkedin.com/feed/update/urn:li:activity:6650805910325338112/).
As I've been winding through the various opportunities out there, I found a
company that wants a sample of "analysis" as part of their application.

I’ll be honest, I sat in front of this section for an hour without coming up
with anything. I wrote down some of the times I’d done deep analysis that I
could remember, but none of them really impress me. Now, you may be reading
this thinking “heh, yeah, cause this guy doesn’t know how to analyze”. But to
be honest, I think for me, this question is like asking [Greg
Maddux](https://en.wikipedia.org/wiki/Greg_Maddux) how he threw his best
fastball, or asking [Sir Mick
Jagger](https://en.wikipedia.org/wiki/Mick_Jagger) how he performed his best
chicken dance, or a great white shark how it ate its most fish. They could all
probably tell you more about doing taxes. They’re just being themselves, it’s
what makes them great.

Analyzing systems has always been very natural for me. I mean always. I was
that kid pulling apart the VCR to see what was inside, and then putting it back
together successfully.. sometimes. I truly do not remember what I did there, but
look ma, the whining noise is gone when we rewind!

So, that said, I’ll not give you the best analysis I’ve done, because I just
can’t pick one of the thousands. Instead, I’ll give you the very first one I
was paid for. A brief story.

The year is 1997, and the protagonist is a recent graduate of High School. For
the past 3 months, our hero has been employed doing his dream: playing with
computers. As a contrarian, this rare Linux-using teenager has decided to go
right in to the IT industry and skip that silly college thing (yes, this
teenager was as dumb as a teenager, and twice as stubborn).  And they even have
an HP-9000 *real* unix box to play with.

The developers are all perplexed, on this day however. The *literal green
screen* application that runs the entire company is crashing, randomly. All
hands on deck, the 4 developers are furiously examining code and records in the
database to find out what is causing this problem. Our hero loves code, and has
chatted with the devs a few times about what they do. This weird system they
work in is called “PickDB”, and the app is in “PickBASIC”, and it’s really
simple, so, Sir Paperbox-carrying PC-network-card-reseating 18 year old has
been peeking at the manual and playing on his own green-screen to learn it in
spare time.

Alas, the problem is vexing. This particular firm is a medical equipment
manufacturer, and billing agents are seeing, randomly, that some records they
pull up simply corrupt their entire screen view. The cursor flies around, weird
matrix-like (oh wait, there’s no Matrix yet) characters print, and generally
they have to have a server-side reset to continue (kill their shell, the
database vendor explains, and our hero already knew how to do that and showed
the devs so they could self-service).

Well the devs are fighting through it, so he sits down to peek at the database
as well. They have a list of records known to cause the problem, so he pulls
one up with the usual method: SELECT foo WHERE id = ‘999’ or something like
that, honestly, it wasn't SQL, but it was the SQL of PickDB. Behold! A perfect
record is printed, line by line. One by one, all of the records look pretty
normal, though you can see where the longer records had incomplete words.

The vigor of this young man will not be stopped though, and he wonders if he
just writes a program to print out the records, if it works differently. Writes
program, runs it, and there, in front of him, is a broken terminal.

So, he kills his session and tries turning the characters in to their ASCII
numbers. Oh noes, the program crashes HARD. What’s this then? The built-in
function that turns characters in to numbers has printed a runtime error and
halted his program. “High-bit char detected.”

Fast-forward to an hour later, where this 18 year old is explaining to these 40
year olds how to fix the problem. See, PickDB and PickBASIC don’t actually
exist anymore. It was originally run on IBM mini-computers, but those are
expensive, so some vendors had shown up to swoop in and replace it with cheaper
emulators that run on cheaper HP-9000’s. This was called “UniData”, and it
worked flawlessly.

However, when this company had converted from Pick to UniData, the vendor had
converted most of the data in some black-box process. But now, 4 years later,
the database was purged of most of those records, and everything in it was
newly entered in the green screens which were serially wired to a
serial-to-telnet gateway via CAT-3 cables wired into RS-232 connectors. So, one
day, 4 years ago, the vendor had arrived, taken the old IBM system out, and put
in the HP-9000, and taken all of those RS-232 patches out of the IBM MUX, and
put them into an HP terminal concentrator.

Meanwhile, over 4 years, the company had grown, and more and more green-screens
purchased and wired up in the same fashion. Reorgs shifted people around, and
terminal connections stayed where they were, with users just logging in to
wherever they sat.

And so, what had happened? Last week, a reorg had sent accounting into the
space used by medical bill processing, and vice-versa. This meant that records
were now being entered in the space that had been newly built out for
accounting 2 years earlier. Accounting didn’t do much data entry, but medical
billing was literally just taking doctors’ patients forms on paper, and
entering them into forms on green screen.  And so, for the past week, new
terminals had been used to enter all of the new records.

But the vendor had forgotten one thing. They forgot to tell the person who they
trained on how to wire new connections, to log in to the terminal concentrator,
and change it to use x-on/x-off 7-bit for green-screens. The default, was
CTS/CTR. The details of this dark and arcane protocol are lost to my brain as
it has been over 20 years, but basically, when people typed fast, the
concentrator would set a pin on the RS-232 to 1 instead of 0 to say “STOP
SENDING ME STUFF MAH BUFFER'S GONNA BURST”, but the terminal would keep sending
stuff, and when the pin went back to 0, the concentrator would start reading
again, and binary hilarity ensued.

This realization came about because our hero had been playing with serial
connections and modems since he was 12. He knew what CTS/CTR and x-on/x-off
were, sorta, and had read the manuals for both the green-screens and the
terminal concentrator while debugging this problem. Once the high-bit chars
error was seen, the real problem was unmasked. And it was a short process to go
make a well behaved terminal suddenly become a garbage-data-generator.

Funny enough, the SELECT program from UniData had a filter which would remove
high-bit chars, which is why it was so hard to find these nasty chars. Even
worse, this DB used the 8-bit int value of 253 to mean "field delimiter", and
254 as "record delimiter", so if you got REALLY unlucky, your keystrokes would
split a record or a field in two! The devs just hadn’t thought that the
built-in program would lie to them! By writing his own program, our hero had
satisfied the X-files rule of debugging: Trust No-one.  After reading the
manuals he had then applied the same principal to the terminal concentrator
configs: why trust one port over another?

In closing, this analysis also led to an amazing discovery that changed the
lives of the data-entry folks for a brief time. In reading the manual for the
port-concentrator, he discovered that the ports were all set to 19200bps, which
was ok, but that the port concentrator could actually go much, much faster if
it could use CTS/CTR. And all of the new terminals in the data-entry area were
WYSE-60+, not WYSE-50, which meant they actually could be configured for CTS/CTR
and the much higher data rate. As a result, screen paints were 10x faster on
these models, and soon they became coveted treasures in the company.

FIN
