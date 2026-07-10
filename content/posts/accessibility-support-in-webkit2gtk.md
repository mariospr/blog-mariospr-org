---
title: Accessibility support in WebKit2GTK+
date: '2012-01-27T16:06:34+00:00'
slug: accessibility-support-in-webkit2gtk
categories:
- a11y
- accessibility
- Epiphany
- GNOME
- Hackfest
- Planet GNOME
- Planet GPUL
- Planet Igalia
- Planet WebKitGTK
- Planeta GNOME Hispano
- WebKit
- WebKit2
- WebKitGTK
wp_id: 684
---

As <a title="API's blog" href="https://blogs.igalia.com/apinheiro">Piñeiro</a> already mentioned <a title="Do you want to hear some news about GNOME and accessibility?" href="https://blogs.igalia.com/apinheiro/2011/12/23/do-you-want-to-hear-some-news-about-gnome-and-accessibility/">in</a> <a title="ATK/AT-SPI2 Hackfest 2012: Day 1" href="https://blogs.igalia.com/apinheiro/2012/01/19/atkat-spi2-hackfest-2012-day-1">some</a> <a title="ATK/AT-SPI2 Hackfest 2012: Days 2,3,4,5" href="https://blogs.igalia.com/apinheiro/2012/01/24/atkat-spi2-hackfest-2012-days-2345">posts</a>, last week a bunch of hackers attended the <a title="ATK/AT-SPI Hackfest 2012" href="https://live.gnome.org/Accessibility/Hackfests/ATK2012">ATK/AT-SPI Hackfest 2012</a> here at the <a title="Igalia" href="http://www.igalia.com">Igalia</a> offices, in the lovely city of <a title="Coruña" href="http://en.wikipedia.org/wiki/A_Coru%C3%B1a">Coruña</a>.

As the guy working on accessibility support for <a title="WebKitGTK+" href="http://www.webkitgtk.org">WebKitGTK+</a>, I attended the hackfest to join some other great people representing different projects, such as <a title="Alex Surkov's blog" href="http://asurkov.blogspot.com/">Mozilla</a>, <a title="Joanmarie Diggs's blog" href="http://blog.grain-of-salt.com/">Orca</a>, <a title="Mike Gorse's blog" href="http://lightvortex.livejournal.com/">AT-SPI</a>, <a title="API's blog" href="https://blogs.igalia.com/apinheiro">ATK</a>, <a title="Benjamin Otte's blog" href="http://blogs.gnome.org/otte/">GTK+</a> and <a title="Frederik Gladhorn's blog" href="http://blogs.fsfe.org/gladhorn/">Qt</a>. So, apart from helping with some "local" organizational details of the hackfest and taking <a title="Pictures of the ATK/AT-SPI Hackfest 2012" href="http://www.flickr.com/photos/mariosp/sets/72157628951274383/">some pictures</a>, I spent some time hacking in <a title="WebKitGTK+" href="http://www.webkitgtk.org">WebKitGTK+</a>'s accessibility code and participating in some discussions.

And from that dedication I managed to achieve some interesting things too, being my favorite ones a <a title="WebKitGTK's a11y code in WebCore" href="http://svn.webkit.org/repository/webkit/trunk/Source/WebCore/accessibility/gtk/">big refactoring of the a11y code in WebCore</a> (so it's now better organized and hence more readable and easy to hack on) and pushing my <a title="Patch for enabling a11y support in WebKit2GTK+" href="http://trac.webkit.org/changeset/105503">patch for enabling accessibility support in WebKit2GTK+</a>, after going through a meticulous process of review (see <a title="WebKit bug: [GTK] Expose accessibility hierarchy in WebKit2 to ATK/AT-SPI based ATs" href="https://bugs.webkit.org/show_bug.cgi?id=72589">the related WK bug</a>), which started with the patch I wrote and attached back when attending to the <a title="WebKitGTK+ Hackfest 2011" href="https://live.gnome.org/Hackfests/WebKitGTK2011">WebKitGTK+ hackfest</a>, as I mentioned in <a title="Blog post: WebKitGTK+ Hackfest: WK2, a11y and Ephiphany’s ad blocker extension" href="/2011/12/06/webkitgtk-hackfest-wk2-a11y-and-ephiphanys-ad-blocker/">my previous entry in this blog</a>.

Yeah, I know that some weeks have already passed since then and so perhaps you're thinking this could have been done faster... but I've spent some weeks on holidays in <a title="Barcelona" href="http://en.wikipedia.org/wiki/Barcelona">Barcelona</a> in December (<a title="Pictures or my last holidays in Barcelona" href="http://www.flickr.com/photos/mariosp/sets/72157628502724051">pictures here</a>!) and so I wouldn't have much time before January to devote to this task. However, the patch got integrated faster than what I would expect when I proposed the first version of it, so I'm quite satisfied and happy anyway just by being able to announce this at this moment. Hope you share my joy :-)

