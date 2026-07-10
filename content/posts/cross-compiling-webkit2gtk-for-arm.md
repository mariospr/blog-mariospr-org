---
title: Cross-compiling WebKit2GTK+ for ARM
date: '2016-09-30T19:10:56+00:00'
slug: cross-compiling-webkit2gtk-for-arm
categories:
- Hackfest
- Meetings and conferences
- Planet GNOME
- Planet GPUL
- Planet WebKitGTK
- Planeta GNOME Hispano
- Tips
- WebKit
- WebKit2
- WebKitGTK
- Endless
- Tools
wp_id: 2194
---

I haven't blogged in a while -mostly due to lack of time, as usual- but I thought I'd write something today to let the world know about one of the things I've worked on a bit during this week, while remotely attending the <a href="http://webengineshackfest.org/">Web Engines Hackfest</a> from home:
<p style="text-align: left;"><strong>Setting up an environment for cross-compiling <a href="https://webkitgtk.org/">WebKit2GTK+</a> for ARM</strong></p>
I know this is not new, nor ground-breaking news, but the truth is that I could not find any up-to-date documentation on the topic in a any public forum (the only one I found was this <a href="http://webkit.sed.hu/blog/20100419/webkitgtk-cross-compilation-arm">pretty old post from the time WebKitGTK+ used autotools</a>), so I thought I would devote some time to it now, so that I could save more in the future.

Of course, I know for a fact that many people use local recipes to cross-compile WebKit2GTK+ for ARM (or simply build in the target machine, which usually takes a looong time), but those are usually ad-hoc things and hard to reproduce environments locally (or at least hard for me) and, even worse, often bound to downstream projects, so I thought it would be nice to try to have something tested with upstream WebKit2GTK+ and publish it on <a href="https://trac.webkit.org">trac.webkit.org</a>,

So I spent some time working on this with the idea of producing some <a href="https://github.com/mariospr/webkit2gtk-ARM/blob/master/README.md">step-by-step instructions</a> including how to create a reproducible environment from scratch and, after some inefficient flirting with a VM-based approach (which <a href="https://github.com/mariospr/webkit2gtk-ARM/commit/94d035491c3edb0cb96c0300f3910915768edcf7">turned out to be insanely slow</a>), I finally settled on creating a chroot + provisioning it with a simple <a href="https://github.com/mariospr/webkit2gtk-ARM/blob/master/bootstrap.sh">bootstrap scrip</a>t + using a simple <a href="https://cmake.org/cmake/help/v3.6/manual/cmake-toolchains.7.html#cross-compiling-for-linux">CMake Toolchain file</a>, and that worked quite well for me.

In my fast desktop machine I can now get a full build of WebKit2GTK+ 2.14 (or trunk) in less than 1 hour, which is pretty much a productivity bump if you compare it to the approximately 18h that takes if I build it natively in the target ARM device I have :-)

Of course, I've <a href="https://trac.webkit.org/wiki/BuildingGtk#CrossCompilingforARMdevices">referenced this documentation in trac.webkit.org</a>, but if you want to skip that and go directly to it, I'm hosting it in a git repository here: <a href="https://github.com/mariospr/webkit2gtk-ARM">github.com/mariospr/webkit2gtk-ARM</a>.

Note that I'm not a CMake expert (nor even close) so the toolchain file is far from perfect, but it definitely does the job with both the 2.12.x and 2.14.x releases as well as with the trunk, so hopefully it will be useful as well for someone else out there.

Last, I want to thanks the <a href="http://www.webengineshackfest.org/#sponsors">organizers of this event</a> for making it possible once again (and congrats to <a href="https://www.igalia.com">Igalia</a>, which <a href="https://www.igalia.com/nc/igalia-247/news/item/igalia-celebrates-our-15th-anniversary/">just turned 15 years old</a>!) as well as to <a href="https://endlessm.com">my employer</a> for supporting me attending the hackfest, even if I could not make it in person this time.

<a href="https://endlessm.com/"><img class="aligncenter size-large wp-image-2195" src="/wp-content/uploads/2016/09/Endless_horizontal_2colors-600x92.png" alt="Endless Logo" width="584" height="90" /></a>
