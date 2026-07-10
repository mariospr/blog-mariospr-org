---
title: Watching the WebKit buildbots from your Android phone
date: '2010-12-06T13:24:12+00:00'
slug: watching-the-webkit-buildbots-from-your-android-phone
categories:
- Android
- Java
- Planet GNOME
- Planet GPUL
- Planet Igalia
- Planeta GNOME Hispano
- WebKit
- WebKitGTK
- WebKitWatcher
wp_id: 290
aliases:
- /2010/12/06/watching-the-webkit-buildbots-from-your-phone/
---

<a href="/wp-content/uploads/2010/12/device2.png"><img class="alignright size-thumbnail wp-image-291" src="/wp-content/uploads/2010/12/device2-150x150.png" alt="WebKit Watcher screenshot" width="150" height="150" /></a>This is a short post just to let the world know about my last pet-project, which I managed to name, after several hours struggling, <strong>WebKit Watcher</strong>.

WebKit Watchers is a really simple and minimalistic application that allows you to easily monitorize the status of the WebKit buildbots as you would do it through <a title="WebKit buildbot" href="http://build.webkit.org">build.webkit.org</a>, but from your Android powered device.

It currently works as follows:
<ul>
	<li>Supports watching the core builders only (as in <a title="WebKit core builders console" href="http://build.webkit.org/console?category=core">this url</a>)</li>
	<li>Browse extra details about a builder/build/SVN commit through the browser</li>
	<li>Requires manual refreshing (this is actually a feature to save battery :P)</li>
	<li>Provides an ugly logo (could be uglier, though)</li>
</ul>
As I said, a really simple application that I wrote as part of my weekly hackfest time here at <a title="Igalia" href="http://www.igalia.com">Igalia</a> to satisfy my curiosity about trying out the Android SDK now I got a new phone while, at the same time, scratching an itch I had.

Next steps for following versions would probably go through adding some kind of support for periodical checks and notifications when some buildbots are red, adding support for non-core builders (while allowing the user to filter them out anyway, in case he/she wouldn't be interested in those), and things like that...

By the way, I'm open to suggestions (and patches too), after all it was licensed as a Free Software project you can grab through several ways:
<ul>
	<li>Android Market: just look for "webkit"</li>
	<li>The .APK file to install by copying to the device: grab it from <a title="WebKit Watcher .APK file" href="/misc/WebKitWatcher.apk">my web at Igalia</a></li>
	<li>Source code: get it from <a title="WebKit Watcher git respository" href="http://gitorious.org/webkit-watcher">its git repository</a></li>
</ul>
That's all so far. Hope some of you will fint it useful too.
