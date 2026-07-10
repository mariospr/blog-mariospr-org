---
title: WebKitGTK+ hackfest 2010
date: '2010-12-13T14:57:18+00:00'
slug: webkitgtk-hackfest-2010
categories:
- a11y
- accessibility
- Epiphany
- GNOME
- Hackfest
- Meetings and conferences
- Planet GNOME
- Planet GPUL
- Planet Igalia
- Planet Maemo
- Planeta GNOME Hispano
- WebKit
- WebKitGTK
wp_id: 311
---

After <a title="http://blogs.gnome.org/diegoe/2010/12/05/webkitgtk-hackfest-day-0/" href="http://blogs.gnome.org/diegoe/2010/12/05/webkitgtk-hackfest-day-0/">the</a> <a title="WebKitGTK+ hackfest, day 1" href="http://blogs.gnome.org/diegoe/2010/12/06/webkitgtk-hackfest-day-1/">daily</a> <a title="WebKitGTK+ hackfest, day 2" href="http://blogs.gnome.org/diegoe/2010/12/07/webkitgtk-hackfest-day-2/">reports</a> <a title="http://blogs.gnome.org/diegoe/2010/12/08/3rd-day-of-vebkitgtk-hackfest-live-from-the-cave/" href="http://blogs.gnome.org/diegoe/2010/12/08/3rd-day-of-vebkitgtk-hackfest-live-from-the-cave/">written</a> <a title="WebKitGTK+ hackfest, day 400" href="http://blogs.gnome.org/diegoe/2010/12/09/webkitgtk-hackfest-day-400/">by</a> <a title="http://blogs.gnome.org/diegoe/2010/12/10/webkitgtk-hackfest-day-5/" href="http://blogs.gnome.org/diegoe/2010/12/10/webkitgtk-hackfest-day-5/">Diego</a> in <a href="http://blogs.gnome.org/diegoe/">his blog</a>, few more things can be told about the <a title="WebKitGTK hackfest" href="http://live.gnome.org/Hackfests/WebKitGTK2010">WebKitGTK+ hackfest</a> hosted at the <a title="Igalia" href="http://www.igalia.com">Igalia</a> offices last week, but I'd like to comment anyway some impressions from my personal point of view, if you don't mind reading them.

First of all, this was the second time I attended to this hackfest (I "kind of" attended <a title="WebKitGTK+ Coruña Hackfest 2009" href="http://live.gnome.org/WebKitGtk/Hackfest2009">last year hackfest</a> as well) but now things were pretty different for me, basically because one year ago I was not part of the <a title="Igalia" href="http://www.igalia.com">Igalia</a> <a title="WebKit" href="http://webkit.org">WebKit</a> team yet, hence my contributions in the hackfest were pretty small (see <a title="WebKitGTK+ Hackfest is over (2009)" href="/2009/12/21/webkitgtk-hackfest-is-over/">my post back then</a> for more details). However, this time I attended full-time to the event and I must say I'm really proud of the work I've been doing right there, which I hope will eventually lead to the resolution of <a title="[GTK] Metabug: Bugs blocking Orca support" href="https://bugs.webkit.org/show_bug.cgi?id=25531">this WebKit metabug</a>, which was about fixing bugs blocking <a title="ORCA" href="http://live.gnome.org/Orca">ORCA</a> support from <a title="WebKitGTK" href="http://webkitgtk.org">WebKitGTK</a> based applications.

But fortunately, the work I've been doing during the last week was just a pretty small and humble contribution compared to all the work that has been done by the rest of the people attending to the hackfest, like fixing GTK3 and GObject Introspection issues, fully integrating in libsoup all the new cache stuff written for <a title="WebKitGTK" href="http://webkitgtk.org">WebKitGTK</a> (which eventually lead to removing the equivalent code from WebKitGTK, as <a title="WebKitGtk+ HTTP cache ready!" href="https://blogs.igalia.com/svillar/2010/10/20/webkitgtk-http-cache-ready/">my mate Sergio told some weeks ago</a>, as soon as some bots upgrade to the latest version of libsoup), adding support for profiling in JavascriptCore, implementing some missing and advanced features into the DumRenderTree (aka <em>DRT</em>, the so beloved tool for writing functional tests), fixing spell-checking support... and bugfixing in general (as well as, most likely, lots of other things I'm failing to recall right now). You can read <a href="http://blogs.gnome.org/diegoe/">Diego's blog</a> for more details on those.

Other than that, there was also time for working in <a title="Epiphany: the GNOME browser" href="http://projects.gnome.org/epiphany/">Epiphany</a> were some notorious fixes and improvements also happened. Those I can remember right now are the new error pages for epiphany, the implementation of a certificates viewer and new font preferences, getting rid of <a title="GConf" href="http://projects.gnome.org/gconf/">GConf</a> in <em>epiphany-extensions </em>and general bugfixing tasks. As you can easily understand, as the devoted and committed Epiphany user that I am, I'm pretty excited with these improvements as well. Not needed to say anything about <a title="window-commands: hackfest mooded epiphany" href="http://git.gnome.org/browse/epiphany/commit/?id=5641c511a80969b910ba45897a2be3c411d40618">this patch committed at the beginning of the hackfest</a>, I guess, in my opinion this is one of those cases where a picture is clearly worth a thousand words:-)

<a href="/wp-content/uploads/2010/12/Screenshot-Hackfests-WebKitGTK2010-GNOME-Live.png"><img class="aligncenter size-medium wp-image-321" src="/wp-content/uploads/2010/12/Screenshot-Hackfests-WebKitGTK2010-GNOME-Live-300x244.png" alt="hackfest mooded epiphany" width="300" height="244" /></a>

So, as you can see it was a quite productive week after all here in <a title="Wikipedia: A Coruña" href="http://en.wikipedia.org/wiki/A_Coruña">Coruña</a>!

Last but not least, I'd like to specially thank <a title="The GNOME Foundation" href="http://foundation.gnome.org/">The GNOME Foundation</a> for sponsoring the event, as well as <a title="Igalia" href="http://www.igalia.com">Igalia</a> and <a title="Collabora" href="http://www.collabora.co.uk/">Collabora</a> for helping make this possible once again. Hope we can repeat it next year, and that more people will join the event to help making <a title="WebKitGTK" href="http://webkitgtk.org">WebKitGTK</a> an even better web engine for the <a title="The GNOME platfform" href="http://www.gnome.org">GNOME</a> platform.

See pictures of the hackfest here:
<ul>
	<li><a title="My flickr photostream" href="http://www.flickr.com/photos/mariosp/sets/72157625444570591">My flickr photostream</a></li>
	<li><a title="Joone's flickr photostream" href="http://www.flickr.com/photos/joone/sets/72157625444172107/">Joone's flickr photostream</a></li>
	<li><a title="Diego's 'webkitgtk' tagged pictures" href="http://www.flickr.com/photos/diegoe/tags/webkitgtk/">Diego's 'webkitgtk' tagged pictures</a></li>
</ul>
