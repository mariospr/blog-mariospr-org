---
title: Screen redrawing problems with the "nvidia" driver and Compiz
date: '2009-02-18T23:45:27+00:00'
slug: screen-redrawing-problems-with-the-nvidia-driver-and-compiz
categories:
- General
- Planet GPUL
- Planet Igalia
- Systems
- Tips
- Ubuntu
wp_id: 39
---

Just in case you were experiencing, like me, some very annoying problems with your NVIDIA graphic card while using Compiz, here you have a very useful option to put inside the "Device" section in your /etc/X11/xorg.org file:
<pre>Option         "UseCompositeWrapper" "true"</pre>
After activating this option (available for nvidia drivers &gt;= 169.xx) I found that the problems redrawing windows I was suffering, specially when scrolling (very annoying, for instance, when chatting through pidging), just dissapeared. And it was indeed a very annoying problem, since it used to happen very often and in almost any window (although not in Emacs ;-)) in my system, in a way so any information on it just got screwed up so it was completely unreadable... and the only "manual" workaround I had found so far was just to re-scroll the window or select the text I was trying to read, which seemed not to be a very good idea.

Needed to say that I started to see this odd behavior since I "downgraded" my Ubuntu 8.10 down to 8.04 last week (because of some very specific needs), and this strange problem never happened when using Intrepid, so if you're now using that version perhaps you can just throw this post away to the trash, because then it would not useful at all for you.

But just in case, here you are my two cents, and to make them even more useful, here you are the full configuration of my "Device" section in /etc/X11/xorg.conf, which allows me to use a fully accelerated desktop with no problems at all:
<pre>Section "Device"
&nbsp;&nbsp;&nbsp;&nbsp;Identifier     "Videocard0"
&nbsp;&nbsp;&nbsp;&nbsp;Driver         "nvidia"
&nbsp;&nbsp;&nbsp;&nbsp;VendorName     "NVIDIA Corporation"
&nbsp;&nbsp;&nbsp;&nbsp;BoardName      "Quadro NVS 140M"
&nbsp;&nbsp;&nbsp;&nbsp;Option         "AllowGLXWithComposite" "true"
&nbsp;&nbsp;&nbsp;&nbsp;Option         "UseCompositeWrapper" "true"
&nbsp;&nbsp;&nbsp;&nbsp;Option         "XAANoOffscreenPixmaps"
&nbsp;&nbsp;&nbsp;&nbsp;Option         "NoLogo" "true"
&nbsp;&nbsp;&nbsp;&nbsp;Option         "backingstore" "true"
&nbsp;&nbsp;&nbsp;&nbsp;Option         "TripleBuffer" "true"
&nbsp;&nbsp;&nbsp;&nbsp;Option         "AddARGBGLXVisuals"  "true"
EndSection</pre>
Hope this will be useful for you as well :-).

<strong>Update:</strong> If you're still suffering these problems even after adding these lines to xorg.conf, you could try to install the nvidia driver through <a title="Envy" target="_blank" href="http://albertomilone.com/nvidia_scripts1.html">Envy</a>. These steps worked for me (at the end, the annoying problem appeared again, although not so often than before):
<ol>
	<li>Uninstall any other driver you had installed before (through the ubuntu "restricted drivers" manager, or the .run script downloaded from nvidia.com).</li>
	<li>Install <a title="Envy" target="_blank" href="http://albertomilone.com/nvidia_scripts1.html">Envy</a>: <em>apt-get install envyng-core
</em></li>
	<li>Shutdown X and install the nvidia driver <strong>from a tty terminal</strong>: <em>envyng -t</em></li>
</ol>
After following these steps, and the simple instructions on screen, by ubuntu hardy perfectly booted up with the nvidia driver v173.14, which seems not to present the same problem.

Let's see if these new advice helps you too :-)
