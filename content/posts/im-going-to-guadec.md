---
title: I'm going to GUADEC!
date: '2013-07-12T19:06:22+00:00'
slug: im-going-to-guadec
categories:
- a11y
- accessibility
- Epiphany
- GNOME
- Meetings and conferences
- Planet GNOME
- Planet GPUL
- Planet WebKitGTK
- Planeta GNOME Hispano
- WebKit
- WebKit2
- WebKitGTK
wp_id: 1559
---

<a href="/2013/07/12/im-going-to-guadec/guadec2013/" rel="attachment wp-att-1560"><img class="alignright size-full wp-image-1560" alt="I'm attending GUADEC" src="/wp-content/uploads/2013/07/guadec2013.png" width="125" height="125" /></a>One year again <a title="GUADEC" href="http://www.guadec.org">GUADEC</a> is approaching and, also again, I'm very happy to say that I'll be there as well this time, even if I have to recognize it was not on my plans for this year, at least not initially.

And the reason why it was not initially in my plans was mainly because I've been already through quite <a title="Moving on" href="/2012/11/19/moving-on/">some</a> <a title="My first week at SERI" href="/2013/01/12/my-first-week-at-seri/">changes</a> during these past months year, and my family just came over to the <a title="United Kingdom" href="http://en.wikipedia.org/wiki/United_Kingdom">UK</a> two months ago. This means that, even I already arrived by the beginning of the year, we just started to settle here as a family a few weeks ago. So in that context, I didn't feel like leaving them alone for one week already now, it definitely would look like a "wrong management of priorities" to me.

However, it turns out that my wife and kids won't be here anyway during the first week of August and, on top of that, <a title="Samsung" href="http://www.samsung.com">Samsung</a> has been so kind to sponsor this trip just based on the simple fact that I'm part of the <a title="The GNOME Project" href="http://www.gnome.org">GNOME</a> community. So, I certainly can no longer find a single reason not to go and spend 7 amazing days in <a title="Brno, Czech Republic" href="http://en.wikipedia.org/wiki/Brno">Brno</a>, meeting people that I normally see only in conferences (and this time that group of people will be bigger than ever, since my former mates from <a title="Igalia" href="http://www.igalia.com">Igalia</a> are now also included there), while attending to what it seems to be <a title="GUADEC Schedule" href="https://www.guadec.org/schedule/">a very appealing event</a>.

Also, I will try to make the most of the trip to do some work during the different hackfests and <a title="GUADEC BoFs" href="https://wiki.gnome.org/GUADEC/2013/BOFs">BoFs that are already planned</a>, which special focus in the one about <a title="Computer accessibility" href="http://en.wikipedia.org/wiki/Computer_accessibility">accessibility</a>, of course. As a personal goal, I expect to have the chance to move forward some work I've been doing lately in the <a title="WebKitGTK+" href="http://www.webkitgtk.org">WebKitGTK+</a> a11y world, such as <a title="[GTK] Metabug: Get rid of Pango/Gail dependencies in accessibility for ATK" href="https://bugs.webkit.org/show_bug.cgi?id=114867">getting rid of the nasty dependency</a> on <a title="Pango" href="https://git.gnome.org/browse/pango">Pango</a>/<a title="GTK+ Accessibility Implementation Layer" href="https://git.gnome.org/browse/libgail-gnome/">Gail</a> we still have there, something I've been already working on for some time now, and which I expect it will be fixed soon, hopefully before <a title="GUADEC" href="http://www.guadec.org">GUADEC</a>, although time will tell.

Once that it's fixed, <a title="WebKit2GTK+" href="http://webkitgtk.org/reference/webkit2gtk/unstable/index.html">WebKit2GTK+</a> based apps should recover the ability to properly expose text through the <a title="AtkText interface" href="https://developer.gnome.org/atk/unstable/AtkText.html"><em>atk_text_get_text_*_offset()</em></a> family of functions for different <a title="AtkText boundaries" href="https://developer.gnome.org/atk/unstable/AtkText.html#AtkTextBoundary">text boundaries</a>, which means that <em><a href="http://en.wikipedia.org/wiki/Assistive_technology" rel="nofollow">ATs</a></em> (e.g. the <a href="https://live.gnome.org/Orca" rel="nofollow">Orca</a> screen reader)  will be able to properly allow again line-by-line navigation when in caret browsing mode. And, as you can imagine, this is quite a big problem these days, since <a title="WebKit2GTK+" href="http://webkitgtk.org/reference/webkit2gtk/unstable/index.html">WebKit2GTK+</a> that has become the default backend for some core apps such as the <a title="The Epiphany Browser" href="https://projects.gnome.org/epiphany/">Epiphany browser</a> with the <a title="The GNOME Project" href="http://www.gnome.org">GNOME</a> <a title="GNOME 3.8 release notes" href="https://help.gnome.org/misc/release-notes/3.8/">3.8 release</a>, so fixing this is like a high priority now, I'd say.

<a href="/2013/07/12/im-going-to-guadec/logo/" rel="attachment wp-att-1567"><img class="alignright size-full wp-image-1567" alt="Samsung Logo" src="/wp-content/uploads/2013/07/logo.png" width="106" height="35" /></a>Anyway, I'm starting to write too much (as usual) for what it was going to be a short "I'm going to <a title="GUADEC" href="http://www.guadec.org">GUADEC</a>" blog post, so I will stop right now, although not without first thanking <a title="Samsung" href="http://www.samsung.com">Samsung</a> for sponsoring this my first trip to the <a title="Czech Republic" href="http://en.wikipedia.org/wiki/Czech_Republic">Czech Republic</a>.

See you all in three weeks!
