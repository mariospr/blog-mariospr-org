---
title: My sloppy, dirty, ugly... but (maybe) useful script for the Vagalume D-Bus interface
date: '2008-03-01T21:16:39+00:00'
slug: my-sloppy-dirty-ugly-but-maybe-useful-script-for-the-vagalume-d-bus-interface
categories:
- GNOME
- Maemo
- Planet GNOME
- Planet GPUL
- Planet Igalia
- Planet Maemo
- Vagalume
wp_id: 21
---

<a title="Vagalume playing on my hi-fi system" href="/wp-content/uploads/2008/03/20080301-vagalume_aux.jpg"><img src="/wp-content/uploads/2008/03/20080301-vagalume_aux_thumb.jpg" alt="Vagalume playing on my hi-fi system" /></a>

Today, while doing the houseworks, I plugged the N800 to the AUX input of my mini hi-fi system (see the photo), in order to listen my online radios with Vagalume while I was doing several tasks all around my flat.

Then, after finishing those tasks, I sat in front of my laptop and I began to do some tipical tasks: read mail, surf the internet, talk with some friends through IM... while Vagalume kept playing music through my hi-fi system in the living room. And then, while I was thinking how nice is to listen Last.fm through a couple of good speakers, I suddenly found out that I should face the <strong>big dilemma</strong>:
<ul>
	<li>Sometimes I'd like to change the radio station which is being played in Vagalume, or just to Skip some songs.</li>
	<li>I love to listen music through the hi-fi system, even when I'm not in the living room (likely, my neighbours love this too), so stopping Vagalume from running on the N800 and running it in my laptop would not be an option.</li>
	<li>The N800 is in another room, so <strong>I should leave the chair</strong> if I want to interact with Vagalume.</li>
</ul>
Maybe, you could be thinking of me as a very lazy person, but first just think of yourself in a similar situation and maybe you could understand what I'm talking about :-)

So, this stupid situation was the perfect excuse for me to write an small, sloppy and ugly script that, at least, works pretty well on the N800, and which allows to <strong>easily manage some of the functions of Vagalume</strong> that are available via its <strong>D-Bus interface</strong>:
<ul>
	<li>Run / Close Vagalume application (via D-Bus methods).</li>
	<li>Play / Skip / Stop songs.</li>
	<li>Setting the current radio to:</li>
<ul>
	<li>A 'global tags' radio, specifiying tags separated by spaces.</li>
	<li>A 'similar artists' radio, specifying an artist name.</li>
	<li>A 'last.fm group' radio, specifying the name of the group.</li>
	<li>An 'user's loved / neighbours / personal / playlist' radio, specifying the username.</li>
	<li>A custom radio, just specifying a valid lastfm URL.</li>
</ul>
</ul>
So, now I'm able to remotely manage Vagalume in the N800 in an easy way, while it's playing music in the living room and I am, say, in my bedroom working on my laptop, just by 'implementing' the following recipe:
<ul>
	<li>A <strong>ssh server </strong>(available through the <em>maemo-extras</em> repository, IIRC) running on the N800.</li>
	<li><strong>My sloppy script</strong> installed on the N800 as well.</li>
	<li>A X terminal running on my laptop, to remotely control Vagalume.</li>
	<li>A bottle of <a title="Estrella Galicia beer" href="http://www.estrellagalicia.es/html/in/00_home/00_home.asp" target="_blank">a good beer</a> near the laptop, to minimize the need of leaving the chair without a good reason (not mandatory ;-)).</li>
</ul>
For instance, this is how I'd skip a song and then I'd set a <em>hard rock</em> radio:
<blockquote>$ vagalume-dbus skip
$ vagalume-dbus tag "hard rock"</blockquote>
So, here you are the script just in case you're so lazy as me and you'd like to use it too: <a title="The vagalume-dbus script" href="/sources/vagalume/vagalume-dbus">vagalume-dbus script</a>.

Please notice that this is <strong>not</strong> an official script of Vagalume, at least not yet :-). I'll talk to <a title="Berto's blog" href="https://blogs.igalia.com/berto">Berto</a> to see if it would be or not a good idea to bundle it with the next release of Vagalume. Perhaps it could be useful after all :-).

What do you think?
