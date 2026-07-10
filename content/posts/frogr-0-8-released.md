---
title: Frogr 0.8 released
date: '2012-12-29T20:15:49+00:00'
slug: frogr-0-8-released
categories:
- Debian
- Fedora
- frogr
- GNOME
- Planet GNOME
- Planet GPUL
- Planeta GNOME Hispano
- Ubuntu
wp_id: 1239
---

During the last weeks, I decided to make the most of some spare time I had while still in "nowhere land" (see <a title="Moving On" href="/2012/11/19/moving-on/">my previous post</a>) and so I've been working in <a title="frogr website" href="https://live.gnome.org/Frogr">frogr</a> to see if I could release the 0.8 version before the end of the year. In my mind it looked like kind of a nice and humble Christmas present to the world and, at the same time, a interesting way to spent this time I had between my depart from <a title="Igalia" href="http://www.igalia.com">my previous job</a> and the start of the new one.

And it turns out that, at the end, I didn't manage to have as much spare time as I initially expected to have (I was pretty busy most of the time, actually), mainly due to many unrelated things I needed also to take care of, but in the end I still managed to steal some minutes here and there and I'm now proudly announcing that <a title="Announcement mail for frogr 0.8" href="https://mail.gnome.org/archives/frogr-list/2012-December/msg00002.html">the new release is finally out</a>.

But before going on, see the mandatory screenshot, as taken in my <a title="Fedora project" href="http://fedoraproject.org/">Fedora</a> 18 machine:
<a href="/2012/12/29/frogr-0-8-released/20121226-frogr-screenshot-2/" rel="attachment wp-att-1257"><img class="aligncenter size-large wp-image-1257" title="Frogr 0.8" src="/wp-content/uploads/2012/12/20121226-frogr-screenshot1-600x375.png" alt="" width="584" height="365" /></a>

As you can already spot in the screenshot, some changes are already quite visible, but some others are not, so let's now comment on the most important ones, one by one...
<h3>Ported to GtkApplication and GMenu</h3>
<a href="/2012/12/29/frogr-0-8-released/20121226-frogr-menus/" rel="attachment wp-att-1261"><img class="aligncenter size-large wp-image-1261" title="Frogr 0.8: Ported to GMenu" src="/wp-content/uploads/2012/12/20121226-frogr-menus-600x145.png" alt="" width="584" height="141" /></a>

It's no secret that one of my favourite changes in this release is the integration with <a title="GNOME 3" href="http://www.gnome.org/gnome-3/">GNOME 3</a>'s "global menu" (aka the <em>application menu</em>), which makes <a title="frogr website" href="https://live.gnome.org/Frogr">frogr</a> more beatifully integrated with the desktop than ever. However that came with a price: I needed to port <a title="frogr website" href="https://live.gnome.org/Frogr">frogr</a> to <a title="GtkApplication" href="http://developer.gnome.org/gtk3/3.4/GtkApplication.html">GtkApplication</a> first and then implement both the application menu and the menu bar using <a title="GMenu" href="http://developer.gnome.org/gio/2.32/GMenu.html">GMenu</a>, which also made me raise the required version for <a title="GTK+" href="http://www.gtk.org">GTK+</a> up to 3.4.

Sure I could have kept adding more <em>ifdefs</em> to the code to keep supporting previous <a title="GTK+" href="http://www.gtk.org">GTK+</a> versions, but I also saw this as a good opportunity to clean up the code and get rid of so many conditional compilation units that were increasingly harder to maintain, and so I did it. As a plus, the <a title="OS X" href="http://en.wikipedia.org/wiki/OS_X">OS X</a> specific code has been reduced enormously as well, since <a title="GTK+" href="http://www.gtk.org">GTK+</a> 3.4 integrates very well with <a title="OS X" href="http://en.wikipedia.org/wiki/OS_X">OS X</a> without having to do anything special, as I needed to do when I used <a title="GTK+" href="http://www.gtk.org">GTK+</a> 2.24 for that port.
<h3>Loading and saving 'projects'</h3>
<a href="/2012/12/29/frogr-0-8-released/20121226-frogr-projects/" rel="attachment wp-att-1262"><img class="aligncenter size-large wp-image-1262" title="Frogr 0.8: Support for projects" src="/wp-content/uploads/2012/12/20121226-frogr-projects-600x145.png" alt="" width="584" height="141" /></a>

This has been one of the features that several people have suggested in the past in different occasions, and so one of those I hope people will enjoy the most with this new release: the possibility to save the current session into a "project file", so you can resume your work later.

How it works it's actually pretty simple: when you save a session to a project, <a title="frogr website" href="https://live.gnome.org/Frogr">frogr</a> will just serialize your current pictures, sets, groups and local tags to a json file (using <a title="json-glib" href="https://live.gnome.org/JsonGlib/"><em>json-glib</em></a>) that you can use to restore the state later. It could be more sophisticated, but I think that it works reasonably well in the tests I did considering what it was designed for. In any case, please feel free to report bugs or feature requests to improve or fix things if needed.
<h3>Support for video uploads</h3>
<a href="/2012/12/29/frogr-0-8-released/20121226-frogr-videos/" rel="attachment wp-att-1263"><img class="aligncenter size-large wp-image-1263" title="Frogr 0.8: support for video uploads" src="/wp-content/uploads/2012/12/20121226-frogr-videos-600x145.png" alt="" width="584" height="141" /></a>

