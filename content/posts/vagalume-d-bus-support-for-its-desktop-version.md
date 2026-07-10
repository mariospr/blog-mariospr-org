---
title: 'Vagalume: D-Bus support for its desktop version'
date: '2008-06-13T17:56:15+00:00'
slug: vagalume-d-bus-support-for-its-desktop-version
categories:
- GNOME
- Maemo
- Planet GNOME
- Planet GPUL
- Planet Igalia
- Planet Maemo
- Vagalume
wp_id: 29
---

As you can check out in the <em>vagalume-devel@garage.maemo.org</em> mailing list archives:

<a title="vagalume-devel mailing list archives" target="_blank" href="https://garage.maemo.org/pipermail/vagalume-devel/2008-June/000151.html">https://garage.maemo.org/pipermail/vagalume-devel/2008-June/000151.html</a>

...today I've finished the implementation of a new patch for <a title="Vagalume web site" href="http://vagalume.igalia.com">Vagalume</a> which will enable D-Bus support in the desktop version of this nice player, since so far D-Bus interaction was only allowed in the maemo platform (due to using functions from <em>libosso</em> for RPC methods, instead of <em>dbus-glib</em>).

So, this is how the <em>vagalumectl</em> script (formerly known as <a title="My sloppy, dirty, ugly… but (maybe) useful script for the Vagalume D-Bus interface" href="/2008/03/01/my-sloppy-dirty-ugly-but-maybe-useful-script-for-the-vagalume-d-bus-interface/"><em>vagalume-dbus</em></a>) would work from now on in a "regular" GNU/Linux machine:
<blockquote>mario@bender:~$ vagalumectl
Usage:
vagalumectl
(Vagalume will be automatically started if not already running)

COMMAND:
play:              start playing the current radio
skip:              skip to the nex song in the current radio
stop:              stop playing the current radio
love:              mark the current song as 'loved'
ban:               mark the current song as 'banned'
tag :         change to a 'global tag' radio.
artist :   change to a 'similar artists' radio
group :     change to a 'last.fm group' radio
loved :      change to a 'loved' radio for a specific user
neighbours : change to a 'neighbours' radio for a specific user
personal :   change to a 'personal' radio for a specific user
playlist :   change to a 'playlist' radio for a specific user
playurl :     just play the specified URL on Vagalume
volumeup [INC]:    increase playback volume
volumedown [INC]:  decrease playback volume
volume :    set the playback volume to a specific value
start:             start Vagalume (if not already running)
close:             close Vagalume (if not already closed)
help:              print this information

Double quotes are REQUIRED when specifying parameters to some commands,
such as TAG or ARTIST, because of the white spaces they might contain, e.g:

$ vagalumectl tag "hard rock"
$ vagalumectl artist "Led Zeppelin"

mario@bender:~$ vagalumectl loved homemaxico
Command 'loved' successfully executed
mario@bender:~$</blockquote>
Well... perhaps not a too much useful 'screenshot' after all... but believe me, that's the proof that D-Bus is working fine on my GNOME desktop from now on.

I hope you can enjoy the patch soon (as soon as <a title="Berto's blog" href="https://blogs.igalia.com/berto">Berto</a> applies it to the <em>SVN trunk</em>)... perhaps in <a title="Vagalume web site" href="http://vagalume.igalia.com">Vagalume</a> 0.7 ;-), who knows...