So, what does this mean from the point of view of accessibility in <a title="The GNOME project" href="http://www.gnome.org">GNOME</a>? Well, that's an easy question to answer: from now on, every browser that uses WebKit2GTK+ will be as much accessible as those using the previous version of <a title="WebKitGTK+" href="http://www.webkitgtk.org">WebKitGTK+</a>, and this is definitely a good thing. Of course, I'm certain there will be bugs in this specific part that will need fixing (as it always happens), but for the time being this achievement means "yet another thing less" preventing us from pushing for upgrading some applications to switch to WebKit2GTK+, such as <a title="Devhelp" href="http://live.gnome.org/devhelp">devhelp</a> (some ongoing work already done, as <a title="Blog post: Porting devhelp to WebKit2" href="https://blogs.igalia.com/carlosgc/2012/01/26/porting-devhelp-to-webkit2/">my mate Carlos announced yesterday</a>), <a href="http://projects.gnome.org/yelp/">yelp</a>, <a href="http://liferea.sourceforge.net/">liferea</a>... and the mighty <a title="Epiphany browser" href="http://projects.gnome.org/epiphany/">Epiphany browser</a>, which is <a title="Blog post: Epiphany marches on" href="http://blogs.gnome.org/xan/2012/01/17/epiphany-marches-on/">rocking more and more ech day</a> that goes by.

Last, I'd like to share with you an screenshot showing this new stuff, but as I am a little bit tired of always using <a title="Minibrowser" href="https://blogs.igalia.com/carlosgc/2011/11/04/webkit2-gtk-minibrowser-ported-to-gtk-api/">Minibrowser</a> (that small browser we use for testing <a title="WebKit2" href="http://trac.webkit.org/wiki/WebKit2">WebKit2</a>), so I decided to try instead that new branch Carlos recently pushed for <a title="Devhelp" href="http://live.gnome.org/devhelp">devhelp</a>, so you could check that what I mentioned before is actually true.

So here you have it (along with a couple of additions done with <a title="Gimp" href="http://www.gimp.org/">Gimp</a>):

<a href="/wp-content/uploads/2012/01/20120127-devhelp-wk2-a11y.png"><img src="/wp-content/uploads/2012/01/20120127-devhelp-wk2-a11y-thumb.png" alt="" width="500" height="312" /></a>

As you can see, <a title="Devhelp" href="http://live.gnome.org/devhelp">devhelp</a> is running and <a title="Accerciser" href="http://live.gnome.org/Accerciser">Accerciser</a> is showing the full hierarchy of accessible objects associated to the application, starting in the <em>UI process</em> (<a title="Benjamin Otte's blog" href="http://blogs.gnome.org/otte/">GTK+</a> <em>world</em>) and continuing in the <em>Web process</em>, where all the accessible objects from the <a title="WebKitGTK+" href="http://www.webkitgtk.org">WebKitGTK+</a> world are being exposed. As <a title="Blog post: WebKit Contributors Meeting, sockets &amp; plugs" href="/2011/05/05/webkit-contributors-meeting-sockets-plugs/">I explained in a previous post</a>, the magic making possible the connection between the two process is done by means of the <a title="AtkSocket documentation" href="http://developer.gnome.org/atk/unstable/atk-AtkSocket.html"><em>AtkSocket</em></a> and the <a title="AtkPlug" href="http://developer.gnome.org/atk/unstable/atk-AtkPlug.html"><em>AtkPlug</em></a> classes, also represented in the screenshot attached above.

So, that's it.
