---
title: 'WebKitGTK+ Hackfest: WK2, a11y and Ephiphany''s ad blocker extension'
date: '2011-12-06T00:01:06+00:00'
slug: webkitgtk-hackfest-wk2-a11y-and-ephiphanys-ad-blocker
categories:
- a11y
- accessibility
- Epiphany
- GNOME
- Hackfest
- Planet GNOME
- Planet GPUL
- Planet Igalia
- Planeta GNOME Hispano
- WebKit
- WebKit2
- WebKitGTK
wp_id: 607
aliases:
- /2011/12/06/webkitgtk-hackfest-wk2-a11y-and-ephy/
---

<a title="WebKitGTK+ Hackfest: Day 2" href="http://www.hadess.net/2011/12/webkitgtk-hackfest-day-2.html">Some</a> <a title="WebKitGTK+ Hackfest: Day 3" href="http://www.hadess.net/2011/12/webkitgtk-hackfest-day-3.html">posts</a> <a title="WebKitGTK+ Hackfest: Day 4" href="http://www.hadess.net/2011/12/webkitgtk-hackfest-day-4.html">have</a> <a title="WebKitGTK+ Hackfest: Day 5" href="http://www.hadess.net/2011/12/webkitgtk-hackfest-day-5.html">been</a> <a title="Announcing the WebKitGTK+ hackfest 2011" href="https://blogs.igalia.com/juanjo/2011/11/17/announcing-the-webkitgtk-hackfest-2011/">already</a> <a title="Open web apps and device APIs" href="https://blogs.igalia.com/juanjo/2011/12/03/open-web-apps-and-device-apis/">published</a> <a title="A new design for Epiphany: Web" href="http://blogs.gnome.org/xan/2011/12/04/a-new-design-for-epiphany-web/">about</a> <a title="webkittens! lexical scoping is in danger!" href="http://wingolog.org/archives/2011/12/02/webkittens-lexical-scoping-is-in-danger">this</a> during the last days, but just in case you missed them I will mention it here again: Last week, a bunch of hackers gathered together in the <a title="Igalia" href="http://www.igalia.com">Igalia</a> office in <a title="A Coruña" href="http://en.wikipedia.org/wiki/A_Coru%C3%B1a">Coruña</a> for the <a title="WebKitGTK+ Hackfest 2011" href="https://live.gnome.org/Hackfests/WebKitGTK2011">third edition of the WebKitGTK+ hackfest</a> , and a lot of work has been done, as <a title="Juanjo's blog" href="https://blogs.igalia.com/juanjo">Juanjo</a> has already summarized in <a title="WebKitGTK+ hackfest wrap up" href="https://blogs.igalia.com/juanjo/2011/12/04/webkitgtk-hackfest-wrap-up/">his "WebKitGTK+ hackfest wrap up" post</a>.

<a title="WebKitGTK+ 2011 Hackfest by mariosp, on Flickr" href="http://www.flickr.com/photos/mariosp/6429995845/"><img src="https://farm8.staticflickr.com/7143/6429995845_975e314fff.jpg" alt="WebKitGTK+ 2011 Hackfest" width="500" height="333" /></a>

So, as everything has been already said from a more general perspective, I'd like to write my very personal wrap up here, focused on the tasks that I've been working on, which can be summarized in three:
<ul>
	<li>Enabling accessibility support in <a title="WebKit2" href="http://trac.webkit.org/wiki/WebKit2">WebKit2GTK+</a>.</li>
	<li>Rewrite of the Ad Blocker extension for <a title="Epiphany browser" href="http://www.gnome.org/projects/epiphany">Epiphany</a>.</li>
	<li>Bug fixing in <a title="WebKitGTK+" href="http://www.webkitgtk.org/">WebKitGTK+</a>'s accessibility related code.</li>
</ul>
<h3>Enabling accessibility support in WebKit2GTK+</h3>
This has been, by far, the task I devoted most of the time to during the hackfest, mainly focused on writing a 'feature complete' patch that could be applied upstream, and thus that could be reviewed in first place. But, what do I mean by "a 'feature complete' patch"? Well, perhaps you are already aware of the <a title="Orca and WebKit2GTK+: initial results" href="/2011/11/11/orca-and-webkit2gtk-initial-results/">initial results already got in the WebKit2GTK+ a11y realm</a>, but those results were obtained with a patch still in a very early state and, among other things, lacking a very important requirement for getting it accepted upstream: <strong>tests</strong>.

