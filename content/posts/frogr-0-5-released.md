---
title: Frogr 0.5 released
date: '2011-05-27T12:24:17+00:00'
slug: frogr-0-5-released
categories:
- frogr
- GNOME
- Planet GNOME
- Planet GPUL
- Planet Igalia
- Planeta GNOME Hispano
- Ubuntu
wp_id: 510
---

Now announcing that the new release of <a title="Frogr" href="https://live.gnome.org/Frogr">frogr</a> is finally out.

This time, I'm afraid you won't find huge changes in the application, but a bunch of small improvements instead, in the way of subtle -yet handy- new features, bug fixes and new and uptaded translations mainly. Still, I can mention some of the new small features that I specially like, since I use it a lot:
<ul>
	<li>Uploading pictures stored in remote machines via well-known protocols like smb, ssh, ftp... well anything supported by <a title="GVFS" href="http://developer.gnome.org/gio/stable/GVfs.html">GVFS</a>, basically.</li>
	<li>Sort pictures in the interface by title and date taken (and keep the pictures sorted as you add more pictures!).</li>
	<li>Allow disabling tags autocompletion (seems to slow frogr down when you have thousands of tags).</li>
	<li>Tooltips with basic info about the pictures in the icon view (title, size, date taken).</li>
	<li>Show the total amount of data to be uploaded in the status bar.</li>
	<li>Allow filling the details for pictures right from the photoset details, when creating a new one.</li>
	<li>Correct picture orientation in the icon view, if needed (rotation).</li>
	<li>Support both for Gtk+2 and Gtk+3 (now this is the default toolkit for building).</li>
	<li>Support for generating <a title="MacOSX" href="http://en.wikipedia.org/wiki/Macosx">MacOSX</a> packages, thanks to <a title="GTK-OSX" href="http://gtk-osx.sourceforge.net">the GTK-OSX project</a>.</li>
	<li>As usual, several other bug fixes, improvements and nitpicky stuff.</li>
</ul>
As usual, you can get it through different ways:
<ul>
	<li>Source code: clone from <a title="Frogr's git repository" href="http://git.gnome.org/browse/frogr">the git repository at gnome.org</a>.</li>
	<li>Tarballs: both in <a title="frogr-0.5.tar.xz" href="http://download.gnome.org/sources/frogr/0.5/frogr-0.5.tar.xz">xz</a> and <a title="frogr-0.5.tar.bz2" href="http://download.gnome.org/sources/frogr/0.5/frogr-0.5.tar.bz2">bzip2</a> formats.</li>
	<li>Pre-compiled packages for <a title="The Fedora Project" href="http://www.fedoraproject.org">Fedora</a>: at <a title="Frogr packages for Fedora" href="http://people.gnome.org/~mario/files/frogr/fedora" target="_blank">my personal public folder in gnome.org</a>.</li>
	<li>For the specific case of <a title="Ubuntu Linux" href="http://www.ubuntu.com">Ubuntu</a> you can use <a title="Frogr PPA at launchpad" href="http://launchpad.net/~mariospr/+archive/frogr">this PPA at LaunchPad</a>.</li>
	<li><a title="MacOSX" href="http://en.wikipedia.org/wiki/Macosx">MacOSX</a> packages (Intel) in the <a title="MacOSX package of frogr (Intel)" href="//ftp.gnome.org/pub/GNOME/binaries/mac/frogr/frogr-0.5.macosx.intel.dmg">GNOME FTP server</a> (experimental, yet ready for everyday use)</li>
</ul>
<em><strong>[Update 31/05/2011]: </strong>If you have <strong>already installed frogr 0.5</strong> for Ubuntu from my PPA or from the pre-compiled packages, <strong>please do upgrade</strong> to the latest version of the Ubuntu packages <strong>a</strong><strong>s soon as possible</strong>, as available <a title="Frogr packages at Frogr's PPA" href="https://launchpad.net/~mariospr/+archive/frogr/+packages">in my PPA</a>. If you already have the PPA configured in your system, you can upgrade just frogr by simply doing this:</em>
<blockquote><em>sudo apt-get update &amp;&amp; sudo install frogr</em></blockquote>
<em>There was a problem with the generation of the previous version of the packages for Ubuntu (files being installed under /tmp/frogr, instead of /usr/share) and all of them are broken and need to be updated. <em>Sorry for the hassle.</em></em>

If you want to contribute, remember you can do it by proposing ideas, <a title="Frogr module at l10n.gnome.org" href="http://l10n.gnome.org/module/frogr/">translating</a>, <a title="Frogr's git repository" href="http://git.gnome.org/browse/frogr">coding</a>, <a title="Frogr's mailing list" href="http://mail.gnome.org/mailman/listinfo/frogr-list">discussing</a> or <a title="File new bugs for Frogr" href="https://bugzilla.gnome.org/enter_bug.cgi?product=frogr">filing</a> and/or <a title="Frogr's list of bugs" href="https://bugzilla.gnome.org/browse.cgi?product=frogr">fixing</a> bugs.

Also if you want to see <a title="Frogr" href="https://live.gnome.org/Frogr">frogr</a> packaged for your favourite distro and can help with that (maybe you're a packager or know better than me the required steps for that), that would be awesome. At the moment only <a title="Debian" href="http://www.debian.org">Debian</a> has packaged it so far that I know of (thanks <a title="Berto's blog" href="https://blogs.igalia.com/berto">Berto</a>!), but I would love to see it also in other distros (specially in <a title="The Fedora Project" href="http://www.fedoraproject.org">Fedora</a>, which is what I currently use) so more people can use it without having to use either <a title="My PPA at launchpad" href="http://launchpad.net/~mariospr/+archive/frogr">the Frogr PPA</a> or <a title="Frogr website: downloads" href="http://people.gnome.org/~mario/files/frogr" target="_blank">the homegrown packages I usually prepare with each release</a>.

For more information, just check out <a title="Frogr's web site" href="http://live.gnome.org/Frogr">its web site</a>. Here you have a screenshot of how <a title="Frogr" href="https://live.gnome.org/Frogr">frogr 0.5</a> looks in the awesome <a title="GNOME 3: Made of Easy" href="http://gnome3.org/">GNOME 3</a> in my <a title="The Fedora Project" href="http://www.fedoraproject.org">Fedora</a> box:

<a href="/wp-content/uploads/2011/05/20110527-frogr-0.5-screenshot.png"><img class="aligncenter" src="/wp-content/uploads/2011/05/20110527-frogr-0.5-screenshot-thumb.png" alt="Frogr 0.5 running in GNOME 3" width="520" height="325" /></a>
