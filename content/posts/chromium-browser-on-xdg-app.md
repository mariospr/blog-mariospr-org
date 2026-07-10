---
title: Chromium Browser on xdg-app
date: '2016-04-13T11:17:10+00:00'
slug: chromium-browser-on-xdg-app
categories:
- GNOME
- Hackfest
- Meetings and conferences
- Planet GNOME
- Planet GPUL
- Planeta GNOME Hispano
- Endless
- Chromium
- Flatpak
wp_id: 2135
---

Last week I had the chance to attend for 3 days the <a href="https://wiki.gnome.org/Hackfests/GnomeSoftware2016">GNOME Software Hackfest,</a> organized by <a href="https://blogs.gnome.org/hughsie">Richard Hughes </a>and hosted at the brand new <a href="https://www.redhat.com/en/about/office-locations">Red Hat's London office</a>.

And besides meeting new people and some old friends (which I admit to be one of my favourite aspects about attending these kind of events), and discovering what it's now <a href="http://boroughmarket.org.uk">my new favourite place for fast-food near London bridge</a>, I happened to learn quite a few new things while working on my particular personal quest: getting <a href="http://www.chromium.org/Home">Chromium browser</a> to run as an <a href="https://wiki.gnome.org/Projects/SandboxedApps">xdg-app</a>.

While this might not seem to be an immediate need for <a href="https://www.endlessm.com">Endless</a> right now (we currently ship a Chromium-based browser as part of our <a href="https://ostree.readthedocs.org/en/latest/">OSTree</a> based system), this was definitely something worth exploring as we are now implementing the next version of <a href="https://endlessm.com/press/endless_os_appstore_en/">our App Center </a>(which will be based on <a href="https://wiki.gnome.org/Apps/Software">GNOME Software</a> and <a href="https://wiki.gnome.org/Projects/SandboxedApps">xdg-app</a>). Chromium updates very frequently with fixes and new features, and so being able to update it separately and more quickly than the OS is very valuable.
<p style="text-align: center;"><a href="/wp-content/uploads/2016/04/Endless_OS_Appstore_EN.png"><img src="/wp-content/uploads/2016/04/Endless_OS_Appstore_EN-600x338.png" alt="Endless OS App Center" width="584" height="329" /></a>
Screenshot of Endless OS's current App Center</p>
So, while <a href="http://www.joaquimrocha.com/">Joaquim</a> and <a href="http://ramcq.net">Rob</a> were working on the GNOME Software related bits and discussing aspects related to <a href="https://build.gnome.org">Continuous Integration</a> with the rest of the crowd, I spent some time learning about xdg-app and trying to get Chromium to build that way which, unsurprisingly, was not an easy task.

Fortunately, the <a href="https://wiki.gnome.org/Projects/SandboxedApps">base documentation about xdg-app</a> together with <a href="https://blogs.gnome.org/alexl/2016/02/19/building-an-xdg-app-part-1">Alex Larsson's blog post series</a> about this topic (which I wholeheartedly recommend reading) and some experimentation from my side was enough to get started with the whole thing, and I was quickly on my way to fixing build issues, adding missing deps and the like.

Note that my goal at this time was <strong>not</strong> to get a fully featured Chromium browser running, but to get something running based on the version that we use use in Endless (Chromium 48.0.2564.82), with a couple of things disabled for now (e.g. chromium's own sandbox, udev integration...) and putting, of course, some holes in the xdg-app configuration so that Chromium can access the system's parts that are needed for it to function (e.g. network, X11, shared memory, pulseaudio...).

Of course, the long term goal is to close as many of those holes as possible using <a href="https://wiki.gnome.org/Projects/SandboxedApps/Sandbox">Portals</a> instead, as well as not giving up on Chromium's own sandbox right away (some work will be needed here, since `setuid` binaries are a no-go in xdg-app's world), but for the time being I'm pretty satisfied (and kind of surprised, even) that I managed to get the whole beast built and running after 4 days of work since I started :-).

But, as <a href="https://siliconislandblog.wordpress.com/">Alberto</a> usually says... "screencast or it didn't happen!", so I recorded a video yesterday to properly share my excitement with the world. Here you have it:
<p style="text-align: center;"><iframe src="https://www.youtube.com/embed/euwSnOm89hM" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe>
[<a href="https://www.youtube.com/watch?v=euwSnOm89hM">VIDEO: Chromium Browser running as an xdg-app</a>]</p>
As mentioned above, this is <em>work-in-progress</em> stuff, so please hold your horses and manage your expectations wisely. It's not quite there yet in terms of what I'd like to see, but definitely a step forward in the right direction, and something I hope will be useful not only for us, but for the entire Linux community as a whole. Should you were curious about the current status of the whole thing, feel free to check the relevant files at <a href="https://github.com/mariospr/chromium-browser-xdg-app">its git repository here</a>.

Last, I would like to finish this blog post saying thanks specially to <a href="https://blogs.gnome.org/hughsie">Richard Hughes</a> for organizing this event, as well as the <a href="https://www.gnome.org/foundation/">GNOME Foundation</a> and <a href="http://www.redhat.com/">Red Hat</a> for their support in the development of <a href="https://wiki.gnome.org/Apps/Software">GNOME Software</a> and <a href="https://wiki.gnome.org/Projects/SandboxedApps">xdg-app</a>. Finally, I'd also like to thank my employer <a href="https://www.endlessm.com">Endless</a> for supporting me to attend this hackfest. It's been a terrific week indeed... thank you all!

<img src="https://feaneron.files.wordpress.com/2016/02/banner-down.png?w=810" alt="Credit to Georges Stavracas" align="middle" />
<p style="text-align: center;">Credit to <a href="https://feaneron.com/home/blog">Georges Stavracas</a></p>
