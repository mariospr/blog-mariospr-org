---
title: (freedesktop) Tray icon for Vagalume
date: '2008-04-25T11:31:41+00:00'
slug: freedesktop-tray-icon-for-vagalume
categories:
- GNOME
- Maemo
- Planet GNOME
- Planet GPUL
- Planet Igalia
- Planet Maemo
- Vagalume
wp_id: 25
---

As you might know, some time ago I developed a plugin for the <a title="Maemo: code in your hands" href="http://www.maemo.org" target="_blank">maemo</a> version of <a title="Vagalume web site" href="http://vagalume.igalia.com">Vagalume</a> which would allow the user to manage the most basic features from a tiny icon in the status bar.

After that, I thought it could be a good idea to implement a <a title="Freedesktop" href="http://www.freedesktop.org" target="_blank">freedesktop</a> <a title="System Tray Protocol Specification" href="http://standards.freedesktop.org/systemtray-spec/systemtray-spec-0.2.html" target="_blank">tray icon</a> as well, so you would be able to hide/show <a title="Vagalume web site" href="http://vagalume.igalia.com">Vagalume</a> with a tray icon in the notification area, in the same way you could do it with some other programs such as <em>pidgin</em>, <em>xchat</em> or <em>rhythmbox</em>, for instance. Moreover, some people told me that it would be very nice to have a tray icon in the desktop version of vagalume, so everything seemed to say that I was not mad after all and that it could be a good idea...

So, I've started working on its implementation (using a <a title="GtkStatusIcon: API reference" href="http://library.gnome.org/devel/gtk/2.11/GtkStatusIcon.html" target="_blank"><em>GtkStatusIcon</em></a>) some weeks ago and now I finally managed to get the enough 'spare time' to plug everything together and to finally <strong>finish</strong> the patch for being applied to one of the latest revisions of the <em>SVN trunk</em> (158). In fact, at this moment I've already sent it to <em>vagalume-devel@maemo.org</em> mailing list and I'm waiting for <a title="Berto's blog" href="https://blogs.igalia.com/berto">Berto</a> to take a look into it to finally integrate it for (hopefully) the next release :-)

<strong>Update [2008/04/29]:</strong> After working a bit more on this new tray icon during the past weekend I've <strong>added libnotify support</strong> to allow the tray icon to show a notification each time <a title="Vagalume web site" href="http://vagalume.igalia.com">Vagalume</a> starts playing a new song. Of course, as I know there're people who might dislike this feature, I've also added the possibility of disabling these notifications from the 'Settings' dialog in the <a title="The GNOME project" href="http://www.gnome.org" target="_blank">GNOME</a> version of the application. I've also added an screenshot of the notifications working at the end of this post.

To finish with this post, and knowing that sometimes an image is better than just a description, here you are a couple of screenshots of the new tray icon working in my <a title="The GNOME project" href="http://www.gnome.org" target="_blank">GNOME</a> environment:
<p align="center"><a href="/wp-content/uploads/2008/04/20080425-vagalume_tray_icon-menu.png" target="_blank"><img src="/wp-content/uploads/2008/04/20080425-vagalume_tray_icon-menu-thumb.png" alt="Vagalume's tray icon: showing the menu" align="middle" /></a></p>
<p align="center"><em>Vagalume's tray icon: showing the menu</em></p>
<p align="center"><img src="/wp-content/uploads/2008/04/20080425-vagalume_tray_icon-tooltip.png" alt="Vagalume's tray icon: showing the tooltip" align="middle" /></p>
<p align="center"><em>Vagalume's tray icon: showing the tooltip</em></p>
<p align="center"><img src="/wp-content/uploads/2008/04/20080429-vagalume_tray_icon-notifications.png" alt="Vagalume's tray icon: showing playback notifications" align="middle" /></p>
<p align="center"><strong>Update [2008/04/29]: </strong><em>Vagalume's tray icon: showing playback notifications</em></p>
<p align="left">And that's all. I hope the patch is good enough to integrate it with the next release of <a title="Vagalume web site" href="http://vagalume.igalia.com">Vagalume</a>. Of course, suggestions and criticisms are always welcome, so don't hesitate to leave your comments here.</p>
<p align="left">I hope you like it ;-)</p>
