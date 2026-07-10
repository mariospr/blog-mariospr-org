---
title: Frogr 0.7 released
date: '2012-05-23T19:08:34+00:00'
slug: frogr-0-7-released
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
wp_id: 742
---

As you might already know <a title="Flickr now Supports OAuth 1.0a" href="http://code.flickr.com/blog/2011/06/21/flickr-now-supports-oauth-1-0a/">Flickr has added support for OAuth a while ago</a>, which is meant to be the obvious replacement to the <a title="The old Flickr auth API" href="http://www.flickr.com/services/api/misc.userauth.html">old Flickr auth API</a> that has been available since a long long time ago, which has been used by many applications our there, like <a title="Frogr" href="https://live.gnome.org/Frogr">frogr</a>. But the important point here for apps using the old auth method is that <a title="Farewell FlickrAuth" href="http://code.flickr.com/blog/2012/01/13/farewell-flickrauth">it won't be longer available after July 31st</a>, which means they should get updated if they want to keep working as so far.

<a href="/wp-content/uploads/2012/05/20120523-frogr-screenshot.png"><img class="aligncenter" src="/wp-content/uploads/2012/05/20120523-frogr-screenshot-thumb.png" alt="Frogr 0.7" width="520" height="325" /></a>

So, this is the <strong>main point of this release</strong>: to update the internal implementation of the <a title="Flickr REST API" href="http://www.flickr.com/services/api/">Flickr REST API</a> in <a title="Frogr" href="https://live.gnome.org/Frogr">frogr</a> (which, ideally, will be released independently as a library at some point) to use <a title="OAuth documentation" href="http://oauth.net/">OAuth</a> instead of the old authentication API.

Additionally, in order to make things easier for users of older versions, the application will take care of exchanging the authentication token from the old system to the new ones used by the <a title="OAuth documentation" href="http://oauth.net/">OAuth</a> API. If you want to know more details about this, check <a title="flickr.auth.oauth.getAccessToken" href="http://www.flickr.com/services/api/flickr.auth.oauth.getAccessToken.html">the related API</a>. For the rest of you, you shouldn't notice anything the first time you run this new release.

Still, some other things were included in this new release that are worth mentioning:
<ul>
	<li>Ability to import tags already present in pictures  (e.g. as set by f-spot or shotwell).</li>
	<li>Allow users deciding, right from <a title="Frogr" href="https://live.gnome.org/Frogr">frogr</a> and on a picture-by-picture basis, whether to set the geolocation information for pictures when uploading them to <a title="Flickr" href="http://www.flickr.com">Flickr</a>.</li>
	<li>New tags are added to the auto-completion without having to upload anything first.</li>
	<li>Allow using a dark version of your theme if available (e.g. Adwaita).</li>
	<li>Some redesign of the menu bar, thinking of a future migration to <a title="GMenu API documentation" href="http://developer.gnome.org/gio/stable/GMenu.html">GMenu</a>.</li>
	<li>Added menu accelerators for the most common operations.</li>
	<li>As usual, bugfixes, cleanups... that kind of stuff.</li>
</ul>
Also, you can check the <a title="Frogr 0.7 announcement mail" href="https://mail.gnome.org/archives/gnome-announce-list/2012-May/msg00023.html">announcement mail</a> or the <a title="Frogr's NEWS file" href="http://git.gnome.org/browse/frogr/tree/NEWS">NEWS file</a> if you want for more detail about this new release, as well as <a title="Frogr's website" href="https://live.gnome.org/Frogr">the website of the project</a> for additional information, such as knowing about <a title="Get involved in frogr" href="https://live.gnome.org/Frogr#Get_Involved">ways of collaborating</a> or <a title="Get frogr" href="https://live.gnome.org/Frogr#Get_Frogr">how to get frogr installed on your system</a>.

I think that's it. Enjoy!
