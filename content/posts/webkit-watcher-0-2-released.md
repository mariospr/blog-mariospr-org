---
title: WebKit Watcher 0.2 released
date: '2012-06-01T02:04:42+00:00'
slug: webkit-watcher-0-2-released
categories:
- Android
- Java
- Planet GNOME
- Planet GPUL
- Planet Igalia
- Planet WebKitGTK
- Planeta GNOME Hispano
- WebKit
- WebKit2
- WebKitGTK
- WebKitWatcher
wp_id: 773
---

Some time ago I wrote a (very!) <a title="WebKit Watcher 0.1 released" href="/2010/12/06/watching-the-webkit-buildbots-from-your-android-phone/">small android application to scratch an itch I had</a>: being able to easily check the status of <a title="WebKit build bots" href="http://build.webkit.org/">WebKit buildbots</a> right from my phone, which turned out to be quite useful in some scenarios.

And no, I'm not the kind of guy that does the <a title="Cool developers don't look at the buildbots" href="http://webkitmemes.tumblr.com/post/18264800090/cool-developers-dont-look-at-the-build-bots">"Land Patch / Goes Home"</a> thing, but sometimes you see yourself in the situation of having to leave your workplace before than expected <strong>and</strong> after having committed certain kind of patches a while ago. And in such a situation <a title="WebKit Watcher" href="https://play.google.com/store/apps/details?id=com.igalia.mario.webkitwatcher">WebKit Watcher</a> has proved to be a helpful tool many times, at least to me.

So, what's new in this 0.2 release? Not many bells and whistles, to be honest, I just scratched a couple of small itches more I felt today, while going back to working as <em>gardener</em> for the <a title="WebKitGTK+" href="http://www.webkitgtk.org">WebKitGTK+</a> port. Basically:
<ul>
	<li>Replaced the main view showing only the core bots with a (static) list of the different platforms, so you know can  now check the results for all the bots of a specific platform. Selecting a platform will take you to the typical view showing the results for every build bot associated to it.</li>
	<li>Added possibility of checking the results for all the bots in a single list view ('All' item in the main view), as previously only those "marked" as 'core bots' were shown in the application. Now you can check the results of all the 43 bots, in case you want to.</li>
	<li>Removed unnecessary permission <em>CHANGE_NETWORK_STATE</em>, as I personally <strong>hate</strong> apps asking me for more permissions than those strictly needed. I'm still wondering why I added that in the first place...</li>
</ul>
And now, some screenshots that will make your eyes bleed because of the 'design' of this app:

<a href="/wp-content/uploads/2012/06/20120601-WebKitWatcher-1.png"><img class="alignnone" src="/wp-content/uploads/2012/06/20120601-WebKitWatcher-1-thumb.png" alt="" width="156" height="260" /></a> <a href="/wp-content/uploads/2012/06/20120601-WebKitWatcher-2.png"><img class="alignnone" src="/wp-content/uploads/2012/06/20120601-WebKitWatcher-2-thumb.png" alt="" width="156" height="260" /></a> <a href="/wp-content/uploads/2012/06/20120601-WebKitWatcher-3.png"><img class="alignnone" src="/wp-content/uploads/2012/06/20120601-WebKitWatcher-3-thumb.png" alt="" width="156" height="260" /></a>

I told you it was so beautiful!

By the way, you can grab it and install this app through several ways:
<ul>
	<li><strong>Google Play</strong>: just <a title="WebKit Watcher in Google Play" href="https://play.google.com/store/apps/details?id=com.igalia.mario.webkitwatcher">look for “webkit”</a></li>
	<li><strong>The<em> .APK</em> file</strong> to install by copying to the device: grab it from <a title="WebKit Watcher .APK file" href="/misc/WebKitWatcher.apk">here</a></li>
	<li><strong>Source code</strong>: get it from <a title="WebKit Watcher git respository" href="http://gitorious.org/webkit-watcher">its git repository</a></li>
</ul>
