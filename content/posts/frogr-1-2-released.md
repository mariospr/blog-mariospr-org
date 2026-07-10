---
title: Frogr 1.2 released
date: '2016-10-05T13:46:49+00:00'
slug: frogr-1-2-released
categories:
- Debian
- frogr
- GNOME
- Planet GNOME
- Planet GPUL
- Planeta GNOME Hispano
- Ubuntu
- Flatpak
wp_id: 2237
---

Of course, just a few hours after <a href="/2016/10/05/frogr-1-1-released/">releasing frogr 1.1</a>, I've noticed that there was actually no good reason to depend on <em>gettext</em> 0.19.8 for the purposes of removing the <em>intltool</em> dependency only, since 0.19.7 would be enough.

So, as raising that requirement up to 0.19.8 was causing trouble to package frogr for some distros still in 0.19.7 (e.g. <a href="http://packages.ubuntu.com/xenial/gettext">Ubuntu 16.04 LTS</a>), I've decided to do a quick new release and frogr <a href="https://mail.gnome.org/archives/frogr-list/2016-October/msg00001.html">1.2 is now out with that only change</a>.

One direct consequence is that you can now install the <a href="https://launchpad.net/%7Emariospr/+archive/ubuntu/frogr/+packages">packages for Ubuntu from my PPA</a> if you have Ubuntu Xenial 16.04 LTS or newer, instead of having to wait for Ubuntu Yakkety Yak (yet to be released). Other than that 1.2 is <strong>exactly</strong> the same than 1.1, so you probably don't want to package it for your distro if you already did it for 1.1 without trouble. Sorry for the noise.

&nbsp;
