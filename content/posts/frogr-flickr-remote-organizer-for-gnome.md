---
title: 'frogr: flickr remote organizer for GNOME'
date: '2009-06-05T18:25:18+00:00'
slug: frogr-flickr-remote-organizer-for-gnome
categories:
- frogr
- GNOME
- Planet GNOME
- Planet GPUL
- Planet Igalia
wp_id: 58
---

<a href="http://code.google.com/p/frogr"><img class="alignleft" src="/wp-content/uploads/2009/06/20090605-frogr-logo.png" alt="" width="104" height="100" /></a>Right some days before than my son was born I started to hack a bit on a new and small project to develop a C-based <a title="Flickr website" href="http://www.flickr.com" target="_blank">flickr</a> manager for <a title="The GNOME Project" href="http://www.gnome.org" target="_blank">GNOME</a>, as current alternatives out there (which I were extensively using for more than a year), even thought being great applications, were not by all means what I was looking for or, in other words, what I would expect from a GNOME application which would not only allow me to upload pictures, but also to do a couple more of things like re-tagging pictures or managing albums for instance.

Therefore, bearing in mind how my new responsibilities as a father would add an extra level of challenge to the idea of developing an application when having even less time, I decided to go ahead with it and try to write some basic lines of code to see how feasible this could be. And after two months since I came up with this idea, although I could not of course code everyday (not even every week), I decided some days ago to push this forward and to really acquire the commitment of going ahead with the project in my spare time, even thought there's not too much nowadays ;-)

So here I am, introducing this new project, so hopefully someone else could like to join this quest and help me to build a full featured flickr manager for our beloved favourite desktop environment. Have to say, of course, that the project is now at a very early stage (no debian package, only basic features, horrible UI...) but please don't be scared of it just because of that :-). Moreover, in the other hand I have to say as well that at least it already performs the most basic features I thought of for this stage, which are:
<ul>
	<li>Asking for authorization inside the user's flickr account, requesting read/write permissions.</li>
	<li>Loading several pictures to be uploaded at the same time, showing all of then inside a convenient GtkIconView widget.</li>
	<li>Upload all the loaded pictures with just one click, opening a specific flickr URL at the end of the process, to allow specifying some properties for the pictures uploaded: name, description and tags.</li>
</ul>
<a href="http://code.google.com/p/frogr"><img class="aligncenter" src="/wp-content/uploads/2009/06/20090605-frogr-screenshot.jpg" alt="" /></a>

As you can see this is not too much, but the plan is follow the "release early release often" approach, so that's why I'm doing this right now. Later on (hopefully soon) many other features will be implemented, which should make of this app a great tool for flickr fans like me... and I guess the code base to make this a reality is already written so now it's a matter of implementing one feature after another.

Please take a look to the <em>TODO</em> file in case you're interested in participate, and if you want a more comprehensive list of tasks I think should be the next ones. And obviously I'm open to suggestions so don't hesitate to comment, propose or criticism anything you want.

To finish with this, I'd like to leave here some pointers, in case you were somehow interested on this project:
<ul>
	<li><strong>Website</strong>: <a title="Frogr website" href="http://code.google.com/p/frogr" target="_blank">http://code.google.com/p/frogr</a></li>
	<li><strong>Mailing lists</strong>:
<ul>
	<li>General discussion: <a title="General discussion about frogr" href="http://groups.google.com/group/frogr-users" target="_blank">http://groups.google.com/group/frogr-users</a></li>
	<li>Technical discussion: <a title="Technical discussion about frogr" href="http://groups.google.com/group/frogr-devel" target="_blank">http://groups.google.com/group/frogr-devel</a></li>
</ul>
</li>
	<li><strong>Source code</strong>: <a title="Git repository at gitorious" href="http://gitorious.org/frogr" target="_blank">http://gitorious.org/frogr</a></li>
</ul>
So that's all I guess. Now it's time for me to continue the development... and for you to start <strong>getting involved</strong> ;-).

C'mon, flickr maniac, what are you waiting for?

PS: Thanks <a title="Adrian's blog" href="https://blogs.igalia.com/aperez/" target="_blank">Adrian</a> for providing a logo for the project. Quite a nice way to get a first contribution with the project ;-)
