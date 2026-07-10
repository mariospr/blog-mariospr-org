---
title: Frogr 0.3 released (hello, flicksoup!)
date: '2010-12-24T17:17:34+00:00'
slug: frogr-0-3-released-hello-flicksoup
categories:
- Debian
- Fedora
- frogr
- GNOME
- Planet GNOME
- Planet GPUL
- Planet Igalia
- Planeta GNOME Hispano
- Ubuntu
wp_id: 338
---

After more than one year without writing almost anything related to my other pet project "<a title="frogr project's website" href="http://code.google.com/p/frogr/">frogr</a>", I finally found some time, motivation and energy to put all the loose parts I already had more or less in place together and evolve them towards what finally made a new release of this -yet another- <a title="The GNOME project" href="http://www.gnome.org">GNOME</a> <a title="flickr image sharing website" href="http://www.flickr.com">flickr</a> uploader.

<a href="/wp-content/uploads/2010/12/frogr-0_3-screenshot.png"><img class="aligncenter" src="/wp-content/uploads/2010/12/frogr-0_3-screenshot-thumb.png" alt="" width="459" height="350" /></a>

That way, I finally released frogr 0.3 two days ago (see the <a title="Announcement for frogr 0.3 release" href="http://mail.gnome.org/archives/gnome-announce-list/2010-December/msg00045.html">announcement here</a>), featuring the following changes:
<ul>
	<li><strong>Replaced <a title="flickcurl library" href="http://librdf.org/flickcurl/">flickcurl</a> </strong>(synchronous, libcurl based) <strong>with <a title="flicksoup library" href="http://gitorious.org/flicksoup">flicksoup</a></strong> (asynchronous, libsoup based) as the backend library for dealing with the Flickr API.</li>
	<li><strong>Improved authentication process and made it more "seamless"</strong>, so the application is more aware now of the potential issues that might happen, reporting them to the user if needed (e.g. asking the user to re-authorize the app).</li>
	<li><strong>Better error handling and reporting</strong>, not only about the authorization process but about everything about the user-flickr interaction, which made it way more user-friendly (e.g. quota limit exceeded, host unreachable, process cancelled by the user...).</li>
	<li><strong>Added support to allow cancelling uploads</strong> (no more closing the application if forgotten to do something before pressing 'Upload'!).</li>
	<li><strong>Added support to allow setting pictures to be added to albums</strong> after the upload process. So far, only adding to already existing albums is available, but for the next release allowing the user to create albums on the fly is also planned.</li>
	<li><strong>Menubar redesigned</strong>, so no options get hidden in the contextual menu (did you know there was one?).</li>
	<li><strong>Updated translations</strong>... errr... well... updated THE only translation we have so far (es_ES). Doesn't it make you feel like tranlating frogr to your beautiful language? C'mon, it's a really small file with just a bunch of strings!.</li>
	<li><strong>Simplified code both in frogr and flicksoup</strong>, which should ease a lot future enhancements in next releases of frogr, as former design was blocking quite a lot of things until I changed it once and for all.</li>
	<li>Lots of <strong>bugfixes</strong> and several <strong>minor improvements</strong>.</li>
</ul>
From the point of view of the end user, perhaps it's a bit strange to even mention the flickcurl/flicksoup change in the list of features above, but I couldn't help it since that was the biggest change since 0.2 and what I consider the most important one, since it allowed (or just helped a lot, as you wish) that the rest of points actually happened in the way I thought it would be the right one: through a GNOME-ish library which would allow implementing asynchronous operations without the need of using threads (thanks to the mainloop and implementing the methods using the GIO's GAsync functions), as well as properly reporting errors through GErrors, as it's commonly done in these kind of applications.

I must say flickcurl is still a great C library which currently implements 99% of the remote flickr API, but for this project I found it too complicated and limited for the kind of things I'd like to do in frogr, which was leading me in many ocassions to work things around in many ways that wouldn't be necessary if it was a GObject library based in libsoup, instead of a C library based in libcurl. And that's why I decided to start its implementation, back in February 2010. Unfortunately, the library is not mature enough yet to be separately released, so for the time being I'm just developing it along with frogr, so I can at least release the application, and keeping the intention of release it separately at some point in the future. Still, you can grab the latest code from <a title="flicksoup library" href="http://gitorious.org/flicksoup">its own repository</a> if you want to use it separately, where I regularly dump all the changes I do to it through frogr. But I must warn you, it just implements a few functions so far, those strictly needed by frogr, so don't expect a complete libsoup based version of flickcurl yet, which is far more mature and full of features than this one.

<strong>[UPDATE 03/06/2011]</strong>: Today I removed the flicksoup repository from gitorious since the truth is that at the moment is not an independently maintained library and what I was doing at the end was (i)regularly dumping files from frogr repo to the flicksoup one. And this, apart from being tedious and usually out-of-sync, was also an issue from the point of view of some distros (like Fedora) when it comes to package frogr, so I decided to go ahead and remove it for the time being. Hopefully in the future flicksoup will be released as an independent library, but as for now it is just part of frogr (although I will keep the whole picture in mind when developing changes for flicksoup inside of frogr). More details in <a href="https://bugzilla.redhat.com/show_bug.cgi?id=708765">this bug</a>

As usual, you can grab frogr through different ways:
<ul>
	<li>Source code: clone from <a title="Git repository at gitorious" href="http://gitorious.org/frogr" target="_blank">the git repository at gitorius</a>.</li>
	<li>Tarballs: from <a title="Frogr website: downloads" href="http://code.google.com/p/frogr/downloads/list" target="_blank">the web of the project</a>, in <a title="Source code tarball (gzip)" href="http://frogr.googlecode.com/files/frogr-0.3.tar.gz" target="_self">gzip</a> and <a title="Source code tarball (bzip2)" href="http://frogr.googlecode.com/files/frogr-0.3.tar.bz2">bzip2</a> formats.</li>
	<li>Pre-compiled packages for most common distros: at <a title="Frogr website: downloads" href="http://code.google.com/p/frogr/downloads/list" target="_blank">the web of the project</a>.</li>
</ul>
So far, there are only a few of pre-compiled 32-bit packages for ubuntu and fedora in there (those I generated myself, basically), but hopefully this manual effort could stop being needed at some point in the short terms thanks to the efforts of my mate at <a title="Igalia" href="http://www.igalia.com">Igalia</a> <a title="Alberto Garcia's blog" href="https://blogs.igalia.com/berto">Alberto García</a>, who kindly already packaged for <a title="Debian project" href="http://www.debian.org">debian</a> and <a title="ITP: frogr -- Flickr Remote Organizer for GNOME " href="http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=607889">asked for its inclusion in the project</a>. Thanks, Berto!
