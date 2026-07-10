---
title: Gaim stores passwords in plain text
date: '2006-06-27T20:00:05+00:00'
slug: gaim-stores-passwords-in-plain-text
categories:
- GNOME
- Planet GNOME
- Planet Igalia
wp_id: 248
---

Last afternoon I spent some time in the <a target="_blank" title="Lfcia" href="http://www.lfcia.org">Lfcia</a> talking to Miriam, and she told me about Gaim storing passwords in plain text. I had no idea of this before she told me, and that's why, as soon as I was warned about, I took a look into my ~/.gaim directory and I realized how my password was really stored in the <strong>accounts.xml</strong> text file.

The reason for my password to be there was that I'd checked the typical "Remember my password" checkbox when adding my IM accounts to gaim, with the only purpose of not being annoyed each time I login into my accounts. Somebody could say at this point that the only real security would be not storing passwords at all (and this is true, of course), but I think that if a program asks you for doing something like that, you should be able to trust it about how your password is going to be saved at disk (hopefully, in a secure way).

After thinking for a while, I <em>googled</em> a bit looking for information about this and to see if there's a plugin, a patch or something similar to fix this situation... and here is the final result of my search:

<a target="_blank" title="http://gaim.sourceforge.net/plaintextpasswords.php" href="http://gaim.sourceforge.net/plaintextpasswords.php">http://gaim.sourceforge.net/plaintextpasswords.php</a>.

In this URL, gaim developers tell that <em>gaim does not now and is not likely to encrypt the passwords in the  <code>accounts.xml</code> file, nor is it likely to be encrypted in a  future release</em>. "Hard declarations!", I thought ;)... but, after all, I think their arguments are not so bad, except that they are not taking into account a common situation when using gaim that makes unsafe storing passwords in the <em>accounts.xml</em> file (even when that file is only readable by its owner): what about using gaim on a computer whose <em>superuser</em> is not you? That <em>superuser</em> could read your <em>accounts.xml</em> file even when nobody but you couldn't, and that's not seem to be "pretty good privacy" :).

I know that gaim developers would say that I shouldn't use this feature in such those environments, but this means assuming gaim users know what's really happening when saving passwords, and this is not always true (just look at me :P). At least, I think showing an informative message warning the user about how his/her password is going to be stored could be a good thing in order to avoid this kind of surprises.

What do you think about?
