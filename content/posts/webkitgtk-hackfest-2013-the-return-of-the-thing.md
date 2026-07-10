---
title: 'WebKitGTK+ Hackfest 2013: The Return of the Thing'
date: '2013-12-13T20:10:04+00:00'
slug: webkitgtk-hackfest-2013-the-return-of-the-thing
categories:
- a11y
- accessibility
- GNOME
- Hackfest
- Meetings and conferences
- Planet GNOME
- Planet GPUL
- Planet WebKitGTK
- Planeta GNOME Hispano
- WebKit
- WebKit2
- WebKitGTK
wp_id: 1674
---

<a href="/2013/12/13/webkitgtk-hackfest-2013-the-return-of-the-thing/webkitgtk-hackfest-2013/" rel="attachment wp-att-1684"><img class="alignright size-medium wp-image-1684" alt="The WebKitGTK+ Hackfest 2013" src="/wp-content/uploads/2013/12/webkitgtk-hackfest-2013-300x225.png" width="300" height="225" /></a>As many other <a title="The WebKitGTK+ project" href="http://webkitgtk.org">WebKitGTK+ </a>hackers (30 in total), I flew last Saturday to A Coruña to attend the <a title="The WebKitGTK+ Hackfest 2013" href="https://wiki.gnome.org/Hackfests/WebKitGTK2013">5th edition of the WebKitGTK+ Hackfest</a>, hosted once again by <a title="Igalia" href="http://www.igalia.com">Igalia</a> at their premises and where people from several different affiliations gathered together to try to give our beloved port a boost.

As for me, I flew there to work mainly on accessibility related issues, making the most of the fact that both <a title="Joanie's blog" href="http://blog.grain-of-salt.com/">Joanie</a> (<a title="Orca screen reader" href="http://live.gnome.org/Orca">Orca</a> maintainer) and <a title="API's blog" href="https://blogs.igalia.com/apinheiro/">Piñeiro</a> (<a title="ATK" href="https://developer.gnome.org/atk/unstable/">ATK</a> maintainer) would be there too, so it should be possible to make things happen faster, specially discussion-wise.

And turns out that, even if I feel like I could have achieved more than what I actually did (as usual), I believe we did quite well in the end: we discussed and clarified things that were blocking the mapping of new <a title="WAI-ARIA User Agent Implementation Guide" href="www.w3.org/TR/wai-aria-implementation">WAI-ARIA</a> roles in <a title="The WebKitGTK+ project" href="http://webkitgtk.org">WebKitGTK+</a>, we got rid of a bunch of WebKit1-specific unit tests (<a title="Joanie's blog" href="http://blog.grain-of-salt.com/">Joanie</a> converted them into nice layout tests that will be run by <a title="WebKit2GTK+" href="http://webkitgtk.org/reference/webkit2gtk/unstable/">WebKit2GTK+</a> too), we got a few new roles in <a title="ATK" href="https://developer.gnome.org/atk/unstable/">ATK</a> to be able to better map things from the web world and and we fixed a couple of issues in the way too.

Of course, not everything has been rainbows and unicorns, as it seems that one of the patches I landed broke the inspector for <a title="WebKit2GTK+" href="http://webkitgtk.org/reference/webkit2gtk/unstable/">WebKit2GTK+</a> (sorry <a title="Gustavo's blog" href="http://blog.kov.eti.br/">Gustavo</a>!). Fortunately, that one has been rolled out already and I hope I will be able to get back to it soon (next week?) to provide a better patch for that without causing any problem. Fingers crossed.

In the other hand, my mate Brian Holt joined us for three days too and, despite of being his first time in the hackfest, he got integrated pretty quickly with other hackers, teaming up to collaborate in the big boost that the <em>network process</em> &amp; <em>multiple web processes</em> items have went through during the event. And not only that, he also managed to give a boost to his last patch to provide automatic memory leak detection in <a title="The WebKitGTK+ project" href="http://webkitgtk.org">WebKitGTK+</a>, which I'm sure it will be a great tool once it's finished and integrated upstream.

Anyway, if you want more details on those topics, or anything else, please check out the blog posts that <a href="http://www.gnome.org/news/2013/12/webkitgtk-hackfest-underway-in-a-coruna/">other</a> <a href="https://people.gnome.org/~csaavedra/news-2013-12.html">hackers</a> <a href="http://blog.kov.eti.br/2013/12/webkitgtk-hackfest-5-0-2013/">have</a> <a href="http://base-art.net/Articles/124/">been</a> <a href="https://blogs.igalia.com/itoral/2013/12/11/webkitgtk-2013-hackfest-on-the-road-to-webkit2-wayland-support-in-webkitgtk/">posting</a> <a href="https://blogs.igalia.com/carlosgc/2013/12/12/webkitgtk-hackfest-2013-the-network-process/">these</a> <a href="http://kwangyulseo.wordpress.com/2013/12/13/webkitgtk-hackfest-2003/">days</a>, specially <a title="WebKitGTK+ Hackfest 2013, by Carlos Carcia Campos" href="https://blogs.igalia.com/carlosgc/2013/12/12/webkitgtk-hackfest-2013-the-network-process/">Carlos's blog post</a>, which is quite extensive and detailed.

<a href="/2013/07/12/im-going-to-guadec/logo/" rel="attachment wp-att-1567"><img class="alignright size-full wp-image-1567" alt="Samsung Logo" src="/wp-content/uploads/2013/07/logo.png" width="106" height="35" /></a>Of course, I would like to thank the main sponsors <a title="Igalia" href="http://www.igalia.com">Igalia</a> and the <a title="The GNOME project" href="http://www.gnome.org">GNOME</a> Foundation for making this thing happen again, and to my employer <a title="Samsung UK" href="http://www.samsung.com/uk">Samsung</a>  for helping as well by paying our trips and accommodation, as well as the snacks and the coffee that helped us stay alive and get fatter during the hackfest.

Last, I would like to mention (in case anyone reading this wondered) that it has indeed felt a bit strange to go the city where I used to live in and stay in a hotel, not to mention going to the office where I used to work in and hang around it as a visitor. However, both my former city and my former colleagues somehow ensured that I felt as "at home" once again, and so I can't do anything about it but feeling enormously grateful for that.

Thank you all, and see you next year!