Believe it or not, <a title="frogr website" href="https://live.gnome.org/Frogr">frogr</a> has been <em>almost</em> ready to upload videos since some time ago, since for <a title="Flickr" href="http://www.flickr.com">Flickr</a> a video is just a "moving picture", and it's <a title="Videos in the flickr API" href="http://code.flickr.net/2008/05/01/videos-in-the-flickr-api/">treated in exactly the same way than pictures</a> when it comes to the <a title="Flickr's upload API" href="http://www.flickr.com/services/api/upload.api.html">upload API</a>.

The only thing that was missing to remove that <em>almost</em> from here was to generate thumbnails for videos so they could get loaded into the UI. Not rocket science, sure, but something which needed doing and which was not a priority at all until now. And to be honest, it is not a priority yet anyway, but I felt like doing it this time once and for all, so from now on you can upload videos too.
<h3>Other features &amp; bug fixes</h3>
Besides those three and perhaps more noticeable features, <a title="frogr website" href="https://live.gnome.org/Frogr">frogr</a> 0.8 comes with several other new things, bug fixes, small changes and refinement that I hope will make this release more stable, useful and fun to use than ever.

<a href="/2012/12/29/frogr-0-8-released/20121226-frogr-maximized/" rel="attachment wp-att-1264"><img class="aligncenter size-large wp-image-1264" title="Frogr 0.8: hide title bar when maximized" src="/wp-content/uploads/2012/12/20121226-frogr-maximized-600x145.png" alt="" width="584" height="141" /></a>

Some examples of those other new things are, as taken from <a title="Frogr's NEWS file" href="http://git.gnome.org/browse/frogr/plain/NEWS">the NEWS file</a>:
<ul>
	<li>Handle and report errors in a better way (no more mysterious failures).</li>
	<li>Perform after-upload operations (add to sets/groups, set license...) in parallel.</li>
	<li>Avoid fetching sets/groups/tags when still not connected yet to <a title="Flickr" href="http://www.flickr.com">Flickr</a>.</li>
	<li>Hide title bar when main window is maximized (see screenshot above).</li>
	<li>Renamed the 'Actions' menu to 'Edit' and brought the 'File' menu back.</li>
	<li>Allow sorting elements in the icon view by size.</li>
</ul>
Last, I'm also quite happy to tell that the <a title="OS X" href="http://en.wikipedia.org/wiki/OS_X">OS X</a> port of <a title="frogr website" href="https://live.gnome.org/Frogr">frogr</a> has been finally migrated to <a title="GTK+" href="http://www.gtk.org">GTK+</a> 3 in this release (at last!), <strong>and</strong> that the whole process of building it for that platform is now easier than ever, thanks to a specific <a title="Jhbuild" href="https://live.gnome.org/Jhbuild">Jhbuild</a> <a title="Frogr's moduleset for OS X" href="http://git.gnome.org/browse/frogr/plain/osx/jhbuild/frogr.modules">moduleset I created for that purpose</a>, following <a title="GEdit's moduleset for OS X" href="http://git.gnome.org/browse/gedit/plain/osx/jhbuild/gedit.modules">the lead of GEdit</a> (thanks <a title="Nacho's blog" href="http://blogs.gnome.org/nacho/">Nacho</a> for the suggestion).

Check out the <a title="README file to build frogr for OS X" href="http://git.gnome.org/browse/frogr/plain/osx/README">README</a> file in the <a title="osx/ directory" href="http://git.gnome.org/browse/frogr/tree/osx">osx/ directory</a> if you feel curious about the process or if you want to build it yourself. It shouldn't take more than 2-3 commands in the terminal to get something like this running in your <a title="OS X" href="http://en.wikipedia.org/wiki/OS_X">OS X</a> machine:

<a href="/2012/12/29/frogr-0-8-released/20121226-frogr-screenshot-osx/" rel="attachment wp-att-1255"><img class="aligncenter size-large wp-image-1255" title="Frogr 0.8 for Mac OS X" src="/wp-content/uploads/2012/12/20121226-frogr-screenshot-osx-600x375.png" alt="" width="584" height="365" /></a>

Also, another advantage of having that moduleset created, is that now it's trivial to properly document (by means of <a title="generate-SOURCES script" href="http://git.gnome.org/browse/frogr/plain/osx/generate-SOURCES">a shell script</a>) the bundle file used to distribute <a title="frogr website" href="https://live.gnome.org/Frogr">frogr</a> in <a title="OS X" href="http://en.wikipedia.org/wiki/OS_X">OS X</a>, instead of just providing an "opaque" pre-compiled bundle, as I used to do in an "unofficial way" with previous versions. Feel free to <strong>grab the bundle</strong> I've just created for this release <a title="Frogr 0.8 for Mac OS X" href="http://ftp.gnome.org/pub/gnome/binaries/mac/frogr/0.8/">from the GNOME FTP server</a>.

So that's it. I hope you enjoy using <a title="frogr website" href="https://live.gnome.org/Frogr">frogr</a> 0.8 as much as I did writing it, and if you eventually find it useful too, then even better! As usual, check <a title="Frogr's website" href="https://live.gnome.org/Frogr">the website of the project</a> for additional information or just to know <a title="Get frogr" href="https://live.gnome.org/Frogr#Get_Frogr">how to install frogr on your system</a>.
