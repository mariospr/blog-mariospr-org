---
title: Wrapping up the GNOME a11y hackfest
date: '2010-10-13T21:43:30+00:00'
slug: wrapping-up-the-gnome-a11y-hackfest
categories:
- a11y
- accessibility
- GNOME
- Meetings and conferences
- Planet GNOME
- Planet GPUL
- Planet Igalia
- Planeta GNOME Hispano
- WebKit
- WebKitGTK
wp_id: 268
---

As I told in <a title="&quot;Attending to the GNOME a11y hackfest&quot; post" href="/2010/09/27/attending-to-the-gnome-a11y-hackfest/">my previous post</a>, I've spent the last week in Seville attending ﻿﻿﻿the <a title="GNOME Accessibility Hackfest" href="http://live.gnome.org/Accessibility/HackfestAEGIS2010">GNOME Accessibility Hackfest</a>, which was an amazing experience to me, so I guess now it's time to talk about some (mostly personal and subjective) conclusions.

First of all, let's repeat this was the first time I attended an a11y related hackfest, and from that point of view the experience was even better and more rewarding than what I'd expected. Meeting other a11y developers in real life and putting faces to them, along with being able to check the real needs that people demand from assistive technologies was an awesome experience, and way richer than just having a list of bugs in need of getting fixed.

Up to this point, I can say that one of the best things I extracted from the hackfest is that I've learned, with real-life living examples, why implementing certain kind of stuff in the <a title="WebKitGTK website" href="http://webkitgtk.org/">WebKitGTK</a> port is so important for people with diverse kind of impairements, and even learned to prioritize and value different a11y related issues so I could make the most of my work to be more effective when helping, with my humble 2 cents in my daily work, to make the next release of <a title="The GNOME project" href="http://www.gnome.org">GNOME</a> a good one also from the point of view of accessibility. Obviously, there's still a long road ahead to keep learning and improving, but I think this is a good achievement anyway, if you ask me.

Other than that, together with <a title="Joanmarie Diggs' blog" href="http://blog.grain-of-salt.com/">Joanmarie Diggs</a>, we managed to move some important things forward related to the integration of <a title="WebKitGTK website" href="http://webkitgtk.org/">WebKitGTK</a> based applications and the <a title="The ORCA project" href="http://live.gnome.org/Orca">ORCA</a> screen reader, so now the <em>"ORCA experience"</em> with the web is clearly better compared to how it was some months ago (or at least that's what Joanmarie says, and I trust her). In this regard, I feel specially proud of the advancements we've been doing with the implementation of the <a title="AtkHypertext documentation" href="http://library.gnome.org/devel/atk/unstable/AtkHypertext.html">AtkHypertext</a>/<a title="AtkHyperlink" href="http://library.gnome.org/devel/atk/unstable/AtkHyperlink.html">AtkHyperlink</a> related stuff, which makes the experience of "screen reading" a web page way better and more complete than how it would be without that feature. And I mention this stuff here, because that's precisely what I've been working on most of the time during the hackfest and  because, even though it's <a title="Patch for the AtkHypertext and AtkHyperlink stuff in WebKitGTK" href="https://bugs.webkit.org/show_bug.cgi?id=33785">still a provisional patch</a> pending on some final tweaks to be proposed for review, I hope it will be soon integrated in <a title="WebKitGTK website" href="http://webkitgtk.org/">WebKitGTK</a>.... (you know, 'hope' is a so beautiful word... but I feel somehow confident with this stuff, "let's hope I'm right" :-)).

So, as you can see I have reasons to be very happy about the results of the hackfest, even if we all were somehow jinxed because one reason or another, and the overall result of all this stuff is that I clearly felt a boost in my motivation to keep working on this stuff and to keep helping to improve the overall status of the accessibility from my beloved <a title="WebKit website" href="http://webkit.org/">WebKit</a> world... which is not that bad, IMHO.

<a href="/wp-content/uploads/2010/10/64670_437917296020_610601020_5752200_6981586_n.jpg"><img class="alignright size-thumbnail wp-image-278" src="/wp-content/uploads/2010/10/64670_437917296020_610601020_5752200_6981586_n-150x150.jpg" alt="My birthday cake coming from the GNOME a11y team, by Juanje Ojeda" width="150" height="150" /></a>Last but not least, I have to say there was room as well for having a lot of fun (<a title="Jack, from the movie &quot;The Shinning&quot;" href="http://2.bp.blogspot.com/_AaFtdasP2WQ/R1I7BR687rI/AAAAAAAAAGg/w1zqdm9iV6A/s1600-R/The_shining_heres_johnny.jpg">"A</a><em><a title="Jack, from the movie &quot;The Shinning&quot;" href="http://2.bp.blogspot.com/_AaFtdasP2WQ/R1I7BR687rI/AAAAAAAAAGg/w1zqdm9iV6A/s1600-R/The_shining_heres_johnny.jpg">ll work and no play makes Jack a dull boy"</a>) </em>with my mates from the <a title="GNOME Accessibility" href="http://projects.gnome.org/accessibility/">GNOME accessibility team</a>, who even had prepared a surprise for me in the shape of a cake to celebrate my birthday (see the picture below, by <a title="Juanje Ojeda's blog" href="http://blogs.gnome.org/juanje/">Juanje Ojeda</a>).

Thank you guys! It was a really really nice experience! Let's repeat it soon in the future... but as for now, let's get back to work!
