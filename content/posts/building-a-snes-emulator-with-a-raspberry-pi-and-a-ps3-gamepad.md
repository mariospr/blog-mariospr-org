---
title: Building a SNES emulator with a Raspberry Pi and a PS3 gamepad
date: '2015-03-26T03:46:55+00:00'
slug: building-a-snes-emulator-with-a-raspberry-pi-and-a-ps3-gamepad
categories:
- Personal
- Planet GNOME
- Planet GPUL
- Planeta GNOME Hispano
- RaspberryPi
- Emulators
wp_id: 1734
---

It's been a while since I did this, but I got some people asking me lately about how exactly I did it and I thought it could be nice to write a post answering that question. Actually, it would be a nice thing for me to have anyway at least as "documentation", so here it is.

But first of all, <strong>the idea</strong>: my personal and very particular goal was to have a proper SNES emulator plugged to my TV, based on the Raspberry Pi (simply because I had a spare one) that I could control entirely with a gamepad (no external keyboards, no <em>ssh</em> connection from a laptop, nothing).

Yes, I know there are other emulators I could aim for and even Raspberry specific distros designed for a similar purpose but, honestly, I don't really care about MAME, NeoGeo, PSX emulators or the like. I simply wanted a SNES emulator, period. And on top of that I was quite keen on playing a bit with the Raspberry, so I took this route, for good or bad.

Anyway, after doing some investigation I realized all the main pieces were already out there for me to build such a thing, all that was needed was to put them all together, so I went ahead and did it. And these are the HW &amp; SW ingredients involved in this recipe:
<ul>
	<li>A <a title="Raspberry Pi Model B" href="http://www.raspberrypi.org/product/model-b/">Raspberry Pi Model B</a> (or better) with <a title="Raspbian" href="http://www.raspbian.org/">Raspbian</a> installed</li>
	<li>A <a title="Cheap £10 Bluetooth dongle" href="http://www.maplin.co.uk/p/nikkai-mini-bluetooth-20-dongle-a63hy">Bluetooth 2.0 dongle</a></li>
	<li>A <a title="PS3 DualShock 3 gamepad" href="http://en.wikipedia.org/wiki/DualShock#DualShock_3">PS3 DualShock 3</a> gamepad</li>
	<li><a title="QtSixA" href="http://qtsixa.sourceforge.net/">QtSixA</a>: a joystick manager for PS3's SixAxis gamepads</li>
	<li><a title="PiSNES" href="https://code.google.com/p/pisnes/">PiSNES</a>: A SNES emulator for the Raspberry Pi, based on SNES9X 1.39</li>
</ul>
Once I got all these things around, this is how I assembled the whole thing:

<strong>1.</strong> Got the gamepad paired and recognized as a joystick under <em>/dev/input/js0</em> using the <a title="QtSixA" href="http://qtsixa.sourceforge.net/">QtSixA</a> project. I followed the <a title="Installing a PS3 DualShock controller in the Raspberry Pi" href="http://www.raspians.com/Knowledgebase/ps3-dualshock-controller-install-on-the-raspberry-pi/">instructions here</a>, which explain fairly well how to use <em>sixpair</em> to pair the gamepad and how to get the <em>sixad</em> daemon running at boot time, which was an important requirement for this whole thing to work as I wanted it to.

<strong>2.</strong> I downloaded the source code of <a title="PiSNES" href="https://code.google.com/p/pisnes/">PiSNES</a>, then patched it slightly so that it would <a title=" Recognize the Dual Shock 3 as a valid pad, even if it has more than 6… " href="https://github.com/mariospr/pisnes/commit/d6c64e93157c0c9d5fd7abd633abd1e6f65f05dd">recognize the PS3 DualShock gamepad</a>, <a title="Allow defining the four directions of the joystick using the configuration file" href="https://github.com/mariospr/pisnes/commit/accdf4bb05af2a62ed78572ad4f0e2ffca20a855">allow me define the four directions of the joystick through the configuration file</a>, among <a title="My local modifications to PiSNES" href="https://github.com/mariospr/pisnes/commits/my-local-setup">other things</a>.

<strong>3.</strong> I had no idea how to get the PS3 gamepad paired automatically when booting the Raspberry Pi, so I wrote a stupid small script that would basically wait for the gamepad to be detected under <em>/dev/input/js0</em>, and then launch the snes9x.gui GUI to choose a game from the list of ROMS available. I placed it under <em>/usr/local/bin/snes-run-gui</em>, and looks like this:
<pre>#!/bin/bash

BASEDIR=/opt/pisnes