Fortunately, I can now proudly say that I managed to find a good way to write those tests (specially tricky due to the multiprocess architecture of <a title="WebKit2" href="http://trac.webkit.org/wiki/WebKit2">WebKit2</a>) and that there shouldn't be any problem either with getting them work properly in the <a title="WebKit's build bots" href="http://build.webkit.org">buildbots</a>, which was something I was quite concerned about by the begining of the week, to be honest.

Besides the tests, the other obvious problem was that such a patch was not widely tested yet with the <a title="Orca screen reader" href="http://live.gnome.org/Orca">Orca screen reader</a> (I use <a title="Accerciser" href="https://live.gnome.org/Accerciser">Accerciser</a> for development purposes most of the time), and that would for sure unveil issues that would need fixing before being really able to propose a patch for reviewing, and so that was the other aspect where I put the spotlight during this week.

And regarding to this, I have to say that<a title="Joanmarie Diggs's blog" href="http://blog.grain-of-salt.com/"> Joanmarie Diggs</a> was working tirelessly by testing <a title="Orca screen reader" href="http://live.gnome.org/Orca">Orca</a> with my WebKit2GTK+ a11y patch, reporting bugs, and helping me a lot to prioritize the tasks that would need to be done. From all those, I mainly worked this week in the following ones:
<ul>
	<li><strong>Emitting the AtkDocument's signals</strong> ('load-complete', 'load-stopped' and 'reload'), which was working only in <a title="WebKitGTK+" href="http://www.webkitgtk.org/">WebKitGTK+</a> but not in WebKit2GTK+. See the bug report and the patch (still pending on review) for this issue in <a title="Move emissions of AtkDocument signals down to WebCore" href="https://bugs.webkit.org/show_bug.cgi?id=73750">bug 73750</a>. Also, I reported and worked for a while in another bug related to this, which is now already fixed upstream (see <a title="WebKit Bug 73746" href="https://bugs.webkit.org/show_bug.cgi?id=73746">bug 73746</a>). Yay!</li>
	<li><strong>Ensure that the accessibility hierarchy doesn't break when (re)loading</strong>, which was causing that <a title="Orca screen reader" href="http://live.gnome.org/Orca">Orca</a> stopped speaking unless it "manually" drilled down the full a11y hierarchy after the (re)load. I finally fixed that issue yesterday and integrated it in the patch for enabling a11y support in WebKit2GTK+, now already attached and pending on review along with <a title="Bug 72589" href="https://bugs.webkit.org/show_bug.cgi?id=72589">bug 72589</a>.</li>
</ul>
So, the conclusion of this part would be that we have now a patch in <a title="WebKit bugzilla" href="http://bugs.webkit.org">WebKit's bugzilla</a> (see <a title="Bug 72589" href="https://bugs.webkit.org/show_bug.cgi?id=72589">bug 72589</a>) that, once it's approved, would enable accessibility in WebKit2GTK+ once and for all. Of course, this will probably take some time before it gets accepted upstream, but it's yet another nice milestone in my opinion, and I personally hope it would happen on time for <a title="The GNOME project" href="http://www.gnome.org">GNOME</a> 3.4. Time will tell, though.
<h3>Rewrite of the Ad Blocker extension for Epiphany</h3>
This was another thing I've been randomly working on since some time ago (whenever "spare" time permitted), and that I was able to advance quite a lot right after coming back from the parental leave I enjoyed on September (did I say my second child was born on August the 30th?). However, the patch was not finished by any means, and some issues kindly pointed by <a title="Xan's blog" href="http://blogs.gnome.org/xan">Xan</a> in <a href="https://bugzilla.gnome.org/show_bug.cgi?id=660154">bugzilla</a> needed fixing before being able to say aloud something like "hey, the new ad blocker is now in town!".

