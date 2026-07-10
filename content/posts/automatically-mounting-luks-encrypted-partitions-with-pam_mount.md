---
title: Automatically mounting LUKS encrypted partitions with pam_mount
date: '2008-03-08T12:43:04+00:00'
slug: automatically-mounting-luks-encrypted-partitions-with-pam_mount
categories:
- GNOME
- Planet GNOME
- Planet GPUL
- Planet Igalia
- Systems
wp_id: 22
url: /2008/03/08/automatically-mounting-luks-encrypted-partitions-with-pam_mount/
---

Yesterday I've got my new Thinkpad T61 laptop and I had to spend some time installing a GNU/Linux distribution on it, so doing all those related tasks that are a must: partitioning, installing linux, installing emacs... and besides to all those tasks <strong>a very important one</strong>: encrypting some disk partitions.

To do that, I just followed the instructions that <a title="Berto's blog" href="https://blogs.igalia.com/berto">Berto</a> had posted some months ago in his blog, either for <a title="Disk encryption in Linux (IV): Encrypting a full partition with LUKS" href="https://blogs.igalia.com/berto/2006/11/08/disk-encryption-in-linux-iv-encrypting-a-full-partition-with-luks/">encrypting full regular partitions with LUKS</a> as for <a title="Disk encryption in Linux (III): Encrypting temporary filesystems" href="https://blogs.igalia.com/berto/2006/11/03/disk-encryption-in-linux-iii-encrypting-temporary-filesystems/">encrypting temporary filesystems</a>, say, <strong>/tmp</strong> and <strong>swap</strong> partitions.

So, once I got those tasks done (quite easy if you follow the steps <a title="Berto's blog" href="https://blogs.igalia.com/berto">Berto</a>'s explained in his posts), only one more task was still left: to make those <a title="LUKS" href="http://luks.endorphin.org/">LUKS</a> encrypted partitions to be automatically mounted when logging into the system with my username.

The idea behind this is just that you use the <strong>same password</strong> both for logging into the system with your username as for decrypting those LUKS partitions before mounting them. To do this, I've just  used the <a title="pam_mount module" href="http://pam-mount.sourceforge.net/">pam_mount</a> module so it took care of using the user password to automatically mount those partitions right after the user gets identified in the system. And of course, that pam module also takes care of unmounting those partitions right after you log out and no open sessions with your username remains active.

So, I'd like to share with you a recipe to get all this stuff easily working:
<ol>
	<li>Follow the steps in <a title="Berto's blog" href="https://blogs.igalia.com/berto">Berto</a>'s post to <a title="Disk encryption in Linux (IV): Encrypting a full partition with LUKS" href="https://blogs.igalia.com/berto/2006/11/08/disk-encryption-in-linux-iv-encrypting-a-full-partition-with-luks/">encrypt a full partition with LUKS</a>.</li>
	<li>When you add a LUKS password for that encrypted partition, use the <strong>same password</strong> you use to log into your system with your username. LUKS allows you to add more than one password for your partitions, so at least one of them should be the same than your user password.</li>
	<li>Install the <a title="pam_mount module" href="http://pam-mount.sourceforge.net/">pam_mount</a> module:</li>
<blockquote>sudo apt-get install libpam-mount</blockquote>
	<li>Edit your /etc/security/pam_mount.conf file and append there a line like the following one (one for each encrypted partition you'd like to automatically mount):</li>
<blockquote>volume USERNAME crypt - DEV_FILE MOUNTPOINT - - -</blockquote>
For example, to mount a encripted partition present in /dev/sda6 under a /encrypted folder whenever the user 'mario' logs into the system, you should append the following line:
<blockquote>volume mario crypt - /dev/sda6 /encrypted - - -</blockquote>
	<li>Edit /etc/pam.d/login so it looks as follows at the end of the file</li>
<blockquote>[...]
# Standard Un*x account and session
@include common-account
@include common-session
@include common-pammount
@include common-password</blockquote>
	<li>And, if you use <a title="Gnome display manager" href="http://www.gnome.org/projects/gdm/">GDM</a> (as me), you should also edit /etc/pam.d/gdm in a similar way:</li>
<blockquote>[...]
@include common-account
session required        pam_limits.so
@include common-session
@include common-pammount
session optional        pam_gnome_keyring.so  auto_start
@include common-password</blockquote>
	<li>At last make sure that you have removed (or commented) some lines in /etc/fstab and /etc/crypttab, in order to avoid both asking for the LUKS password at startup (because the crypttab file) as trying to mount a not decrypted partition (because of fstab). For instance, this is how those files would look for the example given:</li>
<ol />
<ul>
	<li>/etc/crypttab:</li>
</ul>
<ol>
<blockquote>#encrypted /dev/sda6  none            luks,check=ext2
cswap   /dev/sda8   /dev/urandom    swap
ctmp    /dev/sda9    /dev/urandom    tmp</blockquote>
</ol>
<ul>
	<li>/etc/fstab:</li>
</ul>
<ol>
<blockquote>[...]
#/dev/mapper/encrypted     /encrypted  ext3    defaults        0       2
[...]</blockquote>
</ol>
</ol>
Once you have followed all those steps, you should be able to reboot and see how the encrypted partition gets mounted right after you login in your system, either by using GDM as by using a text-mode terminal.

And that's all. I hope you find it useful.
