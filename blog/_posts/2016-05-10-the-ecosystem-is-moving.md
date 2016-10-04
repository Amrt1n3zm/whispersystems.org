---
title: "Blog >> Reflections: The ecosystem is moving"
layout: post
author: moxie0
---

*At Open Whisper Systems, we've been developing open source "consumer-facing" software for
the past four years.  We want to share some of the things we've learned while doing it.*

As a software developer, I envy writers, musicians, and filmmakers.  Unlike software, when
they create something, it is really done &mdash; forever.  A recorded album can be just the same 20 years
later, but software has to change.

Software exists as part of an ecosystem, and **the ecosystem is moving**.  The platform changes
out from under it, the networks evolve, security threats and countermeasures are in constant shift,
and the collective UX language rarely sits still.  As more money, time, and focus has gone into the
ecosystem, the faster the whole thing has begun to travel.

All of this means that the set of expectations users have for social and communication features
are evolving rapidly. Anyone building software today knows that it is not possible to stand still.

XXXXX

One of the controversial things we did with Signal early on was to build it as an unfederated
service. Nothing about any of the protocols we've developed requires centralization; it's entirely possible to
build a federated Signal Protocol based messenger, but I no longer believe that it is possible to build a
*competitive* federated messenger at all.

## Stuck in time

In some circles, this has not been a popular opinion.  When someone recently asked me about federating
an unrelated communication platform into the Signal network, I told them that I thought we'd be unlikely
to ever federate with clients and servers we don't control.  Their retort was "that's dumb, how far would
 the internet have gotten without interoperable protocols defined by 3rd parties?"

I thought about it.  We got to the first production version of IP, and have been trying for the past
20 years to switch to a second production version of IP with limited success.  We got to HTTP version 1.1 in 1997, and
have been stuck there until now.  Likewise, SMTP, IRC, DNS, XMPP, are all similarly frozen in time circa the
late 1990s.  To answer his question, that's how far the internet got.  It got to the late 90s.

That has taken us pretty far, but it's undeniable that once you federate your protocol, it becomes very
difficult to make changes.  And right now, at the application level, things that stand still don't fare
very well in a world where **the ecosystem is moving**.

Indeed, cannibalizing a federated application-layer
protocol into a centralized service is almost a sure recipe for a successful consumer product today. It's
what Slack did with IRC, what Facebook did with email, and what WhatsApp has done with XMPP.  In each
case, the federated service is stuck in time, while the centralized service is able to iterate into the
modern world and beyond.

<!--
HTTP is actually moving again, but arguably only because the web experience has centralized so much around Google.
Google already had the top two most popular websites in the world, so once Google Chrome also became the most
popular web client, it was easy for them to develop a new communication protocol of their own, which
everyone else has more or less begrudgingly agreed to call HTTP/2 and deploy as well.  This has also only been
possible because HTTP clients don't interact with each-other, only with server.
-->

So while it's nice that I'm able to host my own email, that's also the reason why my email isn't
end to end encrypted, and probably never will be.  By contrast, WhatsApp was able to introduce end to end encryption
to over a billion users with a single software update.  So long as federation means stasis while centralization means
movement, federated protocols are going to have trouble existing in a software climate that demands
movement as it does today.

Early on, I thought we'd federate Signal once its velocity had subsided.  Now I realize that things will probably
never slow down, and if anything the velocity of the entire landscape seems to be steadily increasing.

### Extensible federation

XMPP is an example of a federated protocol that advertises itself as a "living standard."  Despite
its capacity for protocol "extensions," however, it's undeniable that XMPP still largely resembles a synchronous
protocol with limited support for rich media, which can't realistically be deployed on mobile devices.
If XMPP is so extensible, why haven't those extensions quickly brought it up to speed with the modern
world?

Like any federated protocol, extensions don't mean much unless everyone applies them, and that's
an almost impossible task in a truly federated landscape.  What we have instead is a complicated morass of XEPs
that aren't consistently applied anywhere. The implications of that are severe, because someone's choice to use
an XMPP client or server that doesn't support video or some other arbitrary feature doesn't only effect them,
it effects everyone who tries to communicate with them. It creates a climate of uncertainty, never knowing
whether things will work or not. In the consumer space, fractured client support is often worse than no client
support at all, because consistency is incredibly important for creating a compelling user experience.

For example, even GitHub has problems with consistency and control right now.  They introduced
[issue templates](https://github.com/blog/2111-issue-and-pull-request-templates), but
a number of 3rd party GitHub clients don't support them, so even after creating a [thorough issue
template](https://github.com/WhisperSystems/Signal-Android/blob/master/.github/ISSUE_TEMPLATE.md)
for the Signal Android repository, we still get people who post "it doesn't work please help,"
because their client never even showed them the template.  That makes me annoyed with GitHub, even though
I use the official GitHub clients. It's a potential opportunity for a GitHub competitor that can
display issue templates consistently.

### Federation and meta-data

One potential benefit of federation is the ability to choose what provider gets access to your meta-data.
However, as someone who self-hosts my email, that has never felt particularly relevant, given that every email I send
or receive seems to have gmail on the other end of it anyway.  Federated services always seem to coalesce around
a provider that the bulk of people use, with a long tail of small scattered self-hosting across the internet.
That makes sense, because running a reliable service isn't easy, but it's an outcome that is sadly the worst
of both worlds.

If anything, protecting meta-data is going to require innovation in new protocols and software. Those changes
are only likely to be possible in centralized environments with more control, rather than less.  Just as
making the changes to consistently deploy end to end encryption in federated protocols like email has
proved difficult, we're more likely to see the emergence of enhanced metadata protection in centralized
environments with greater control.

### Federation and control

On some level, federation is appealing precisely because it *does* freeze protocols in time.  It's great when
centralized clients and servers roll out features that benefit us, but they could just as easily roll out
features that don't.  Federation gives us more collective control over what changes we accept, but that
comes with an unacceptable inability to adapt.

Given that federated services always seem to coalesce around a provider that the bulk of people use,
federation becomes a sort of implicit threat.  Nobody really wants to run their own servers, but they know
that it might be possible if their current host does something egregious enough to make it worth the effort.

However, over the past six years, we've also seen the user cost of switching between centralized communication services
reduced substantially, particularly given the tendency towards addressing with user-owned identifiers like phone numbers.
The device's [address book is now the social network](/blog/contact-discovery), so using phone numbers as an identifier
has reduced switching costs by putting a user's social network under their control.  In a way, the notification center
on a mobile device has become the federation point for all communication apps, similar to how older desktop IM clients
unified communication across multiple IM networks.

The effect has been visible in the messaging space, where market leaders have come and gone, new popular apps come out
of nowhere, and even the most successful players seem compelled to continue iterating and improving their services as
quickly as possible.

This reduced user friction has begun to extend the implicit threat that used to come with federated services into
centralized services as well.  Where as before you could switch hosts, or even decide to run your own server, now
users are simply switching entire networks.  In many cases that cost is now much lower than the federated switching cost
of changing your email address to use a different email provider.

An open source infrastructure for a centralized network now provides almost the same level of control as federated
protocols, without giving up the ability to adapt.  If a centralized provider with an open source infrastructure
ever makes horrible changes, those that disagree have the software they need to run their own alternative instead.
It may not be as beautiful as federation, but at this point it seems that it will have to do.