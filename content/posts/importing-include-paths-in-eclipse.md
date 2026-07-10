---
title: Importing include paths in Eclipse
date: '2015-11-07T02:35:51+00:00'
slug: importing-include-paths-in-eclipse
categories:
- GNOME
- Planet GNOME
- Planet GPUL
- Planet WebKitGTK
- Planeta GNOME Hispano
- Tips
- WebKit
- Emacs
- TextEditors
- Tools
- Chromium
- Eclipse
wp_id: 2071
---

First of all, let me be clear: no, I'm not <a href="/2013/03/23/multiple-cursors-emacs-and-me/">trying to leave Emacs again</a>, already got over that stage. Emacs is and will be my main editor for the foreseeable future, as it's clear to me that there's no other editor I feel more comfortable with, which is why I spent some time <a href="https://github.com/mariospr/emacs-configuration">cleaning up my .emacs.d and making it more "manageable"</a>.

But as much as like Emacs as my main "weapon", I sometimes appreciate the advantages of using a different kind of beast for specific purposes. And, believe me or not, in the past 2 years I learned to love <a href="https://eclipse.org/cdt/">Eclipse/CDT</a> as the best work-mate I know when I need some extra help to get deep inside of the two monster C++ projects that <a href="http://www.webkit.org">WebKit</a> and <a href="http://www.chromium.org/">Chromium</a> are. And yes, I know Eclipse is resource hungry, slow, bloated... and whatnot; but I'm lucky enough to have fast <em>SSDs</em> and lots of RAM in my laptop &amp; desktop machines, so that's not really a big concern anymore for me (even though I reckon that indexing chromium in the laptop takes "quite some time"), so let's move on :-)

However, there's this one little thing that still bothers quite me a lot of Eclipse: you need to <a href="http://help.eclipse.org/mars/index.jsp?topic=%2Forg.eclipse.cdt.doc.user%2Ftasks%2Fcdt_t_proj_paths.htm">manually setup the include paths for the external dependencies not in a standard location that a C/C++ project uses</a>, so that you can get certain features properly working such as code auto-completion, automatic error-checking features, call hierarchies... and so forth.

And yes, I know there is an <a href="https://marketplace.eclipse.org/content/pkg-config-support-eclipse-cdt">Eclipse plugin adding support for pkg-config</a> which should do the job quite well. But for some reason I can't get it to work with <a href="https://projects.eclipse.org/releases/mars">Eclipse Mars</a>, even though others apparently can use it there for some reason (and I remember using it with <a href="https://eclipse.org/juno/">Eclipse Juno</a>, so it's definitely not a myth).

Anyway, I did not feel like fighting with that (broken?) plugin, and in the other hand I was actually quite inclined to play a bit with <a href="https://www.python.org/">Python</a> so... my quick and dirty solution to get over this problem was to write a <a href="https://github.com/mariospr/scripts/blob/master/pkg-config-to-eclipse">small script that takes a list of package names (as you would pass them to pkg-config) and generates the XML content that you can use to import in Eclipse</a>. And surprisingly, that worked quite well for me, so I'm sharing it here in case someone else finds it useful.

Using <a href="https://git.gnome.org/browse/frogr/">frogr</a> as an example, I generate the XML file for Eclipse doing this:
<pre>
  $ pkg-config-to-eclipse glib-2.0 libsoup-2.4 libexif libxml-2.0 \
        json-glib-1.0 gtk+-3.0 gstreamer-1.0 > frogr-eclipse.xml
</pre>
...and then I simply import <em>frogr-eclipse.xml</em> from the project's properties, inside the <em>C/C++ General &gt; Paths and Symbols</em> section.

After doing that I get rid of all the brokenness caused by so many missing symbols and header files, I get code auto-completion nicely working back again and all those perks you would expect from this little big IDE. And all that without having to go through the pain of defining all of them one by one from the settings dialog, thank goodness!

Now you can quickly see how it works in the video below:
<p style="text-align: center;"><iframe src="https://www.youtube.com/embed/16TJ1zopjeY" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen"></iframe>
<a href="https://www.youtube.com/watch?v=16TJ1zopjeY">VIDEO: Setting up a C/C++ project in Eclipse with pkg-config-to-eclipse</a></p>
This has been very helpful for me, hope it will be helpful to someone else too!
