---
title: Frogr 0.2 released!
date: '2009-10-13T00:07:54+00:00'
slug: frogr-0-2-released
categories:
- Debian
- frogr
- GNOME
- Planet GNOME
- Planet GPUL
- Planet Igalia
- Ubuntu
wp_id: 132
---

After coming back from an awesome week of holidays in Paris (lovely city, btw!), today I finally managed to get some time for making up what it became the second upstream release of frogr: <strong>frogr 0.2</strong>

Just trying to give a brief update on "what is new", here you have an excerpt from the <strong>NEWS</strong> file:
<ul>
	<li> Generate ChangeLog from git log with 'make dist'</li>
	<li>Added .spec file for fedora 11 packaging system (thanks Adrián Pérez)</li>
	<li>Added drag'n'drop support for loading pictures in frogr</li>
	<li>Added support to add tags to pictures (instead of just replacing)</li>
	<li>Fixed (legacy) support for libgnome2 to compile in debian lenny</li>
	<li>Use accesor functions instead direct access and removed some deprecated GTK+ symbols (thanks Javier Jardón)</li>
	<li>Added i18n support and a es_ES lang file (thanks Alejandro Piñeiro, aka API)</li>
	<li>Support silent build rules with automake 1.11 (thanks Javier Jardón)</li>
	<li>Bugfixes and several minor improvements</li>
</ul>
Entering in more detail, and as you can easily extract from the list above, the main improvements from the user's point of view are:
<ul>
	<li>Drag'n'drop now supported, so having to add pictures through the filechooser is no longer the only method to load pictures in frogr.</li>
	<li>New "add tags" dialog, very handy to add tags to some specific pictures before uploading them.</li>
	<li>i18n support, which should make easier to get more contributions for frogr in further releases, in the form of new translations to make it even more accessible for people all over the world (did I say we're eager for new language files?)</li>
</ul>
At last, just to mention that you already can find pre-compiled packages for some distros at <a title="Frogr website" href="http://code.google.com/p/frogr" target="_blank">the web of the project</a>, as well as the source code tarballs in <a title="Source code tarball (gzip)" href="http://frogr.googlecode.com/files/frogr-0.2.tar.gz" target="_self">gzip</a> and <a title="Source code tarball (bzip2)" href="http://frogr.googlecode.com/files/frogr-0.2.tar.bz2">bzip2</a> formats. And of course, get the source code from <a title="Git repository at gitorious" href="http://gitorious.org/frogr" target="_blank">the git repository at gitorius</a>, in case you prefer to directly clone the source tree to make up wonderful and nice patches to contribute with, or just to provide new pre-compiled packages for your favourite distro ;-)

So... what else could I say? Just go and get it... Hope you enjoy it as much as I do :-)

<strong>Update [2009/10/14]</strong>: It seems the other day my mind was still a bit "on holidays" :-) and I screwed it up when creating both the pre-compiled packages and the source tarballs uploaded to <a title="Frogr website" href="http://code.google.com/p/frogr" target="_blank">the web of the project</a>, so they would just not  work as they should when installing frogr (basically, they would not install files under the proper path so frogr just would not work).

I realized of this yesterday and now everything should be fixed in packages (and tarballs) uploaded in the "Downloads" section of such a web, so if you experienced any problems two days ago just try now again and everything should be fine.
