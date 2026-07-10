---
title: Bringing sanity back to my T440s
date: '2015-03-30T03:32:32+00:00'
slug: bringing-sanity-back-to-my-t440s
categories:
- Fedora
- Planet GNOME
- Planet GPUL
- Planeta GNOME Hispano
- Tools
wp_id: 1901
---

As a long time Thinkpad's trackpoint user and owner of a Lenovo T440s, I always felt quite frustrated with the clickpad featured in this laptop, since it basically ditched away all the physical buttons I got so used to, and replace them all with a giant, weird and noisy "clickpad".

<a href="http://shop.lenovo.com/gb/en/laptops/thinkpad/t-series/t440s/"><img class=" aligncenter" src="https://www.lenovo.com/images/gallery/1060x596/lenovo-laptop-thinkpad-t440s-keyboard-zoom-3.jpg" alt="" width="583" height="357" /></a>

Fortunately, following <a title="X.Org synaptics support for the Lenovo T440, T540, X240, Helix, Yoga, X1 Carbon" href="http://who-t.blogspot.com.au/2014/03/xorg-synaptics-support-for-lenovo-t440.html">Peter Hutterer's post on X.Org Synaptics support for the T440</a>, I managed to get a semi-decent configuration where I basically disabled any movement in the touchpad and used it three giant soft buttons. It certainly took quite some time to get used to it and avoid making too many mistakes but it was at least usable thanks to that.

Then, just a few months ago from now, I learned about the new T450 laptops and how they introduced again the physical buttons for the trackpoint there... and felt happy and upset at the same time: happy to know that Lenovo finally reconsidered their position and decided to bring back some sanity to the legendary trackpoint, but upset because I realized I had bought the only Thinkpad to have ever featured such an insane device.

Luckily enough, I recently found that someone was selling this T450's new touchpads with the physical buttons in eBay, and people in many places seemed to confirm that it would fit and work in the T440, T440s and T440p (just google for it), so I decided to give it a try.

So, the <a href="https://twitter.com/mariospr/status/580020313020317696">new touchpad arrived here last week</a> and I did try to fit it, although I got a bit scared at some point and <a href="https://twitter.com/mariospr/status/580121079764639744">decided to step back and leave it for a while</a>. After all, this laptop is 7 months old and I did not want to risk breaking it either :-). But then I kept reading the <a title="T440s's Hardware Maintenance Manual " href="http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles_pdf/t440s_hmm_en_sp40a25360_01.pdf">T440s's Hardware Maintenance Manual</a> in my spare time and learned that I was actually closer than what I thought, so decided to give it a try this weekend again... and this is the final result:

<a href="/wp-content/uploads/2015/03/IMG_20150329_005436.jpg"><img class="aligncenter size-large wp-image-1902" src="/wp-content/uploads/2015/03/IMG_20150329_005436-600x450.jpg" alt="T440s with trackpoint buttons!" width="584" height="438" /></a>

Initially, I thought of writing a detailed step by step guide on how to do the installation, but in the end it all boils down to removing the system board so that you can unscrew the old clickpad and screw the new one, so you just follow the steps in the <a title="T440s's Hardware Maintenance Manual " href="http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles_pdf/t440s_hmm_en_sp40a25360_01.pdf">T440s's Hardware Maintenance Manual</a> for that, and you should be fine.

If any, I'd just add that you don't really need to remove the heatskink from the board, but just unplug the fan's power cord, and that you can actually do this without removing the board completely, but just lifting it enough to manipulate the 2 hidden screws under it. Also, I do recommend disconnecting all the wires connected to the main board as well as removing the memory module, the Wifi/3G cards and the keyboard. You can probably lift the board without doing that, but I'd rather follow those extra steps to avoid nasty surprises.

Last, please remember that this model has a built-in battery that you need to disable from the BIOS before starting to work with it. This is a new step compared to older models (therefore easy to overlook) and quite an important one, so make sure you don't forget about it!

Anyway, as you can see the new device fits perfectly fine in the hole of the former clickpad and it even gets recognized as a Synaptics touchpad, which is good. And even better, the touchpad works perfectly fine out of the box, with all the usual features you might expect: soft left and right buttons, 2-finger scrolling, tap to click...

The only problem is that the trackpoint's buttons would not work that well: the left and right buttons would translate into "scroll up" and "scroll down" and the middle button would simply not work at all. Fortunately, <a title="Lenovos X1 Carbon 3rd touchpad woes" href="http://who-t.blogspot.com.au/2015/01/lenovos-x1-carbon-3rd-touchpad-woes.html">this is also covered in Petter Hutterer's blog</a>, where he explains that all the problems I was seeing are expected at this moment, since some patches in the Kernel are needed for the 3 physical buttons to become visible via the trackpoint again.

But in any case, for those like me who just don't care about the touchpad at all, <a href="https://bugs.freedesktop.org/show_bug.cgi?id=88609#c10">this comment in the tracking bug for this issue</a> explains a workaround to get the physical trackpoint buttons working well right now (middle button included), simply by disabling the Synaptics driver and enabling <em>psmouse</em> configured to use the <em>imps</em> protocol.

And because I'm using Fedora 21, I followed the recommendation there and simply added <em>psmouse.proto=imps</em> to the <em>GRUB_CMDLINE_LINUX</em> line in <i>/etc/default/grub</i>, then run <em>grub2-mkconfig -o /boot/grub2/grub.cfg</em>, and that did the trick for me.

Now I went into the BIOS and disabled the "trackpad" option, not to get the mouse moving and clicking randomly, and finally enabled scrolling with the middle-button by creating a file in <em>/etc/X11/xorg.conf.d/20-trackpoint.conf</em> (based on the one from my old x201), like this:
<pre>Section "InputClass"
        Identifier "Trackpoint Wheel Emulation"
        MatchProduct "PS/2 Synaptics TouchPad"
        MatchDriver "evdev"
        Option  "EmulateWheel"  "true"
        Option  "EmulateWheelButton" "2"
        Option  "EmulateWheelInertia" "10"
        Option  "EmulateWheelTimeout" "190"
        Option  "Emulate3Buttons" "false"
        Option  "XAxisMapping"  "6 7"
        Option  "YAxisMapping"  "4 5"
EndSection
</pre>
So that's it. I suppose I will keep checking the <a href="https://bugs.freedesktop.org/show_bug.cgi?id=88609">status of the proper fix in the tracking bug</a> and eventually move to the Synaptic driver again once all those issue get fixed, but for now this setup is perfect for me, and definitely way better than what I had before.

I only hope that I hadn't forgotten to plug a cable when assembling everything back. At least, I can tell I haven't got any screw left and everything I've tested seems to work as expected, so I guess it's probably fine. Fingers crossed!
