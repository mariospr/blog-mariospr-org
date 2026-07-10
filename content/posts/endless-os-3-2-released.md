---
title: Endless OS 3.2 released!
date: '2017-07-04T11:15:44+00:00'
slug: endless-os-3-2-released
categories:
- GNOME
- Planet GNOME
- Planet GPUL
- Planeta GNOME Hispano
- Endless
- GNOME Shell
wp_id: 2386
---

We just <a href="https://community.endlessos.com/t/release-endless-os-version-3-2/2794">released Endless OS 3.2</a> to the world after a lot of really hard work from everyone here at <a href="https://endlessm.com/">Endless</a>, including many important changes and fixes that spread pretty much across the whole OS: from the guts and less visible parts of the core system (e.g. a newer <a href="https://github.com/torvalds/linux">Linux kernel</a>, <a href="https://ostree.readthedocs.io/en/latest/manual/introduction/">OSTree</a> and <a href="https://flatpak.org">Flatpak</a> improvements, updated libraries...) to other more visible parts including a whole rebase of the GNOME components and applications (e.g. mutter, gnome-settings-daemon, nautilus...), newer and improved "Endless apps" and a completely revamped desktop environment.

By the way, before I dive deeper into the rest of this post, I'd like to remind you that<a href="https://endlessos.com/">Endless OS</a> is a <a href="https://endlessos.com/download/">Operating System that you can download for free</a> from <a href="https://endlessos.com">our website</a>, so please don't hesitate to check it out if you want to try it by yourself. But now, even though I'd love to talk in detail about ALL the changes in this release, I'd like to talk specifically about what has kept me busy most of the time since around March: the full revamp of our desktop environment, that is, our particular version of <a href="https://wiki.gnome.org/Projects/GnomeShell">GNOME Shell</a>.

<figure class="wp-caption aligncenter" style="max-width:600px"><a href="/wp-content/uploads/2017/07/1.eos-desktop.png"><img class="wp-image-2387 size-large" src="/wp-content/uploads/2017/07/1.eos-desktop-600x338.png" alt="Endless OS 3.2 as it looks in my laptop right now" width="600" height="338" /></a><figcaption>Endless OS 3.2 as it looks in my laptop right now</figcaption></figure>

If you're already familiar with what Endless OS is and/or with <a href="https://www.gnome.org">the GNOME project</a>, you might already know that Endless's desktop is a forked and heavily modified version of GNOME Shell, but what you might not know is that it was specifically based on <a href="https://git.gnome.org/browse/gnome-shell/tag/?h=3.8.0">GNOME Shell 3.8</a>.

Yes, you read that right, no kidding: a now 4 years old version of GNOME Shell was alive and kicking underneath the thousands of downstream changes that we added on top of it during all that time to implement the desired user experience for our target users, as we iterated based on tons of user testing sessions, research, design visions... that this company has been working on right since its inception. That includes porting very visible things such as the "Endless button", the user menu, the apps grid right on top of the desktop, the ability to drag'n'drop icons around to re-organize that grid and easily manage folders (by just dragging apps into/out-of folders), the integrated desktop search (+ additional search providers), the window picker mode... and many other things that are not visible at all, but that are required to deliver a tight and consistent experience to our users.

<figure class="wp-caption aligncenter" style="max-width:600px"><a href="/wp-content/uploads/2017/07/4.show-desktop-button.png"><img class="wp-image-2391 size-large" src="/wp-content/uploads/2017/07/4.show-desktop-button-600x31.png" alt="Endless button showcasing the new &quot;show desktop&quot; functionality" width="600" height="31" /></a><figcaption>Endless button showcasing the new "show desktop" functionality</figcaption></figure>

<figure class="wp-caption aligncenter" style="max-width:600px"><a href="/wp-content/uploads/2017/07/3.bar-menus.png"><img class="size-large wp-image-2390" src="/wp-content/uploads/2017/07/3.bar-menus-600x181.png" alt="" width="600" height="181" /></a><figcaption>Aggregated system indicators and the user menu</figcaption></figure>

Of course, this situation was not optimal and finally we decided we had found the right moment to tackle this situation in line with the 3.2 release, so I was tasked with leading the mission of "rebasing" our downstream changes on top of a newer shell (more specifically on top of <a href="https://git.gnome.org/browse/gnome-shell/tag/?h=3.22.3">GNOME Shell 3.22</a>), which looked to me like a "hell of a task" when I started, but still I didn't really hesitate much and gladly picked it up right away because I really did want to make our desktop experience even better, and this looked to me like a pretty good opportunity to do so.

By the way, note that I say <em>"rebasing"</em> between quotes, and the reason is because the usual approach of taking your downstream patches on top of a certain version of an Open Source project and apply them on top of whatever newer version you want to update to didn't really work here: the vast amount of changes combined with the fact that the code base has changed quite a bit between 3.8 and 3.22 made that strategy fairly complicated, so in the end we had to opt for a combination of rebasing some patches (when they were clean enough and still made sense) and a re-implementation of the desired functionality on top of the newer base.

<figure class="wp-caption aligncenter" style="max-width:600px"><a href="/wp-content/uploads/2017/07/2.integrated-search.png"><img class="wp-image-2389 size-large" src="/wp-content/uploads/2017/07/2.integrated-search-600x208.png" alt="Integrated desktop search" width="600" height="208" /></a><figcaption>The integrated desktop search in action</figcaption></figure>

