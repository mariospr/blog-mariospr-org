---
title: Frogr 1.4 released
date: '2017-12-28T02:45:24+00:00'
slug: frogr-1-4-released
categories:
- frogr
- GNOME
- Planet GNOME
- Planet GPUL
- Planeta GNOME Hispano
- Flatpak
wp_id: 2476
---

Another year goes by and, again, I <em>feel the call</em> to make one more release just before 2017 over, so here we are: <a href="https://mail.gnome.org/archives/gnome-announce-list/2017-December/msg00009.html">frogr 1.4 is out!</a>

<a href="/wp-content/uploads/2017/12/20171228-frogr-screenshot.png"><img class="aligncenter size-large wp-image-2501" src="/wp-content/uploads/2017/12/20171228-frogr-screenshot-600x375.png" alt="Screenshot of frogr 1.4" width="600" height="375" /></a>

Yes, I know what you're thinking: <em>"Who uses Flickr in 2017 anyway?"</em>. Well, as shocking as this might seem to you, it is apparently not just me who is using this small app, but also another <b id="yui_3_11_0_1_1514425191744_315">8,935 users</b> out there issuing an average of 0.22 Queries Per Second every day (<strong>19008 queries a day</strong>) for the past year, according to the stats provided by Flickr for the API key.

Granted, it may be not a huge number compared to what other online services might be experiencing these days, but for me this is enough motivation to keep the little green frog working and running, thus worth updating it one more time. Also, I'd argue that these numbers for a niche app like this one (aimed at users of the Linux desktop that still use Flickr to upload pictures in 2017) do not even look too bad, although without more specific data backing this comment this is, of course, just my personal and highly-biased opinion.

So, what's new? Some small changes and fixes, along with other less visible modifications, but still relevant and necessary IMHO:
<ul>
 	<li>Fixed integration with GNOME Software (fixed a bug regarding <em style="font-size: 1rem;">appstream</em><span style="font-size: 1rem;"> data).</span></li>
 	<li>Fixed errors loading images from certain cameras &amp; phones, such as the OnePlus 5.</li>
 	<li>Cleaned the code by finally migrating to using <em>g_auto</em>, <em>g_autoptr</em> and <em>g_autofree</em>.</li>
 	<li>Migrated to the meson build system, and removed all the autotools files.</li>
 	<li>Big update to translations, now with more than 22 languages 90% - 100% translated.</li>
</ul>
Also, this is the first release that happens after having a fully operational centralized place for <a href="https://flatpak.org/">Flatpak</a> applications (aka <a href="https://flathub.org/">Flathub</a>), so I've <a href="https://github.com/flathub/org.gnome.frogr/commit/cc48dcb30ec472c5182ea9083fa242f178348c02">updated the manifest</a> and I'm happy to say that frogr 1.4 is already available for <em>i386</em>, <em>arm</em>, <em>aarch64</em> and <em>x86_64</em>. You can install it either from <a href="https://wiki.gnome.org/Apps/Software">GNOME Software</a> (details on how to do it at <em><a href="https://flathub.org">https://flathub.org</a></em>), or from the command line by just doing this:
<pre>flatpak install --from https://flathub.org/repo/appstream/org.gnome.frogr.flatpakref</pre>
Also worth mentioning that, starting with Frogr 1.4, I will no longer be updating my <a href="https://launchpad.net/~mariospr/+archive/ubuntu/frogr">PPA at Launchpad</a>. I did that in the past to make it possible for Ubuntu users to have access to the latest release ASAP, but now we have Flatpak that's a much better way to install and run the latest stable release in any supported distro (not just Ubuntu). Thus, I'm dropping the extra work required to deal with the PPA and flat-out recommending users to use Flatpak or wait until their distro of choice packages the latest release.

And I think this is everything. As usual, feel free to check the <a style="font-size: 1rem;" href="https://wiki.gnome.org/Apps/Frogr">main website</a><span style="font-size: 1rem;"> for extra information on </span><a style="font-size: 1rem;" href="https://wiki.gnome.org/Apps/Frogr#Get_Frogr">how to get frogr</a><span style="font-size: 1rem;"> and/or </span><a style="font-size: 1rem;" href="https://wiki.gnome.org/Apps/Frogr#Get_Involved">how to contribute to it</a><span style="font-size: 1rem;">. Feedback and/or help is more than welcome.</span>

Happy new year everyone!
