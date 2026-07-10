---
title: Frogr 1.0 released
date: '2015-12-30T06:04:21+00:00'
slug: frogr-1-0-released
categories:
- Debian
- Fedora
- frogr
- GNOME
- Planet GNOME
- Planet GPUL
- Planeta GNOME Hispano
- Ubuntu
wp_id: 2112
---

I've just <a href="https://mail.gnome.org/archives/frogr-list/2015-December/msg00000.html">released frogr 1.0</a>. I can't believe it took me 6 years to move from the 0.x series to the 1.0 release, but here it is finally. For good or bad.

<a href="/wp-content/uploads/2015/12/20151230-frogr-screenshot.png"><img class="aligncenter size-large wp-image-2113" src="/wp-content/uploads/2015/12/20151230-frogr-screenshot-600x338.png" alt="Screenshot of frogr 1.0" width="584" height="329" /></a>This release is again a small increment on top of the previous one that fixes a few bugs, should make the UI look a bit more consistent and "modern", and includes some cleanups at the code level that I've been wanting to do for some time, like using <a href="https://developer.gnome.org/gobject/unstable/gobject-Type-Information.html#G-DECLARE-FINAL-TYPE:CAPS">G_DECLARE_FINAL_TYPE</a>, which helped me get rid of ~1.7K LoC.

Last, I've created a few <a href="https://launchpad.net/~mariospr/+archive/ubuntu/frogr/+packages">packages for Ubuntu in my PPA</a> that you can use now already if you're in Vivid or later while it does not get packaged by the distro itself, although I'd expect it to be eventually <a href="https://wiki.gnome.org/Apps/Frogr#Binary_packages">available via the usual means in different distros</a>, hopefully soon. For extra information, just take a look to <a href="https://wiki.gnome.org/Apps/Frogr#Binary_packages">frogr's website at live.gnome.org</a>.

Now remember to take lots of pictures so that you can upload them with <a href="https://wiki.gnome.org/Apps/Frogr">frogr</a> :)

Happy new year!
