---
title: Frogr 0.1 released!
date: '2009-08-22T01:32:10+00:00'
slug: frogr-0-1-released
categories:
- Debian
- frogr
- GNOME
- Planet GNOME
- Planet GPUL
- Planet Igalia
- Ubuntu
wp_id: 116
---

After perhaps quite a long time since <a title="Frogr first announcement" href="/2009/06/05/frogr-flickr-remote-organizer-for-gnome/" target="_self">I announced the "pre-release" of frogr, back in June</a>, I'm now happy to tell the world that the <strong>0.1 release</strong> is finally here, providing the user a very basic but still useful set of features to upload his/her pictures to flickr. Basically, as it's told in the <strong>NEWS</strong> file, most important changes in this first release regarding to the code from almost 2 montsh ago are:
<ul>
	<li>A better UI. Faster and better user experience.</li>
	<li>Basic configuration management to store account details (auth token).</li>
	<li>Support for editing details of multiple pictures at the same time.</li>
	<li>Added status and improved the progress bar usage to show the status of async operations, giving a much better feedback to the end user.</li>
	<li>A better (and more easily hackable) code and design.</li>
	<li>No more .glade files, no more gtk-builder-convert.</li>
	<li>Avoid libgnome dependency if gtk+ &gt;= 2.14 is present</li>
	<li>Still implemented some parts of the UI (menubar) without GtkBuilder to keep compatibility with Gtk+ 2.12 (least version supported)</li>
	<li>Bugfixes and several (minor and major) improvements</li>
</ul>
As usual you can get the source code at <a title="Git repository at gitorious" href="http://gitorious.org/frogr" target="_blank">http://gitorious.org/frogr</a>, where development for version 0.2 has already started, btw. And if you visit the project's web at<a title="Frogr website" href="http://code.google.com/p/frogr" target="_blank"> http://code.google.com/p/frogr</a> you could even find some packages for you favourite distro there as well (currently only i386 packages for Ubuntu hardy, intrepid and jaunty are available, but more flavours and platforms are coming soon: debian, fedora, x86_64...).

For the special case of <strong>hardy</strong> you'll need to install a newer version of <em>libflickcurl0</em> than the bundled in hardy repositories (0.12), which you can get from here: <a title="libflickcurl0 1.3-1" href="http://packages.ubuntu.com/intrepid/libflickcurl0" target="_blank">http://packages.ubuntu.com/intrepid/libflickcurl0</a> (yes, intrepid package will work fine on hardy).

At last, knowing that people use to love screenshots, here you have three of them showing the current status and UI for frogr 0.1. Yes I know, still not too 'eye-candy' but hey!... it's the 0.1 release! what did you expect? We'll have time enough to improve the UI in the future as long as frogr gets more mature and complete. And in the meanwhile I honestly think current UI is not a complete disaster either :-)
<p style="text-align: center"><a href="/wp-content/uploads/2009/08/20090822-frogr-0_1-screenshot.png"><img class="size-full wp-image-118 aligncenter" src="/wp-content/uploads/2009/08/frogr-0_1-screenshot_thumb1.png" alt="Frogr 0.1 screenshots" width="470" height="354" /></a></p>
<p style="text-align: left">Hope you find this interesting.</p>
<p style="text-align: left">Have fun!</p>
