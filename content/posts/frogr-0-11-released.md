---
title: Frogr 0.11 released
date: '2015-01-08T04:09:49+00:00'
slug: frogr-0-11-released
categories:
- Debian
- Fedora
- Fosdem
- frogr
- GNOME
- Planet GNOME
- Planet GPUL
- Planeta GNOME Hispano
- Ubuntu
wp_id: 1782
---

<p style="text-align: center;"><a href="/wp-content/uploads/2015/01/20150107-frogr-screenshot.png"><img class="size-full wp-image-1784 aligncenter" alt="Screenshot of Frogr 0.11" src="/wp-content/uploads/2015/01/20150107-frogr-screenshot-thumb.png" width="520" height="325" /></a></p>
So, after neglecting my responsibilities with this project for way too long, I finally <a title="Announcement email" href="https://mail.gnome.org/archives/frogr-list/2015-January/msg00000.html">released frogr 0.11 now</a>, making the most that I'm now enjoying some kind of "parenting vacation" for a few days.

Still, do not expect this new release to be fully loaded of new features and vast improvements, as it's more like another incremental update that adds a couple of nice new things and fixes a bunch of problems I was really unhappy about (e.g. general slowness, crashes).

Wrapping it up, the main changes included with this release are:
<ul>
	<li>Moved to the new GTK+'s header bar plus the typical <em>menu button</em> when GTK+ &gt;= 3.12 (GTK+ 3.4 is still supported). I personally like this change a lot, as it makes frogr much more compact and sleek IMHO, and much better integrated with newer releases of <a title="The GNOME project" href="http://www.gnome.org">GNOME</a>.</li>
	<li>Added a new option to automatically replace the "date posted" field in flickr with the "date taken" value from the EXIF metadata when uploading pictures. Useful to keep your photo stream sorted regardless of when you uploaded which pictures. Thanks a lot to <a title="Luc Pionchon's blog" href="http://oluc.blogspot.co.uk/">Luc Pionchon</a> for <a title="Bug 734193 - on upload, set 'upload date' to 'taken date' " href="https://bugzilla.gnome.org/show_bug.cgi?id=734193">requesting this feature</a>. I never thought of it before, now I use it all the time!</li>
	<li>Sped up the load of pictures into the main window, as it was a very slow process when importing tags from the XMP keywords was enabled. I measured a 3x improvement, but <em>YMMV</em>.</li>
	<li>Fixed random crashes due to the missing initialization of the gcrypt library introduced with the recent changes to use SSL API end points. Thanks a lot <a title="Andres's blog" href="http://blog.andresgomez.org/">Andrés</a> for your help with this!</li>
	<li>Fixed issues related to the OS X port, which prevented frogr 0.9 from having video support and caused many problems with the 0.10 release. Now it should be fine, <a title="OS X port of frogr" href="http://ftp.acc.umu.se/pub/gnome/binaries/mac/frogr">grab the bundle from here</a>.</li>
	<li>Other things: removed calls to deprecated APIs, updated translations, fixed a few minor bugs and a bit of a clean-up here and there, which is usually good.</li>
</ul>
As usual, feel free to check <a title="Frogr's website" href="https://wiki.gnome.org/Apps/Frogr">the website of the project</a> in case you want to know more about <a title="Frogr" href="https://wiki.gnome.org/Apps/Frogr">frogr</a>, <a title="Get frogr" href="https://wiki.gnome.org/Apps/Frogr#Get_Frogr">how to get it</a> or how to contribute to it. I'm having a hard time lately to find time to devote to this pet project, so any help anyone can provide will be more than welcome :-) <a href="http://www.fosdem.org"><img class="size-full wp-image-1802 alignright" alt="fosdem-15-logo" src="/wp-content/uploads/2015/01/fosdem-15-logo.png" width="163" height="29" /></a>

By the way, I'm going to <a href="http://www.fosdem.org">FOSDEM</a> this year again, so feel free to say "hi" if you want to chat and/or share a beer (or more!).