# Wait for the PS3 Game pad to be available
while [ ! -e /dev/input/js0 ]; do sleep 2; done

# The DISPLAY=:0 bit is important for the GUI to work
DISPLAY=:0 $BASEDIR/snes9x.gui
</pre>
<strong>4.</strong> Because I wanted that script to be launched on boot, I simply added a line to <em>/etc/xdg/lxsession/LXDE/autostart</em>, so that it looked like this:
<pre>@lxpanel --profile LXDE
@pcmanfm --desktop --profile LXDE
@xscreensaver -no-splash
@/etc/sudoers.d/vsrv.sh
@/usr/local/bin/snes-run-gui
</pre>
By doing the steps mentioned above, I got the following <em>"User Experience":</em>
<ol>
	<li>Turn on the RPi by simply plugging it in</li>
	<li>Wait for Raspbian to boot and for the desktop to be visible</li>
	<li>At this point, both the <em>sixad</em> daemon and the <em>snes-run-gui</em> script should be running, so press the PS button in the gamepad to connect the gamepad</li>
	<li>After a few seconds, the lights in the gamepad should stop blinking and the <em>/dev/input/js0</em> device file should be available, so <em>snes9x.gui</em> is launched</li>
	<li>Select the game you want to play and press with the <em>'X'</em> button to run it</li>
	<li>While in the game, press the PS button to get back to the game selection UI</li>
	<li>From the game selection UI, press <em>START+SELECT</em> to shutdown the RPi</li>
	<li>Profit!</li>
</ol>
Unfortunately, those steps above were enough to get the gamepad paired and working with PiSNES, but my TV was a bit tricky and I needed to do a few adjustments more in the booting configuration of the Raspberry Pi, which took me a while to find out too.

So, here is the contents of my <em>/boot/config.txt</em> file in case it helps somebody else out there, or simply as reference (more info about the contents of this file in <a title="RPiConfig" href="http://elinux.org/RPiconfig">RPiConfig</a>):
<pre># NOOBS Auto-generated Settings:
hdmi_force_hotplug=1
config_hdmi_boost=4
overscan_left=24
overscan_right=24
overscan_top=16
overscan_bottom=16
disable_overscan=0
core_freq=250
sdram_freq=500
over_voltage=2

# Set sdtv mode to PAL (as used in Europe)
sdtv_mode=2

# Force sound to be sent over the HDMI cable
hdmi_drive=2

# Set monitor mode to DMT
hdmi_group=2

# Overclock the CPU a bit (700 MHz is the default)
arm_freq=900

# Set monitor resolution to 1280x720p @ 60Hz XGA
hdmi_mode=85
</pre>
As you can imagine, some of those configuration options are specific to the TV I have it connected to (e.g. <em>hdmi_mode</em>), so YMMV. In my case I actually had to try different HDMI modes before settling on one that would simply work, so if you are ever in the same situation, you might want to <em>apt-get install</em> <em>libraspberrypi-bin</em> and use the following commands as well:
<pre> $ tvservice -m DMT # List all DMT supported modes
 $ tvservice -d edid.dat # Dump detailed info about your screen
 $ edidparser edid.dat | grep mode # List all possible modes</pre>
In my case, I settled on <em>hdmi_mode=85</em> simply because that's the one that work better for me, which stands for the <em>1280x720p@60Hz</em> DMT mode, according to <em>edidparser</em>:
<pre>HDMI:EDID DMT mode (85) 1280x720p @ 60 Hz with pixel clock 74 MHz has a score of 80296
</pre>
And that's all I think. Of course there's a chance I forgot to mention something because I did this in my random slots of spare time I had back in July, but that should be pretty much it.

Now, simply because this post has been too much text already, here you have a video showing off how this actually works (and let alone how good/bad I am playing!):
<p style="text-align: center;"><iframe src="https://www.youtube.com/embed/e30DJ2Ym9Ow" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe></p>
<p style="text-align: center;"><a title="Video: Raspberry Pi + PS3 Gamepad + PiSNES" href="https://www.youtube.com/watch?v=e30DJ2Ym9Ow">Video: Raspberry Pi + PS3 Gamepad + PiSNES</a></p>
I have to say I had great fun doing this and, even if it's a quite hackish solution, I'm pretty happy with it because it's been so much fun to play those games again, and also because it's been working like a charm ever since I set it up, more than half a year ago.

And even better... turns out I got it working just in time for "Father's Day", which made me win the "best dad in the world" award, unanimously granted by my two sons, who also enjoy playing those good old games with me now (and beating me on some of them!).

Actually, that has been certainly the most rewarding thing of all this, no doubt about it.
