---
title: The new status bar plugin for Vagalume
date: '2008-01-31T17:06:22+00:00'
slug: the-new-status-bar-plugin-for-vagalume
categories:
- GNOME
- Maemo
- Planet GNOME
- Planet GPUL
- Planet Igalia
- Planet Maemo
- Vagalume
wp_id: 19
---

Hi all,

It has been a long time since <a title="Live report from DudesConf (3 a.m. in the morning)" href="/2007/04/15/live-report-from-dudesconf-2-am-in-the-morning/">my last post</a> (April 15th, 2007), so I think that it's time to write something again... and I can't think of a better chance to do it that talking about this... :-)

As many of you could know, last November 1st my mate <a title="Berto's personal web" href="http://people.igalia.com/berto/">Berto</a> <a title="First release of Vagalume" href="https://blogs.igalia.com/berto/2007/11/01/vagalume-01-released-come-and-get-it/" target="_blank">released the first version</a> of his <a title="GNOME: The Free Software Desktop Project" href="http://www.gnome.org/" target="_blank">Gnome</a>/<a title="Maemo" href="http://maemo.org/" target="_blank">Maemo</a> <a title="Last.fm: The social music revolution" href="http://www.lastfm.com" target="_blank">Last.fm</a> (codenamed "Vagalume 0.1"), which <a title="First release of Vagalume" href="https://blogs.igalia.com/berto/2007/11/01/vagalume-01-released-come-and-get-it/" target="_blank">started being just a "three-button application"</a> and <a title="Vagalume 0.2 released" href="https://blogs.igalia.com/berto/2007/11/09/vagalume-02-its-amazing-and-flies/">evolved</a> <a title="Vagalume 0.3 released" href="https://blogs.igalia.com/berto/2007/11/21/vagalume-03-now-with-some-images-too/">to be</a> <a title="Vagalume 0.4 released" href="https://blogs.igalia.com/berto/2007/12/14/its-been-a-hard-days-night/">a nice application</a> to listen your favorite custom radio stations, providing lots of the typical features that a <a title="Last.fm: The social music revolution" href="http://www.lastfm.com" target="_blank">Last.fm</a> user would expect.

So, besides to all the new features <a title="Berto's personal web" href="http://people.igalia.com/berto/">Berto</a> has been adding everyday, and besides to the nice new UI enhancements <a title="Felipe's blog" href="https://blogs.igalia.com/femorandeira">Felipe</a> has been working on (which will be out with release 0.5)... I also wished to contribute to Vagalume with a new component: a status bar plugin for the Maemo platform.

And taking into account <a title="Berto's personal web" href="http://people.igalia.com/berto/">Berto</a> has just committed <a title="Vagalume status bar plugin patch (revs 85-86)" href="/sources/vagalume/patches/20080131-sb-plugin-r85_86.patch">my patch</a> yesterday (revision 86 of <em>SVN trunk</em> [<strong>*</strong>]), I thought of it could be a good moment to talk about the new plugin itself, so here it goes...

The new status bar plugin would allow Vagalume users to control some features of the application from the status bar:
<ul>
	<li>Check out basic info about the song being played: title / artist / album.</li>
	<li>Play / Stop / Skip songs.</li>
	<li>Love and Ban songs</li>
	<li>Bring Vagalume main window to the front.</li>
	<li>Close Vagalume.</li>
</ul>
And that's all. As you can see there are only a couple of commands available to be executed from the plugin, but we thought it would be the right way not to overcharge it too much with "advanced" features, and just to focus it to provide only basic actions. After all, it was designed to be an small plugin, wasn't it?

At last, just to point out communication is currently carried out by specific <a title="Dbus" href="http://www.freedesktop.org/wiki/Software/dbus">Dbus</a> messages between Vagalume and the plugin, although, in the future, this could change into one of the following ways:
<ul>
	<li>Change the <a title="Dbus" href="http://www.freedesktop.org/wiki/Software/dbus">Dbus</a> methods (with specific destination set: Vagalume main app or the plugin) into broadcast signals, so any application in the platform could interact with Vagalume in the same way the plugin does.</li>
	<li>...or maybe supporting <a title="XMMS2  MPRIS" href="http://wiki.xmms2.xmms.se/index.php/MPRIS" target="_blank">MPRIS</a> standard interface could be a better way to allow integration between Vagalume any other application (Thanks for your suggestion, <a title="Juan's blog" href="https://blogs.igalia.com/jasuarez">Juan</a>).</li>
</ul>
Of course there are more improvements planned for the near future of the plugin, such as:
<ul>
	<li>Adding support for <a title="maemo.org: OS2006" href="http://maemo.org/downloads/OS2006">OS2006</a> and <a title="maemo.org: OS2007" href="http://maemo.org/downloads/OS2007">OS2007</a> in maemo platforms (now, the plugin only works with <a title="maemo.org: OS2008" href="http://maemo.org/downloads/OS2008">OS2008</a>).</li>
	<li>Adding a new dock plugin supporting <a title="Freedesktop.org" href="http://www.freedesktop.org/wiki/" target="_blank">freedesktop.org</a> specs, to allow desktop users to have a similar plugin.</li>
	<li>Adding a new action to allow hiding the Vagalume main app so it's not shown in the "tasks list panel" (desktop), or in the "task navigator" (<a title="Maemo" href="http://maemo.org/" target="_blank">Maemo</a>).</li>
	<li>... any suggestions? ;-)</li>
</ul>
So, I think that's all so far. Now I just hope Vagalume users enjoy this plugin as much as I enjoyed developing it (and using it, of course). IMHO, I think it's a nice way to "control" basic actions of Vagalume from the status bar, without having to open the main window when you're running another application (the web browser or talking with the IM application, for instance), and just by using the drop down panel by clicking in the icon.

But of course, this is my (personal) opinion, so please post any comment you want about this. They will be highly appreciated!

So, let's wait for the 0.5 release to see what people think about the new version of Vagalume, I have the feeling it's going to rock! ;-)

In the meanwhile, here you are a example of the status bar plugin being usen while surfing the web:

<a title="Vagalume status bar plugin screenshot (high resolution)" href="/wp-content/uploads/2008/01/20080131-vagalume_sb_plugin.png"><img src="/wp-content/uploads/2008/01/20080131-vagalume_sb_plugin-thumb.png" alt="Vagalume status bar plugin screenshot" /></a>

Stay tuned, it's coming soon!

[<strong>*</strong>] :: To checkout the code from <em>SVN trunk</em>:
<pre>svn co https://garage.maemo.org/svn/vagalume/trunk</pre>
