---
title: On Linux32 chrooted environments
date: '2015-07-03T15:31:31+00:00'
slug: on-linux32-chrooted-environments
categories:
- Debian
- Planet GNOME
- Planet GPUL
- Planet WebKitGTK
- Planeta GNOME Hispano
- Systems
- Tips
- WebKit
- WebKit2
- WebKitGTK
- Tools
wp_id: 2030
---

I have a chrooted environment in my 64bit Fedora 22 machine that I use every now and then to work on a debian-like 32bit system where I might want to do all sorts of things, such as building software for the target system or creating debian packages. More specifically, today I was trying to build WebKitGTK+ 2.8.3 in there and something weird was happening:

The following CMake snippet was <strong>not</strong> properly recognizing my 32bit chroot:
<pre>
string(TOLOWER ${CMAKE_HOST_SYSTEM_PROCESSOR} LOWERCASE_CMAKE_HOST_SYSTEM_PROCESSOR)
if (CMAKE_COMPILER_IS_GNUCXX AND "${LOWERCASE_CMAKE_HOST_SYSTEM_PROCESSOR}" MATCHES "(i[3-6]86|x86)$")
    ADD_TARGET_PROPERTIES(WebCore COMPILE_FLAGS "-fno-tree-sra")
endif ()
</pre>

After some investigation, I found out that <code>CMAKE_HOST_SYSTEM_PROCESSOR</code> relies on the output of <code>uname</code> to determine the type of the CPU, and this what I was getting if I ran it myself:
<pre>
(debian32-chroot)mario:~ $ uname -a
Linux moucho 4.0.6-300.fc22.x86_64 #1 SMP Tue Jun 23 13:58:53 UTC 2015
x86_64 x86_64 x86_64 GNU/Linux
</pre>

Let's avoid nasty comments about the stupid name of my machine (I'm sure everyone else uses clever names instead), and see what was there: <strong>x86_64</strong>.

That looked <strong>wrong</strong> to me, so I googled a bit to see what others did about this and, besides finding all sorts of crazy hacks around, I found that in my case the solution was pretty simple just because I am using <a href="https://wiki.debian.org/Schroot">schroot</a>, a great tool that makes life easier when working with chrooted environments.

Because of that, all I would have to do would be to specify <code>personality=linux32</code> in the configuration file for my chrooted environment and that's it. Just by doing that and re-entering in the "jail", the output would be much saner now:
<pre>
(debian32-chroot)mario:~ $ uname -a
Linux moucho 4.0.6-300.fc22.x86_64 #1 SMP Tue Jun 23 13:58:53 UTC 2015
i686 i686 i686 GNU/Linux
</pre>

And of course, WebKitGTK+ would now recognize and use the right CPU type in the snippet above and I could "relax" again while seeing WebKit building again.

Now, for extra reference, this is the content of my schroot configuration file:
<pre>
$ cat /etc/schroot/chroot.d/00debian32-chroot
[debian32-chroot]
description=Debian-like chroot (32 bit) 
type=directory
directory=/schroot/debian32/
users=mario
groups=mario
root-users=mario
personality=linux32
</pre>

That is all, hope somebody else will find this useful. It certainly saved my day!
