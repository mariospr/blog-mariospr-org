---
title: Frogr 1.1 released
date: '2016-10-05T01:24:36+00:00'
slug: frogr-1-1-released
categories:
- Debian
- Fedora
- frogr
- GNOME
- Planet GNOME
- Planet GPUL
- Planeta GNOME Hispano
- Ubuntu
- Flatpak
wp_id: 2225
---

After almost one year, I've finally <a href="https://mail.gnome.org/archives/frogr-list/2016-October/msg00000.html">released another small iteration of frogr</a> with a few updates and improvements.

<a href="/wp-content/uploads/2016/10/20161005-frogr-screenshot.png"><img class="aligncenter size-large wp-image-2226" src="/wp-content/uploads/2016/10/20161005-frogr-screenshot-600x338.png" alt="Screenshot of frogr 1.1" width="474" height="267" /></a>

Not many things, to be honest, bust just a few as I said:
<ul>
 	<li><strong>Added support for <a href="http://flatpak.org/">flatpak</a></strong>: it's now possible to authenticate frogr from inside the sandbox, as well as open pictures/videos in the appropriate viewer, thanks to the <em>OpenURI</em> <a href="https://github.com/flatpak/flatpak/wiki/Portals">portal</a>.</li>
 	<li><strong>Updated translations</strong>: as it was noted in the past when I released 1.0, several translations were left out incomplete back then. Hopefully the new version will be <a href="https://l10n.gnome.org/module/frogr/">much better</a> in that regard.</li>
 	<li><strong>Dropped</strong> the build dependency on <strong><em>intltool</em></strong> (requires <em>gettext</em> &gt;= 0.19.8).</li>
 	<li>A few <strong>bugfixes</strong> too and other maintenance tasks, as usual.</li>
</ul>
Besides, another significant difference compared to previous releases is related to the way I'm <strong>distributing</strong> it: in the past, if you used <a href="http://www.ubuntu.com/">Ubuntu</a>, you could configure <a href="https://launchpad.net/~mariospr/+archive/ubuntu/frogr/+packages">my PPA</a> and install it from there even in fairly old versions of the distro. However, this time that's only possible if you have Ubuntu 16.10 <em>"Yakkety Yak"</em>, as that's the one that ships g<em>ettext</em> &gt;= 0.19.8, which is required now that I removed all trace of intltool (more info in <a href="https://blogs.gnome.org/mclasen/2016/07/21/using-modern-gettext/">this post</a>).

However, this is also the first time I'm using <a href="http://flatpak.org/">flatpak</a> to distribute frogr so, regardless of which distribution you have, you can now install and run it as long as you have the <a class="http" href="http://flatpak.org/runtimes.html">org.gnome.Platform/x86_64/3.22 stable runtime </a>installed locally. Not too bad! :-). See more <a href="https://wiki.gnome.org/Apps/Frogr#Flatpak">detailed instructions in its web site</a>.

That said, it's <em>interesting</em> that you also have the <a href="https://github.com/flatpak/xdg-desktop-portal">portal frontend service</a> and a <a href="http://flatpak.org/runtimes.html">backend implementation</a>, so that you can authorize your flickr account using the browser outside the sandbox, via the <em>OpenURI</em> <a href="https://github.com/flatpak/flatpak/wiki/Portals">portal</a>. If you don't have that at hand, you can still used the sandboxed version of frogr, but you'd need to copy your configuration files from a non-sandboxed frogr (under <em>~/.config/frogr</em>) first, right into <em>~/.var/app/org.gnome.Frogr/config</em>, and then it should be usable again (opening files in external viewers would not work yet, though!).

So this is all, hope it works well and it's helpful to you. I've just finished uploading a few hundreds of pictures a couple of days ago and it seemed to work fine, but you never know... <em>devil is in the detail</em>!

&nbsp;