Thus, we thought it would be good to devote some time during the hackfest to try to close this task too, so we did: <a title="Xan's blog" href="http://blogs.gnome.org/xan">Xan</a> reviewed the new version of the patch (addressing the issues he previously pointed out), I made some last changes based on that new feedback from him and we finally pushed it to the repository, replacing the old ad blocker extension with this new one, which is based in <a title="Midori browser" href="http://www.twotoasts.de/index.php?/pages/midori_summary.html">Midori</a>'s ad blocker and so is compatible with <a title="Adblock Plus" href="http://adblockplus.org">Adblock Plus</a> filt﻿ers, which work very well IMHO.

So, this basically means that the new ad blocker extension will be present from <a title="Epiphany browser" href="http://www.gnome.org/projects/epiphany">Epiphany</a> 3.4 on. Check out the related bug in <a title="The GNOME project" href="http://www.gnome.org">GNOME</a>'s bugzilla: <a href="https://bugzilla.gnome.org/show_bug.cgi?id=660154">bug 660154</a>
<h3>Bug fixing in WebKitGTK+'s accessibility related code</h3>
Besides working in the WebKit2GTK+ a11y realm and on finishing the new ad blocker extension, I've also spent some time (although not as much as I would have wanted) fixing regressions in <a title="WebKitGTK+" href="http://www.webkitgtk.org/">WebKitGTK+</a>'s a11y code as reported by <a title="Joanmarie Diggs's blog" href="http://blog.grain-of-salt.com/">Joanie</a> (basically <a href="https://bugs.webkit.org/show_bug.cgi?id=72804">bug 72804</a> and <a href="https://bugs.webkit.org/show_bug.cgi?id=72830">bug 72830</a>).

Compared to the other two points, this has been of course a pretty small contribution, but worth doing anyway since they were very important for <a title="Orca screen reader" href="http://live.gnome.org/Orca">Orca</a> to work properly with <a title="WebKitGTK+" href="http://www.webkitgtk.org/">WebKitGTK+</a> based browsers (special mention to <a href="https://bugs.webkit.org/show_bug.cgi?id=72830">bug 72830</a> here).
<h3>Conclusion</h3>
From the work-related point of view, I'd say this hackfest has been highly productive in general, as we achieved many goals which, as <a title="Juanjo's wrap up" href="https://blogs.igalia.com/juanjo/2011/12/04/webkitgtk-hackfest-wrap-up/">Juanjo pointed out in his wrap up post</a>, "were not mainly about fixing critical and blocker bugs and implementing basic missing features, but about more ambitious and challenging" ones. As for me, I'm pretty happy with the results I got, specially with the WK2 a11y patch, which has now a much better shape, and so I hope we can integrate it soon upstream.

And from a more personal point of view, I'd like to say I had a great time (again!) this year in the hackfest, and not only because of the achiements got, but also because I had quite a lot of fun as well, because I met new people and because I felt, more than ever, part of a community and a project which I love.

To finish, I'd just like to mention that I've been taking some pictures during the hackfest, which you can check out in this <a title="WebKitGTK+ 2011 Hackfest, by me" href="http://www.flickr.com/photos/mariosp/sets/72157628217381055/">photo set in flickr</a> (pictures uploaded with <a title="Frogr site at live.gnome.org" href="live.gnome.org/Frogr">Frogr</a>, of course!). <a title="Nayan's twitter profile" href="https://twitter.com/#!/xc0ffee">Nayan</a> has also taken some pictures as well, <a title="WebKit Gtk Hackfest 2011, by Nayan" href="http://www.flickr.com/photos/59474880@N00/sets/72157628245413107/">check them out here</a>.

<a title="WebKitGTK+ 2011 Hackfest (The End) by mariosp, on Flickr" href="http://www.flickr.com/photos/mariosp/6461606065/"><img src="https://farm8.staticflickr.com/7141/6461606065_fb0f0bbf76.jpg" alt="WebKitGTK+ 2011 Hackfest (The End)" width="500" height="333" /></a>

Of course, thanks a lot to the sponsors that made this possible: <a title="Collabora" href="http://www.collabora.co.uk/">Collabora</a>, <a title="Motorola" href="http://www.motorola.com">Motorola</a>, <a title="Igalia" href="http://www.igalia.com">Igalia</a> and the always awesome <a title="The GNOME Foundation" href="http://foundation.gnome.org/">GNOME Foundation</a>. I hope we'll be able to repeat it next year, since this hackfest it's only getting more and more awesome every time it happens.
