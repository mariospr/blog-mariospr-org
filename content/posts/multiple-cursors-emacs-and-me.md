---
title: Multiple cursors, Emacs and me
date: '2013-03-23T14:41:59+00:00'
slug: multiple-cursors-emacs-and-me
categories:
- Planet GNOME
- Planet GPUL
- Planeta GNOME Hispano
- Tips
- Emacs
- TextEditors
- Tools
wp_id: 1514
---

It's been 7 years already since I started using <a href="http://www.gnu.org/software/emacs/">Emacs</a> and, for some reason, I still haven't found a text editor I do feel more comfortable with, and I Swear to Gods I've tried. I really did. And as proof, I can tell that <a title="Berto's blog" href="https://blogs.igalia.com/berto/">those</a> <a title="Carlos's blog" href="http://carlosabalde.com/">who</a> <a title="Sergio's blog" href="https://blogs.igalia.com/svillar/">know</a> me a bit can really support this statement, no doubt about it.

The thing is that,  for some reason or another, whenever I tried a different editor, a <a title="Eclipse" href="http://www.eclipse.org">fancy IDE</a> or anything else, the result was always the same: I first realize of a new and very interesting feature X in the editor Y which makes me think for a while "hmmm... this could be the one", then I start using that editor Y for a while, then I realize I'm not comfortable enough for many other things, then I realize I'm continuously alternating between that editor and Emacs and then... finally... I somehow manage to "port" that very nice feature X to Emacs and ditch editor Y to finally come back to the origin again.

And that has been the story of my (text editing) life so far. And, as you can see, I haven't written a blog post about every single feature X I added to my Emacs. But this time is different.

Everything started, as usual, with me willing to try a new text editor, and this time I selected <a href="http://www.sublimetext.com/">Sublime Text 2</a> as the one to check, mainly because I wanted to check myself whether of all the hype around it was justified or whether it was just... well... just hype.

And I have to say that I was really impressed by ST2: what I've seen is a very nice and modern editor which is blazingly fast and convenient to use, and which on top of that it comes with a lot of useful features and a nice configuration out-of-the box, which is also very easy to customize and extend if you want to. Up to that moment, everything seemed to suggest I could be really in front of a replacement for Emacs, but given my past experiences I still took this with a grain of salt (even if I could not hide my excitement either)...

If you don't believe me, you should really checkout <a title="Sublime Text website" href="http://www.sublimetext.com/">its website</a> and, even better, the <a title="ST2 tutorial" href="https://tutsplus.com/course/improve-workflow-in-sublime-text-2/">"Perfect Workflow in Sublime Text2" tutorial</a> and you will see yourself what I'm talking about.

However, not all were bells and whistles in my ST2 experience. There were drawbacks too, and the main ones I could see were that it was not an Open Source editor and that the bus-factor was really scary (only one developer, I think). And those two things together were a serious concern to me. But I tried it anyway, because it really feel like it could be a serious competitor for my Emacs, and I was willing to take the risk, just for the sake of checking it (and playing around with a new editor, which I confess is something I love doing every now and then in any case).

But yet again, the same pattern happened one more time: I found myself loving ST2 in many regards but alternating too often between it and Emacs since, even if ST2 was lovely for many things, there was nothing that was really convincing me of replacing my Emacs in favour of it. Well, <strong>almost</strong> nothing... because the <a href="http://www.sublimetext.com/docs/2/multiple_selection_with_the_keyboard.html">"multiple cursors" feature in ST2</a> got my attention as not many text editor features got it in the last years.

So, the obvious step at this point, having already decided that I would be going back to Emacs again, would be to try to port this nice feature to Emacs, and then I found the <a title="Emacs Rocks!" href="emacsrocks.com">awesome "Emacs Rocks!" site</a>, where I found a demonstration of this sleek feature working inside Emacs. I´ll leave <a title="Emacs Rocks! Episode 13: multiple-cursors" href="http://www.youtube.com/watch?v=jNa3axo40qM">the link to the video here</a>, so you can really see what all this is about:

{{< youtube jNa3axo40qM >}}

As you can see, this feature is amazingly useful for many things of everyone's life (well, maybe not really everyone's, but almost!), as it's incredibly helpful for things like massive "search &amp; replace", improving code structure (e.g. break a list of strings in one single line into multiple ones) and many other situations.

Others might disagree, of course, but for me there's a "before" and an "after" I knew about this feature, and I don't think I will be able to easily move now to an editor which doesn't have something like this available in some way.

Should you want to try it out yourself, I recommend you to check out both <a href="http://emacsrocks.com/e13.html">episode 13 in "Emacs Rocks!"</a> as well as the <a href="https://github.com/magnars/multiple-cursors.el">github repository where you'll find the package</a> for Emacs.

Guess this means I'll stick to <a href="http://www.gnu.org/software/emacs/">Emacs</a> for some more time after all, even if I'm still not sure I will stick forever to it, since I can't say either I'm 100% comfortable with it, just that it's the best thing I've found so far. Yet I can't avoid feeling that <a title="U2: &quot;I Still Haven't Found What Im Looking For&quot;" href="http://www.youtube.com/watch?v=Pb1XXs7e7ac">I still haven't found what I'm looking for</a>...
