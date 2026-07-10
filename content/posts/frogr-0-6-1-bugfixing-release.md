---
title: Frogr 0.6.1 (bugfixing) release
date: '2011-08-19T19:18:10+00:00'
slug: frogr-0-6-1-bugfixing-release
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
wp_id: 552
---

Shit happens in many ways, and sometimes that means you release an application with some bugs you just can't stand and need to roll out a bugfixing release as soon as possible. Does this sound familiar to you? :)

So that's why this new release of frogr, just <a href="/2011/08/13/frogr-0-6-released/">one week after the 0.6 version had been published</a>, has arrived, taking care exclusively of fixing the following problems, as stated in the <a title="Frogr's NEWS file" href="http://git.gnome.org/browse/frogr/tree/NEWS">NEWS file</a>:
<ul>
	<li>﻿Fix memory leaks, the most important one happening in the editing details dialog.</li>
	<li>Problems using combo boxes with versions of GTK prior to 2.24.</li>
	<li>Fixed problems authorizing frogr on the MacOSX version.</li>
</ul>
From those above, patches for some them were already included in the debian packages from <a href="http://launchpad.net/~mariospr/+archive/frogr">frogr's Ubuntu PPA</a> and in the package for the Mac, but the most important ones -the leaks- were not, so that's why I decided to roll this new version out.

So that's all, if you were already an user of frogr, <a title="Get frogr" href="https://live.gnome.org/Frogr#Get_Frogr">go and grab it through the usual ways</a>.
