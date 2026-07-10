---
title: Frogr 0.4 is out!
date: '2011-02-05T20:52:34+00:00'
slug: frogr-0-4-is-out
categories:
- frogr
- GNOME
- Planet GNOME
- Planet GPUL
- Planet Igalia
- Planeta GNOME Hispano
wp_id: 398
---

As <a title="My own blog" href="/2011/01/22/some-updates-on-frogr-0-4-and-myself/">I said some days ago</a>, in theory I should be releasing <a title="Frogr's web site" href="http://live.gnome.org/Frogr">Frogr</a> 0.4 this weekend while at <a title="Free and Open Source Developers European Meeting" href="http://www.fosdem.org">FOSDEM</a>, after a 2-week period of feature and string freeze to work on stabilization and bugfixing tasks only. Well, bad news (mainly for myself) is that I did not make it to <a title="Free and Open Source Developers European Meeting" href="http://www.fosdem.org">FOSDEM</a> at the end, due to unavoidable personal matters, but good news is that I'm finally making the release anyway today :-)

So <a title="Frogr's web site" href="http://live.gnome.org/Frogr">Frogr</a> 0.4 is now out and kicking since a couple of hours ago, featuring the following list of changes, as <a title="gnome-announcement-list archives for February 2011" href="http://mail.gnome.org/archives/gnome-announce-list/2011-February/msg00016.html">summarized today in the announcement mail</a>:
<ul>
	<li>Fixed capitalization problems (Philip Withnall).</li>
	<li>Use Unicode ellipsis instead of three dots (Philip Withnall).</li>
	<li>Allow compiling with gtk 3.0 by passing --with-gtk=3.0.</li>
	<li>Raised minimum version required of GTK+ from 2.12 up to 2.14.</li>
	<li>Removed dependency from libgnome.</li>
	<li>Added new man page (Alberto Garcia).</li>
	<li>Fixed slow startup. No longer wait for albums to be loaded.</li>
	<li>New settings dialog to pre-set some values.</li>
	<li>Support for HTTP proxies, through libsoup's API.</li>
	<li>Renamed "Albums" to "Sets".</li>
	<li>Support for creating new sets right from frogr.</li>
	<li>Allow adding pictures to group pools, not just to user albums.</li>
	<li>Allow changing sorting order in 'add to album/group' dialogs.</li>
	<li>Support for seamlessly handling multiple accounts.</li>
	<li>Auto-completion in 'tags' entries.</li>
	<li>Allow setting 'content type' and 'safety level'.</li>
	<li>Allow setting pictures to 'show up on global search results'.</li>
	<li>Remove pictures from UI as soon as they get uploaded.</li>
	<li>Better reporting progress to the users for time consuming operations.</li>
	<li>Allow specifying a list of pictures to be loaded from command line.</li>
	<li>Register frogr as image mime types handler, so it's possible to load pictures on it from other applications (e.g. nautilus or eog).</li>
	<li>Improved keyboard usability by adding mnemonics, making text views not to accept tab and enabling the menu key in the icon view.</li>
	<li>Nine new translations (see <a title="Frogr's TRANSLATORS file" href="http://git.gnome.org/browse/frogr/tree/TRANSLATORS">TRANSLATORS</a> file for details).</li>
	<li>As usual, lots of bugfixes and several minor improvements.</li>
</ul>
From a more practical point of view, let's just say that <a title="Frogr's web site" href="http://live.gnome.org/Frogr">Frogr</a> 0.4 is the first "serious" release, in the way that it should provide a fairly good amount of features for the average <a title="Flickr" href="http://www.flickr.com">Flickr</a> users to feel comfortable using it for their typical use cases. Nevertheless, development won't stop here so don't hesitate to contribute with the project if you feel like doing it, either by proposing ideas, <a title="Frogr module at l10n.gnome.org" href="http://l10n.gnome.org/module/frogr/">translating</a>, <a title="Frogr's git repository" href="http://git.gnome.org/browse/frogr">coding</a>, <a title="Frogr's mailing list" href="http://mail.gnome.org/mailman/listinfo/frogr-list">discussing</a> or even by <a title="File new bugs for Frogr" href="https://bugzilla.gnome.org/enter_bug.cgi?product=frogr">filing</a> or <a title="Frogr's list of bugs" href="https://bugzilla.gnome.org/browse.cgi?product=frogr">fixing</a> bugs.

As usual, you can get it through different ways:
<ul>
	<li>Source code: clone from <a title="Frogr's git repository" href="http://git.gnome.org/browse/frogr">the git repository at gnome.org</a>.</li>
	<li><a title="Git repository at gitorious" href="http://gitorious.org/frogr" target="_blank"></a>Tarballs: both in <a title="Source code tarball (gzip)" href="http://download.gnome.org/sources/frogr/0.4/frogr-0.4.tar.gz" target="_self">gzip</a> and <a title="Source code tarball (bzip2)" href="http://download.gnome.org/sources/frogr/0.4/frogr-0.4.tar.bz2">bzip2</a> formats.</li>
	<li>Pre-compiled packages for most common distros: at <a title="Frogr website: downloads" href="http://people.gnome.org/~mario/files/frogr" target="_blank">the web of the project</a>.</li>
</ul>
Hope you like this tiny little application. For more information, just check out <a title="Frogr's web site" href="http://live.gnome.org/Frogr">its web site</a>.

Ah! And as <em>everybody loves screenshots </em>(tm), here you have one composition of several of them  so you can realize how it looks now in my desktop:

<a href="/wp-content/uploads/2011/02/frogr-0_4-screenshot.png"><img class="aligncenter size-full wp-image-418" src="/wp-content/uploads/2011/02/frogr-0_4-screenshot-thumb.png" alt="Frogr 0.4 screenshots" width="476" height="350" /></a>
