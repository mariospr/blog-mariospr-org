---
title: Frogr 0.9 released
date: '2014-01-17T15:29:50+00:00'
slug: frogr-0-9-released
categories:
- Debian
- Fedora
- frogr
- GNOME
- Planet GNOME
- Planet GPUL
- Planeta GNOME Hispano
wp_id: 1702
---

So, after a bit more than one year without releasing any version of <a title="Frogr web site" href="https://wiki.gnome.org/Apps/Frogr">frogr</a>, I finally managed to get some "spare" time to put all the pieces together and ship the ninth version of it, which I believe/hope is going to be a quite solid one.

<a href="/2014/01/17/frogr-0-9-released/20140117-frogr-screenshot/" rel="attachment wp-att-1705"><img class="aligncenter size-large wp-image-1705" alt="Frogr 0.9" src="/wp-content/uploads/2014/01/20140117-frogr-screenshot-600x375.png" width="584" height="365" /></a>

In all honesty, though, this version does not come with many new features as the previous ones, yet some changes and fixes that I believe were quite necessary, and therefore should help improving the user experience in some subtle ways.

For instance, the layout of the dialog to edit the details of a picture has changed (as per <a title="Ana Rey on Twitter" href="https://twitter.com/anaRB">Ana Rey</a>'s comments during <a title="GUADEC" href="http://www.guadec.org">GUADEC</a>) to enable a more efficient usage of vertical space, so much needed these days in small widescreen laptops. Of course, design-wise still sucks, but I believe it's much more convenient now from a pragmatical point of view.

Also, frogr is now a little bit more "modern" in things such as that it now supports GStreamer 1.0 (0.10 still supported), a lot of deprecated code (e.g. Stock items, GtkActions) has been replaced internally and it now integrates better with <a title="GNOME" href="http://www.gnome.org">GNOME</a> Shell's search box. Ah! and it also now provides an <a href="http://people.freedesktop.org/~hughsient/appdata/">AppData</a> file to integrate with <a title="GNOME Software Center" href="http://blogs.gnome.org/hughsie/2013/08/29/gnome-software-center-and-you/">GNOME Software Center</a>, which is a nice touch too.

Another interesting thing is that I finally fixed the problem that we have with multiple selections in the main view, which was neither intuitive nor very useful, as Ctrl and Shift modifiers did not work as expected. So, from now on, it is finally possible to work with disjoint multiple selections of pictures, a feature I was missing so much.

Last, I fixed two important problems in the code that caused frogr consume two much memory, specially after uploading pictures. It was a quite severe problem since frogr was not properly freeing the memory used by pictures even after those were uploaded and removed from the UI, causing important issues in cases where people tried to upload a lot of pictures at once. It's hopefully fixed now.

And that's all I think. As usual, you can check <a title="Frogr's website" href="https://live.gnome.org/Frogr">the website of the project</a> to know <a title="Get frogr" href="https://live.gnome.org/Frogr#Get_Frogr">how to install frogr on your system</a> if you don't want to wait for your favourite distribution to ship it, or if you just want to check more information about the project or to contribute to it.

<img class="alignright size-full wp-image-1709" alt="FOSDEM 2014" src="/wp-content/uploads/2014/01/fosdem-logo.png" width="165" height="33" />

Ah! By the way... I'm going to <a title="FOSDEM" href="http://www.fosdem.org">FOSDEM</a> again this year, but this time <a href="http://en.wikipedia.org/wiki/Eurostar">by train</a>. Can't wait to be there! :)
