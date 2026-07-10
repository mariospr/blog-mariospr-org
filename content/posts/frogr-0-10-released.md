---
title: Frogr 0.10 released
date: '2014-06-17T03:44:27+00:00'
slug: frogr-0-10-released
categories:
- Debian
- Fedora
- frogr
- GNOME
- Planet GNOME
- Planet GPUL
- Planeta GNOME Hispano
- Ubuntu
wp_id: 1722
---

<a href="/2014/06/17/frogr-0-10-released/frogr/" rel="attachment wp-att-1723"><img class="alignright size-full wp-image-1723" alt="frogr" src="/wp-content/uploads/2014/06/frogr.png" width="128" height="128" /></a>Quick post to let the world know that I've <a title="Announcement email" href="https://mail.gnome.org/archives/frogr-list/2014-June/msg00000.html">just released a new version of frogr right now</a>, in order to address a few issues present in the previous version. Mainly:
<ul>
	<li>Deprecation of non-SSL end points for the <a title="Flickr API" href="https://www.flickr.com/services/developer/api/">Flickr API</a> (see these <a title="New SSL Endpoints for the Flickr API" href="http://code.flickr.net/2014/02/24/new-ssl-endpoints-for-the-flickr-api/">two</a> <a title="Flickr API Going SSL-Only on June 27th, 2014" href="http://code.flickr.net/2014/04/30/flickr-api-going-ssl-only-on-june-27th-2014/">posts</a> for more info). From now on, <a title="Frogr" href="https://wiki.gnome.org/Apps/Frogr">frogr</a> will use SSL-only API calls.</li>
	<li>Address issues with <a title="Frogr" href="https://wiki.gnome.org/Apps/Frogr">frogr</a>'s <a title="AppData specification" href="http://people.freedesktop.org/~hughsient/appdata/">AppData</a> file. Apparently, the AppData file was neither valid (according to <a title="AppData validation tools" href="https://github.com/hughsie/appdata-tools"><em>appdata-validate</em></a>) nor being installed properly, preventing <a title="Frogr" href="https://wiki.gnome.org/Apps/Frogr">frogr</a> from showing up nicely in the <a title="GNOME Software" href="https://wiki.gnome.org/Apps/Software">GNOME Software app</a>.</li>
	<li>Allow disabling video uploads at configuration time (enabled by default), instead of making the decision depending on the detected platform. This will hopefully make life easier for packagers of other platforms (e.g. <a title="MacPorts" href="http://www.macports.org/">MacPorts</a>).</li>
	<li>Removed <a title="libsoup" href="https://wiki.gnome.org/action/show/Projects/libsoup">libsoup-gnome</a> code once and for all (API deprecated a while ago).</li>
	<li>Other things: updated translations and fixed a few minor bugs.</li>
</ul>
As usual, feel free to check <a title="Frogr's website" href="https://wiki.gnome.org/Apps/Frogr">the website of the project</a> in case you want to know more about <a title="Frogr" href="https://wiki.gnome.org/Apps/Frogr">frogr</a>, <a title="Get frogr" href="https://wiki.gnome.org/Apps/Frogr#Get_Frogr">how to get it</a> or how to contribute to it.
