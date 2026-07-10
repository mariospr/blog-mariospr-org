---
title: 'Orca and WebKit2GTK+: initial results'
date: '2011-11-11T23:38:29+00:00'
slug: orca-and-webkit2gtk-initial-results
categories:
- a11y
- accessibility
- GNOME
- Planet GNOME
- Planet GPUL
- Planet Igalia
- Planeta GNOME Hispano
- WebKit
- WebKit2
- WebKitGTK
wp_id: 562
aliases:
- /2011/11/11/orca-and-webkit2gtk-first-results/
---

Last May, <a title="WebKit Contributors Meeting, sockets &amp; plugs" href="/2011/05/05/webkit-contributors-meeting-sockets-plugs/">I wrote about some initial tests I did back then</a> with <a title="AtkSocket" href="http://developer.gnome.org/atk/stable/atk-AtkSocket.html">AtkSocket</a> and <a title="AtkPlug" href="http://developer.gnome.org/atk/stable/atk-AtkPlug.html">AtkPlug</a>, just to learn a bit about that API that allows connecting accessibility trees in different processes, thanks to the magic of the <a title="AT-SPI2 ATK bridge" href="http://git.gnome.org/browse/at-spi2-atk">ATK bridge</a>. I did that in order to prepare for the work that would probably be needed when adding accessibility support in WebKit2GTK+, so browsers using the new version of this web engine could be at least as much accessible as those using the single-process <a title="WebKitGTK+" href="http://webkitgtk.org/">WebKitGTK+</a> library. Looking back, I think that the effort has definitely payed off...

However, because of one reason or another (<a title="The family keeps growing" href="/2011/01/09/the-family-keeps-growing/">and not necessarily work-related</a>), I was not able to devote much time to keep working on this until some weeks ago, but fortunately I'm now again working on this as my primary task in <a title="Igalia" href="http://www.igalia.com">Igalia</a>, as part of our <a title="Igalia's WebKit team" href="http://www.igalia.com/nc/work/project/item/webkitgtk/">WebKit team</a>, so I expect to have some nice results soon, hopefully also in the form of integrated patches upstream.

And talking about results, I can't avoid sharing the following at this very same moment, which is actually the trigger that made me write this post: today I was able to make <a title="ORCA" href="http://live.gnome.org/Orca">Orca</a> read, for the very first time, web content rendered through <a title="WebKit2 MiniBrowser for the GTK+ port running!" href="https://blogs.igalia.com/alex/2011/04/08/webkit2-minibrowser-for-the-gtk-port-running/">WebKit2GTK's MiniBrowser</a>, which has been not an easy task since the <a title="WebKit2" href="http://trac.webkit.org/wiki/WebKit2">multiprocess architecture of WebKit2</a> made it a little bit challenging, to say the least.

Of  course there's still much to do in this regard, so do not think of the current status of the task as it was nearly finished or anything... but still I thought it was a nice milestone to share with the world, and what a better way to do it than using a video for that. After all, <a title="ORCA" href="http://live.gnome.org/Orca">Orca</a>'s main job is about speaking, right?. So here it is:
<p style="text-align: center;"><a href="http://vimeo.com/31969760"><strong>Orca and WebKit2GTK+: initial results </strong><em>(in Vimeo)</em></a></p>
By the way, I'd like to make the most of this post by saying I'm really proud and happy to have <a title="Joanmarie Diggs" href="http://blog.grain-of-salt.com/">Joanmarie Diggs</a> aboard in <a title="Igalia" href="http://www.igalia.com">Igalia</a> for a few weeks now, who contributed <strong>a lot</strong> to making possible that I was writing this post today. Thanks , Joanie!