<figure class="wp-caption aligncenter" style="max-width:600px"><a href="/2017/07/04/endless-os-3-2-released/6-folders/"><img class="wp-image-2418 size-large" src="/wp-content/uploads/2017/07/6.folders-600x150.png" alt="" width="600" height="150" /></a><figcaption>New implementation for folders in Endless OS (based on upstream's)</figcaption></figure>

As you can imagine, and especially considering my fairly limited previous experience with things like mutter, clutter and the shell's code, this proved to be a pretty difficult thing for me to take on if I'm truly honest. However, maybe it’s precisely because of all those things that, now that it's released, I look at the result of all these months of hard work and I can't help but feel very proud of what we achieved in this, pretty tight, time frame: we have a refreshed Endless OS desktop now with new functionality, better animations, better panels, better notifications, better folders (we ditched our own in favour of upstream's), better infrastructure... better <b>everything</b>!.

Sure, it's not perfect yet (no such a thing as "finished software", right?) and we will keep working hard for the next releases to fix known issues and make it even better, but what we have released today is IMHO a pretty solid 3.2 release that I feel very proud of, and one that is out there now already for everyone to see, use and enjoy, and that is quite an achievement.

<figure class="wp-caption aligncenter" style="max-width:600px"><a href="/2017/07/04/endless-os-3-2-released/7-trashcan/" rel="attachment wp-att-2421"><img class="size-large wp-image-2421" src="/wp-content/uploads/2017/07/7.trashcan-600x203.png" alt="" width="600" height="203" /></a><figcaption>Removing and app by dragging and dropping it into the trash bin</figcaption></figure>

Now, you might have noticed I used "we" most of the time in this post when referring to the hard work that <b>we</b> did, and that's because this was not something I did myself alone, not at all. While it's still true I started working on this mostly on my own and that I probably took on most of the biggest tasks myself, the truth is that several other people jumped in to help with this monumental task tackling a fair amount of important tasks in parallel, and I'm pretty sure we couldn't have released this by now if not because of the team effort we managed to pull here.

I'm a bit afraid of forgetting to mention some people, but I'll try anyway: many thanks to <a href="https://blogs.gnome.org/cosimoc/">Cosimo Cecchi</a>, <a href="https://www.joaquimrocha.com/">Joaquim Rocha</a>, <a href="https://www.linkedin.com/in/roddyshuler/">Roddy Shuler</a>, <a href="https://feaneron.com/">Georges Stavracas</a>, <a href="http://www.saikurain.com/">Sam Spilsbury</a>, <a href="https://willthompson.co.uk/">Will Thomson</a>, <a href="https://github.com/erikos">Simon Schampijer</a>, <a href="https://blogs.gnome.org/mcatanzaro/">Michael Catanzaro</a> and of course the entire design team, who all joined me in this massive quest by taking some time alongside with their other responsibilities to help by tackling several tasks each, resulting on the shell being released on time.

<figure class="wp-caption aligncenter" style="max-width:600px"><a href="/wp-content/uploads/2017/07/5.window-picker.png"><img class="size-large wp-image-2394" src="/wp-content/uploads/2017/07/5.window-picker-600x338.png" alt="" width="600" height="338" /></a><figcaption>The window picker as activated from the hot corner (bottom - right)</figcaption></figure>

Last, before I finish this post, I'd just like to <i>pre-answer</i> a couple of questions that I guess some of you might have already:

<em><strong>Will you be proposing some of this changes upstream?</strong></em>

Our intention is to reduce the diff with upstream as much as possible, which is the reason we have left many things from upstream untouched in Endless OS 3.2 (e.g. the date/menu panel) and the reason why we already did some fairly big changes for 3.2 to get closer in other places we previously had our very own thing (e.g. folders), so be sure we will upstream everything we can as far as it's possible and makes sense for upstream.

Actually, we have already pushed many patches to the shell and related projects since Endless moved to GNOME Shell a few years ago, and I don't see any reason why that would change.

<em><strong>When will Endless OS desktop be rebased again on top of a newer GNOME Shell?</strong></em>

If anything we learned from this "rebasing" experience is that we don't want to go through it ever again, seriously :-). It made sense to be based on an old shell for some time while we were prototyping and developing our desktop based on our research, user testing sessions and so on, but we now have a fairly mature system and the current plan is to move on from this situation where we had changes on top of a 4 years old codebase, to a point where we'll keep closer to upstream, with more frequent rebases from now on.

Thus, the short answer to that question is that we plan to rebase the shell more frequently after this release, ideally two times a year so that we are never too far away from the latest GNOME Shell codebase.

<hr />

And I think that's all. I've already written too much, so if you excuse me I'll get back to my Emacs (yes, I'm still using Emacs!) and let you enjoy this video of a recent development snapshot of Endless OS 3.2, as created by my colleague <a href="http://mhall119.com/">Michael Hall</a> a few days ago:
<p style="text-align: center;"><iframe src="https://www.youtube.com/embed/xUALNKTs7Nw" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe>
(Feel free to visit <a href="https://www.youtube.com/channel/UCgqAGKmbwAjRAM0gZR_cyNg">our YouTube channel</a> to check out for more videos like this one)</p>
Also, quick shameless plug just to remind you that we have an <a href="https://community.endlessos.com">Endless Community</a> website which you can join and use to provide feedback, ask questions or simply to keep informed about Endless. And if real time communication is your thing, we're also on IRC (<em>#endless</em> on <em>Freenode</em>) and <a href="https://endless-community.signup.team/">Slack</a>, so I very much encourage you to join us via any of these channels as well if you want.

<a href="https://2017.guadec.org/"><img class="alignright wp-image-2399 size-thumbnail" src="/wp-content/uploads/2017/07/going-to-guadec-badge-150x150.png" alt="" width="150" height="150" /></a> Ah! And before I forget, just a quick note to mention that this year I'm going to <a href="https://2017.guadec.org/">GUADEC</a> again after a big break (my last one was in Brno, in 2013) thanks to my company, which is sponsoring my attendance in several ways, so feel free to say "hi!" if you want to talk to me about Endless, the shell, life or anything else.
