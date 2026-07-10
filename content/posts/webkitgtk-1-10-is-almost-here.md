---
title: WebKitGTK+ 1.10 is almost here!
date: '2012-09-14T17:38:27+00:00'
slug: webkitgtk-1-10-is-almost-here
categories:
- Epiphany
- GNOME
- Planet GNOME
- Planet GPUL
- Planet Igalia
- Planet WebKitGTK
- Planeta GNOME Hispano
- WebKit
- WebKit2
- WebKitGTK
wp_id: 1063
---

As you might already know, the new and shiny 3.6 release of the <a title="The GNOME project" href="http://www.gnome.org">GNOME</a> desktop is <a title="GNOME 3.5.x development series" href="https://live.gnome.org/ThreePointFive">right around the corner</a>, and so it's the next release of <a title="WebKitGTK+" href="http://wwww.webkitgtk.org">WebKitGTK+</a>, the port of the <a title="The WebKit project" href="http://www.webkit.org">WebKit</a> web rendering engine to the <a title="The GTK+ platform" href="http://www.gtk.org">GTK+</a> platform.

And it turns out that such a release is going to be a very special one for us, members of the <a title="Igalia WebKit team" href="http://www.igalia.com/webkit/">WebKit team</a> at <a title="Igalia" href="http://www.igalia.com">Igalia</a>,  since it comes with some very interesting features, like those I already mentioned in the <a title="WebKitGTK+: current status and roadmap" href="/talks/guadec2012-webkitgtk">talk I gave during the past GUADEC</a>, mainly:
<ul>
	<li>Beta version of the <strong><em>WebKit2GTK+ API</em></strong></li>
	<li>Support for <em><strong>Accelerated Compositing</strong></em></li>
	<li><em><strong>WebGL</strong></em> enabled by default</li>
	<li>Support for <strong>HTML5</strong> Fullscreen and <strong>WebAudio</strong></li>
	<li>Multimedia layer ported to <strong>GStreamer 0.11</strong></li>
	<li>Support for the <strong>Low-Level Interpreter</strong> in JavaScriptCore</li>
</ul>
From all those, I'm specially happy because we will be finally releasing the very first beta version of the new <strong><em>WebKit2GTK+ API</em></strong>, based in the multi-process architecture of <a title="WebKit2" href="http://trac.webkit.org/wiki/WebKit2">WebKit2</a>, as well as providing support for <strong><em>Accelerated Compositing</em></strong> and <strong><em>WebGL</em></strong>.

This new <em><a title="WebKit2GTK+ API" href="http://webkitgtk.org/reference/webkit2gtk/unstable/index.html">WebKit2GTK+ API</a></em>, as you perhaps already know, will allow applications gain the split process model of <a title="WebKit2" href="http://trac.webkit.org/wiki/WebKit2">WebKit2</a> out-of-the box, which is awesome. Xan already mentioned  some of the advantages of it becoming beta for <a title="The GNOME project" href="http://www.gnome.org">GNOME</a> 3.6 <a title="We are almost there: Web in 3.6.0" href="http://blogs.gnome.org/xan/2012/09/11/we-are-almost-there-web-in-3-6-0/">in his last post this week</a>, being my favorite ones the "<em>increased responsiveness and stability</em>" (quoting <a title="We are almost there: Web in 3.6.0" href="http://blogs.gnome.org/xan/2012/09/11/we-are-almost-there-web-in-3-6-0/">Xan</a>) that will come with it, as well as the fact that it will be not only powerful enough to port old applications and write new ones, but also simpler and easier to use (we are putting a lot of effort on <a title="WebKit2GTK+ Roadmap" href="http://trac.webkit.org/wiki/WebKitGTK/WebKit2Roadmap">this</a>).

And honestly, I think we are doing pretty well in that regard, even though there's still a lot of work to do before we can release an stable version of this new API (due for <a title="WebKitGTK+" href="http://wwww.webkitgtk.org">WebKitGTK+</a> 2.0,  to be released with <a title="The GNOME project" href="http://www.gnome.org">GNOME</a> 3.8), which will also mean the very first version of <a title="Epiphany and WebKit2" href="https://blogs.igalia.com/carlosgc/2012/07/02/epiphany-and-webkit2/">Epiphany that will be using WebKit2 by default</a>.

With regard to <em>Accelerated Compositing </em>and <em>WebGL</em>, I'd just like to mention that having them supported in <a title="WebKitGTK+" href="http://wwww.webkitgtk.org">WebKitGTK+</a> from now on is great because it means you will be able to render visually stunning web content in your browser of choice (epiphany, huh?), as well as enjoy more subtle improvements such as smoother animations or increased responsivenes while browsing. You can visit this <a title="Accelerated compositing update" href="http://blog.abandonedwig.info/2012/07/accelerated-compositing-update.html">post by my mate Martin</a> for more details on this topic.

Anyway, all these are very nice words and all that, but sometimes it's not that easy to properly understand <em>just with words</em> what exactly those <em>things</em> will actually mean for users, so I decided to spend some time today polishing a bit the videos I used as demos in my talk during <a title="GUADEC!" href="http://www.guadec.org">GUADEC</a>, and link them from here, so everyone can easily watch them now.

Hope you enjoy watching them as much as I did making them:
<p style="text-align: center;"><iframe src="https://player.vimeo.com/video/49440927" frameborder="0" width="500" height="280"></iframe></p>
<p style="text-align: center;"><a href="http://vimeo.com/49440927">WebKitGTK+: WebGL and Accelerated Compositing</a></p>
<p style="text-align: center;"><iframe src="https://player.vimeo.com/video/49443843" frameborder="0" width="500" height="281"></iframe></p>
<p style="text-align: center;"><a href="http://vimeo.com/49443843">WebKit2GTK+: The UI and the Web process</a></p>
<p style="text-align: center;"><iframe src="https://player.vimeo.com/video/49446048" frameborder="0" width="500" height="281"></iframe></p>
<p style="text-align: center;"><a href="http://vimeo.com/49446048">WebKit2GTK+: The Plugin process</a></p>
