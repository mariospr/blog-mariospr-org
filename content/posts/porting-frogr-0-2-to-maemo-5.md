---
title: Porting Frogr 0.2 to Maemo 5
date: '2010-01-13T10:06:37+00:00'
slug: porting-frogr-0-2-to-maemo-5
categories:
- frogr
- GNOME
- Maemo
- Planet GNOME
- Planet GPUL
- Planet Igalia
- Planet Maemo
wp_id: 155
---

<p style="text-align: left">During the last days (well, actually during the last <strong>nights</strong> [*]), I've been spending some time in adapting <a title="Frogr's web site" href="http://code.google.com/p/frogr/" target="_self">frogr 0.2</a> to also compile and work on my brand new N900 (thanks Igalia!), and this is the humble result up to date:</p>
<p style="text-align: left"><a href="/wp-content/uploads/2010/01/Screenshot-20100113-083300.png"><img class="aligncenter size-medium wp-image-156" src="/wp-content/uploads/2010/01/Screenshot-20100113-083300-300x180.png" alt="Frogr 0.2 for Fremantle" width="300" height="180" /></a></p>

Perhaps you're thinking why the hell I needed frogr to upload pictures when the N900 already comes with a nice and handy sharing application to upload pictures directly from the camera app or the image viewer, so here you have some use cases where I found the  sharing app not enough for my needs:
<ul>
	<li><del>To upload several pictures in a row to flickr, instead of having to do it one by one (tipical use case after taking several pictures that I'd like to share/backup in flickr).</del></li>
	<li>To set same name, description <del>and/or tags</del> to a bunch of pictures instead of doing it one by one (related to previous use case).</li>
	<li><del>To be able to upload pictures as "private" instead of "public".</del></li>
</ul>
<strong>Update:</strong> I'm correcting this post here since <a href="/2010/01/13/porting-frogr-0-2-to-maemo-5/#comments">it seems the sharing application already was capable of doing some of those things I mentioned above</a> (ups!). Anyway, as I commented there, this does not discourage me even a little bit of keeping porting my little frogr to Fremantle, but just encourage me to try to make a difference and because... why not to tell it? I'd just love to bring frogr with me wherever I go :-). Thanks Daniel for your comment!

Current status of this port to Fremantle is still work in progress so don't expect to find anything working out-of-the-box if you download the <a title="Source code at gitorious" href="http://gitorious.org/frogr">source code</a> at this moment, but the idea is to get it into a stable state soon to upload it to maemo-extras, along with a packaged version for Fremantle of the great <a title="Flickcurl: C API to flickr" href="http://librdf.org/flickcurl/">flickcurl</a> library, which is a requirement for frogr to work (and at this moment I'm jsut packaging and using it on my own for development purposes).

[*] I think the screenshot explains pretty well the main reason why I work so slowly and at late hours in frogr :-)
