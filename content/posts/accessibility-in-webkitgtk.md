---
title: Accessibility in [WebKit]GTK+
date: '2013-02-03T02:26:23+00:00'
slug: accessibility-in-webkitgtk
categories:
- a11y
- accessibility
- GNOME
- Planet GNOME
- Planet GPUL
- Planet WebKitGTK
- Planeta GNOME Hispano
- WebKit
- WebKit2
- WebKitGTK
wp_id: 1422
---

This past week I've spent some time explaining to my mates at <a title="SERI UK" href="http://www.linkedin.com/company/samsung-electronics-research-institute">Samsung</a> the basics about how accessibility<i> </i>works and is implemented in <a title="WebKitGTK+" href="http://www.webkitgtk.org">WebKitGTK+</a>. I realized, yet again, of how messy and confusing everything can be the first time you encounter these things. After all, <a title="WebKit" href="http://www.webkit.org">WebKit</a> is quite a complex project already and <a title="Computer accessibility" href="http://en.wikipedia.org/wiki/Computer_accessibility">accessibility</a> is not a simple matter either.

In order to help them better understand this topic, I wrote a summary to have as reference that explains in my own words which the main pieces of the whole puzzle are, and how they relate to one another. In my experience, it's not always easy to understand the big picture quickly, and I think this kind of documentation can be quite useful for anyone willing to contribute to accessibility in <a title="WebKitGTK+" href="http://www.webkitgtk.org">WebKitGTK+</a>. At least it would have been useful for me when I started working on this. I only regret not having written it before, but better late than never, right?

So let's begin then. I will start by talking about accessibility-only stuff, which are basically common to any accessible application based in <a title="GTK+" href="http://www.gtk.org">GTK+</a>. Then I will explain the bits specific to <a title="WebKitGTK+" href="http://www.webkitgtk.org">WebKitGTK+</a> and how they fit in the picture.
<h3>Accessibility in GTK+ applications</h3>
The parts, or "actors", involved in any <a title="GTK+" href="http://www.gtk.org">GTK+</a> application from an accessibility point of view are:
<ul>
	<li><strong>Assistive Technologies (<em>ATs</em>)</strong></li>
	<li><strong>AT-SPI (Assistive Technology Service Provider Interface)</strong></li>
	<li><strong>ATK (Accessibility ToolKit)</strong></li>
	<li><strong>ATK &lt;-&gt; AT-SPI bridge</strong></li>
	<li><strong>GTK+</strong></li>
	<li><strong>GTK's Accessibility Implementation</strong></li>
</ul>
<a href="/2013/02/03/accessibility-in-webkitgtk/atk-a11y/" rel="attachment wp-att-1506"><img class="aligncenter size-large wp-image-1506" alt="Accessibility in GTK+ applications" src="/wp-content/uploads/2013/02/atk-a11y-600x290.png" width="584" height="282" /></a>

Now let's describe all those points, one by one:

<strong>Assistive Technologies (<em>ATs</em>)</strong>:

<em><a href="http://en.wikipedia.org/wiki/Assistive_technology" rel="nofollow">ATs</a> are a</em>pplications whose main purpose is to facilitate access and/or interaction with certain bits of information interesting from an accessibility related point of view, exposed by other applications. This access/interaction can be primarily output based. For instance the <a href="https://live.gnome.org/Orca" rel="nofollow">Orca</a> screen reader is an <em>AT</em> which provides access via text to speech and/or refreshable braille to on-screen information exposed by editors, browsers, mail agents and other applications.

Other <em>ATs</em> are primarily input based, allowing the user to interact with the exposed applications by executing certain actions over them (e.g. clicking on a exposed link), so it's not just about "consuming" information. Normally, <strong><em>ATs</em></strong> are called the <strong><i>clients</i></strong> and the <strong>applications</strong> exposing information the <strong><i>servers</i></strong>, as in the end it's actually an implementation of a typical client/server architecture.

<strong>AT-SPI (Assistive Technology Service Provider Interface)</strong>:<strong>
</strong>

Set of interfaces that Assistive Technologies (the <i>clients</i>) understand and use to inspect and interact with the accessible content exposed by applications in Linux environments. At some point, "someone" has to provide actual <a href="http://www.linuxfoundation.org/collaborate/workgroups/accessibility/atk/at-spi/at-spi_on_d-bus" rel="nofollow">AT-SPI</a> objects (linked together forming a <a href="http://www.linuxfoundation.org/collaborate/workgroups/accessibility/atk/at-spi/at-spi_on_d-bus" rel="nofollow">AT-SPI</a> hierarchy) implementing several of those interfaces (depending of the type of object) so <em>ATs</em> can "see them".

This is the job of <a href="http://git.gnome.org/browse/at-spi2-core/tree/registryd" rel="nofollow">the AT-SPI registry</a>, a daemon which takes care of maintaining a hierarchy of <a href="http://www.linuxfoundation.org/collaborate/workgroups/accessibility/atk/at-spi/at-spi_on_d-bus" rel="nofollow">AT-SPI</a> objects for every single accessible application in the system, in a centralized way, so <em>ATs</em> can interact with them. It is worth mentioning that the parent/children relationships in that hierarchy are modelled in terms of <a title="D-Bus" href="http://www.freedesktop.org/wiki/Software/dbus">D-Bus</a>, so different <a href="http://www.linuxfoundation.org/collaborate/workgroups/accessibility/atk/at-spi/at-spi_on_d-bus" rel="nofollow">AT-SPI</a> objects can belong to different processes.

<strong>ATK (Accessibility ToolKit)</strong>:

The toolkit used by <a title="GTK+" href="http://www.gtk.org">GTK+</a> applications to expose accessible representations of the toolkit's objects, along with appropriate interfaces, on the side of the applications exposing content (the <i>servers</i>). This representation is an almost a 1:1 match with the objects and interfaces defined by <a href="http://www.linuxfoundation.org/collaborate/workgroups/accessibility/atk/at-spi/at-spi_on_d-bus" rel="nofollow">AT-SPI</a> (that is, <em>almost</em>).

The main difference when it comes to understanding its place in the puzzle is that <a href="http://www.linuxfoundation.org/collaborate/workgroups/accessibility/atk/at-spi/at-spi_on_d-bus" rel="nofollow">AT-SPI</a> is what <i>clients</i> (ATs) understand, and that is not process-bounded (see previous point). <a href="http://developer.gnome.org/atk/stable/index.html" rel="nofollow">ATK</a>, in contrast, is what <i>servers</i> implement to expose accessible information, and it is process-bounded. Thus the parent/children relationships in the <a href="http://developer.gnome.org/atk/stable/index.html" rel="nofollow">ATK</a> hierarchy are modelled by actual references (pointers) between objects living in the same process.

<strong>ATK &lt;-&gt; AT-SPI bridge</strong>:

The glue that makes sure there's a mapping between the <a href="http://developer.gnome.org/atk/stable/index.html" rel="nofollow">ATK</a> hierarchy living in the <i>server</i> process and the <a href="http://www.linuxfoundation.org/collaborate/workgroups/accessibility/atk/at-spi/at-spi_on_d-bus" rel="nofollow">AT-SPI</a> hierarchy held by <a href="http://git.gnome.org/browse/at-spi2-core/tree/registryd" rel="nofollow">the AT-SPI registry</a>. Such a bridge is implemented in terms of <a title="D-Bus" href="http://www.freedesktop.org/wiki/Software/dbus">D-Bus</a> too, as it needs to communicate with the registry whenever something needs to be updated there, as well as when the <em>server</em> needs to react to external actions coming from ATs (e.g. perform the default <em>action</em> for an object).

<strong> GTK+</strong>:

The widgets toolkit normally used by applications embedding <a title="WebKitGTK+" href="http://www.webkitgtk.org">WebKitGTK+</a>. Explaining what <a title="GTK+" href="http://www.gtk.org">GTK+</a> is beyond the scope of this post, so I will assume you already know what it is.

<strong> GTK's Accessibility Implementation</strong>:

Provides <a title="AtkObject" href="http://developer.gnome.org/atk/stable/AtkObject.html">ATK objects</a> implementing different <a href="http://developer.gnome.org/atk/stable/index.html" rel="nofollow">ATK</a> interfaces for every widget from the <a title="GTK+" href="http://www.gtk.org">GTK+</a> library, and uses the <a href="http://git.gnome.org/browse/at-spi2-atk/" rel="nofollow">ATK &lt;-&gt; AT-SPI bridge</a> to communicate with <a href="http://git.gnome.org/browse/at-spi2-core/tree/registryd" rel="nofollow">the AT-SPI registry</a>. This means that if you use standard <a title="GTK+" href="http://www.gtk.org">GTK+</a> widgets only, your application will be accessible out-of-the-box. On the contrary, should you use custom widgets, you'll probably have to write custom <a title="AtkObject" href="http://developer.gnome.org/atk/stable/AtkObject.html">ATK objects</a> implementing the proper <a href="http://developer.gnome.org/atk/stable/index.html" rel="nofollow">ATK</a> interfaces to make them accessible too.

So that's all so far, when it comes to <a title="GTK+" href="http://www.gtk.org">GTK+</a> applications. Check the following diagram for a more detailed look at all these hierarchies for a hypothetical <a title="GTK+" href="http://www.gtk.org">GTK+</a> application exposing information and a screen reader accessing it:

<a href="/2013/02/03/accessibility-in-webkitgtk/gtk-a11y/" rel="attachment wp-att-1442"><img class="aligncenter size-large wp-image-1442" alt="Accessibility in GTK+ applications: a specific example" src="/wp-content/uploads/2013/02/gtk-a11y-600x259.png" width="584" height="252" /></a>As you can see, there's an <a href="http://developer.gnome.org/atk/stable/index.html" rel="nofollow">ATK</a> tree matching the <a title="GTK+" href="http://www.gtk.org">GTK+</a> hierarchy, and another <a href="http://www.linuxfoundation.org/collaborate/workgroups/accessibility/atk/at-spi/at-spi_on_d-bus" rel="nofollow">AT-SPI</a> tree matching the <a href="http://developer.gnome.org/atk/stable/index.html" rel="nofollow">ATK</a> one. Finally, the screen reader accesses the information through that <a href="http://www.linuxfoundation.org/collaborate/workgroups/accessibility/atk/at-spi/at-spi_on_d-bus" rel="nofollow">AT-SPI</a> tree, as explained above.
<h3>Accessibility in WebKitGTK+</h3>
Now that we already understand the basics of accessibility in <a title="GTK+" href="http://www.gtk.org">GTK+</a> applications, let's add the bits specifically related to <a title="WebKitGTK+" href="http://www.webkitgtk.org">WebKitGTK+</a>. Namely:
<ul>
	<li><strong>WebCore's Accessibility Objects</strong></li>
	<li><strong>WebKitGTK+ (ATK) wrappers</strong></li>
	<li><strong>WebKit2GTK+ specific details</strong></li>
</ul>
Again, a picture is usually better than just text, so here you have one too:

<a href="/2013/02/03/accessibility-in-webkitgtk/wkgtk-a11y/" rel="attachment wp-att-1496"><img class="aligncenter size-large wp-image-1496" alt="Accessibility in WebKitGTK+" src="/wp-content/uploads/2013/02/wkgtk-a11y-600x259.png" width="584" height="252" /></a>

In order to clarify it a bit more before explaining each point, let's just say that  you'll have to look in the dashed box named <em><a href="https://svn.webkit.org/repository/webkit/trunk/Source/WebCore" rel="nofollow">WebCore</a> accessibility world</em>, where the hierarchy on the left (red &amp; orange) represent the<a href="https://svn.webkit.org/repository/webkit/trunk/Source/WebCore" rel="nofollow"> </a><a href="https://svn.webkit.org/repository/webkit/trunk/Source/WebCore/accessibility/" rel="nofollow">WebCore Accessibility objects</a>, while the one on the right (the green one) represents the <a href="https://svn.webkit.org/repository/webkit/trunk/Source/WebCore/accessibility/atk/" rel="nofollow">WebKitGTK+ ATK wrappers</a>.

With this in mind, let's examine these three points in more depth:

<strong>WebCore Accessibility objects</strong>:

Similar to <a href="http://git.gnome.org/browse/gtk+/tree/gtk/a11y" rel="nofollow">GTK's Accessibility Implementation</a>, <a href="https://svn.webkit.org/repository/webkit/trunk/Source/WebCore" rel="nofollow">WebCore</a>'s accessibility objects are the implementation of an independent hierarchy exposing accessibility related information for objects present in a web page. As the mission of accessibility in <a title="WebKit" href="http://www.webkit.org">WebKit</a> is to expose information to users that are normally being rendered in the screen (as well as some other information that might be hidden to regular users), there is a tight relationship between this hierarchy and other ones in <a title="WebKit" href="http://www.webkit.org">WebKit</a>, such as the <a href="https://svn.webkit.org/repository/webkit/trunk/Source/WebCore/dom/">DOM tree</a> and the <a href="https://svn.webkit.org/repository/webkit/trunk/Source/WebCore/rendering/">Render Objects tree</a>.

This layer is meant to be platform-agnostic, so you won't find much <a title="WebKitGTK+" href="http://www.webkitgtk.org">WebKitGTK+</a> specific stuff here. Instead, you will find the implementation of the accessibility related specifications published by the <a title="World Wide Web Consortium" href="http://www.w3.org/">W3C</a>'s <a title="Web Accessibility Initiative" href="http://www.w3.org/WAI/">Web Accessibility Initiative (WAI)</a>, such as <a title="WAI-ARIA" href="http://www.w3.org/WAI/intro/aria.php">WAI-ARIA</a>.

<strong>WebKitGTK+ ATK wrappers</strong>:

An <a href="http://developer.gnome.org/atk/stable/index.html" rel="nofollow">ATK</a>-based implementation of an accessibility hierarchy where every <a title="AtkObject" href="http://developer.gnome.org/atk/stable/AtkObject.html">ATK object</a> will take care of wrapping the proper accessibility object from <a href="https://svn.webkit.org/repository/webkit/trunk/Source/WebCore" rel="nofollow">WebCore</a>, as well as implementing the proper <a href="http://developer.gnome.org/atk/stable/index.html" rel="nofollow">ATK</a> interfaces depending on the situation (e.g. the role of the <a title="WebCore Accessibility Object" href="https://svn.webkit.org/repository/webkit/trunk/Source/WebCore/accessibility/AccessibilityObject.h">WebCore accessibility object</a>, some properties coming from the associated <a href="https://svn.webkit.org/repository/webkit/trunk/Source/WebCore/rendering/">Render Object</a>...).

The <a href="http://developer.gnome.org/atk/stable/index.html" rel="nofollow">ATK</a> hierarchy created here is connected with the <a href="http://developer.gnome.org/atk/stable/index.html" rel="nofollow">ATK</a> hierarchy from the embedding application (normally a <a title="GTK+" href="http://www.gtk.org">GTK+</a> app) by setting the root <a title="AtkObject" href="http://developer.gnome.org/atk/stable/AtkObject.html">ATK object</a> in this tree (normally representing <a title="The DOM" href="http://www.w3.org/DOM/">DOM</a>'s root element) as the child of the leaf <a title="AtkObject" href="http://developer.gnome.org/atk/stable/AtkObject.html">ATK object</a> in the tree coming from the embedding application (normally the <a href="http://developer.gnome.org/gtk3/stable/GtkWidget.html">GtkWidget</a> containing the <a href="https://svn.webkit.org/repository/webkit/trunk/Source/WebKit/gtk/webkit/webkitwebview.h">WebView</a>).

As is the case with any other regular <a title="GTK+" href="http://www.gtk.org">GTK+</a> application, this <a href="http://developer.gnome.org/atk/stable/index.html" rel="nofollow">ATK</a> hierarchy will finally be seen by <em>ATs</em> thanks to the translation that the <a href="http://git.gnome.org/browse/at-spi2-atk/" rel="nofollow">ATK &lt;-&gt; AT-SPI bridge</a> will do for us, making the whole <a href="http://developer.gnome.org/atk/stable/index.html" rel="nofollow">ATK</a> tree from the <a title="WebKitGTK+" href="http://www.webkitgtk.org">WebKitGTK+</a> based application (from the top level <a title="GTK+" href="http://www.gtk.org">GTK+</a> window down to the deepest accessibility object inside <a href="https://svn.webkit.org/repository/webkit/trunk/Source/WebCore" rel="nofollow">WebCore</a>) available to <a href="http://git.gnome.org/browse/at-spi2-core/tree/registryd" rel="nofollow">the AT-SPI registry</a> by means of <a title="D-Bus" href="http://www.freedesktop.org/wiki/Software/dbus">D-Bus</a>.

<strong>WebKit2GTK+ specific details</strong>:

I already talked about this <a title="Accessibility support in WebKit2GTK+" href="/2012/01/27/accessibility-support-in-webkit2gtk/">in</a> <a title="WebKitGTK+ Hackfest: WK2, a11y and Ephiphany’s ad blocker extension" href="/2011/12/06/webkitgtk-hackfest-wk2-a11y-and-ephiphanys-ad-blocker/">previous</a> <a title="Orca and WebKit2GTK+: initial results" href="/2011/11/11/orca-and-webkit2gtk-initial-results/">posts</a>, so I will focus here just on commenting the main difference compared to the generic case for <a title="WebKitGTK+" href="http://www.webkitgtk.org">WebKitGTK+</a> described earlier (see previous diagram above):

<a title="WebKit2GTK+" href="http://webkitgtk.org/reference/webkit2gtk/unstable/index.html">WebKit2GTK+</a> implements a split-process model, where the  high level API belongs to one process (the <a href="https://svn.webkit.org/repository/webkit/trunk/Source/WebKit2/UIProcess/"><em>UI process</em></a>) while the core logic of the web engine lives in another one (the <a href="https://svn.webkit.org/repository/webkit/trunk/Source/WebKit2/WebProcess/"><em>Web process</em></a>).

From an accessibility point of view, this means that the full hierarchy of <a title="AtkObject" href="http://developer.gnome.org/atk/stable/AtkObject.html">ATK objects</a> we had before is also split in two parts: some accessibility objects are now in the <a href="https://svn.webkit.org/repository/webkit/trunk/Source/WebKit2/UIProcess/"><em>UI process</em></a> and the rest of them will be in the <a href="https://svn.webkit.org/repository/webkit/trunk/Source/WebKit2/WebProcess/"><em>Web process</em></a>.

To be more specific, we'll find the following objects in each process:
<ul>
	<li><strong><em>UI Process</em></strong>: basically, the <a title="AtkObject" href="http://developer.gnome.org/atk/stable/AtkObject.html">ATK object</a> associated with the <a href="http://developer.gnome.org/gtk3/stable/GtkWidget.html">GtkWidget</a> provided by <a title="WebKitGTK+" href="http://www.webkitgtk.org">WebKitGTK+</a>, that is, the <a href="https://svn.webkit.org/repository/webkit/trunk/Source/WebKit2/UIProcess/API/gtk/WebKitWebView.h">WebView</a>.</li>
	<li><strong><em>Web Process</em></strong>: the whole hierarchy of <a title="AtkObject" href="http://developer.gnome.org/atk/stable/AtkObject.html">ATK objects</a> wrapping the accessibility objects from <a href="https://svn.webkit.org/repository/webkit/trunk/Source/WebCore" rel="nofollow">WebCore</a>.</li>
</ul>
As <a title="Blog post: WebKit Contributors Meeting, sockets &amp; plugs" href="/2011/05/05/webkit-contributors-meeting-sockets-plugs/">I explained previously</a>, these two <a href="http://developer.gnome.org/atk/stable/index.html" rel="nofollow">ATK</a> hierarchies will be seen as a single accessibility hierarchy by <em>ATs</em> thanks to the "magic" of <a title="AtkPlug" href="http://developer.gnome.org/atk/stable/atk-AtkPlug.html">AtkPlug</a> and <a title="AtkSocket" href="http://developer.gnome.org/atk/stable/atk-AtkSocket.html">AtkSocket</a> classes, which takes care of exposing everything together in a single <a href="http://www.linuxfoundation.org/collaborate/workgroups/accessibility/atk/at-spi/at-spi_on_d-bus" rel="nofollow">AT-SPI</a> tree. And remember that such a tree is modelled by means of <a title="D-Bus" href="http://www.freedesktop.org/wiki/Software/dbus">D-Bus</a>, so it does not matter that things are actually in different processes.

Thus, since <em>ATs</em> just<em> </em> understand <a href="http://www.linuxfoundation.org/collaborate/workgroups/accessibility/atk/at-spi/at-spi_on_d-bus" rel="nofollow">AT-SPI</a>, they will see The Right Thing (tm) as in the previous case where we have one single process. See the following diagram for a more visual explanation of this:

<a href="/2013/02/03/accessibility-in-webkitgtk/wk2gtk-a11y/" rel="attachment wp-att-1447"><img class="aligncenter size-large wp-image-1447" alt="Accessibility in WebKit2GTK+" src="/wp-content/uploads/2013/02/wk2gtk-a11y-600x335.png" width="584" height="326" /></a>
<h3>Wrapping up</h3>
So that's it. At the end the post turned out to be longer than what I was expecting, as my initial idea was to publish the stuff I wrote internally at <a title="SERI UK" href="http://www.linkedin.com/company/samsung-electronics-research-institute">Samsung</a> this week, but ended up extending it quite a lot!

At least I hope this will be helpful for anyone willing to contribute to accessibility, either in <a title="WebKitGTK+" href="http://www.webkitgtk.org">WebKitGTK+</a> or in a more general way.

After all, most of the stuff I talked about here applies to  every accesible <a title="GTK+" href="http://www.gtk.org">GTK+</a> application: <a href="http://en.wikipedia.org/wiki/Assistive_technology" rel="nofollow">Assistive Technologies (<em>ATs</em>)</a>, <a href="http://www.linuxfoundation.org/collaborate/workgroups/accessibility/atk/at-spi/at-spi_on_d-bus" rel="nofollow">AT-SPI</a>, <a href="http://developer.gnome.org/atk/stable/index.html" rel="nofollow">ATK</a>, the <a href="http://git.gnome.org/browse/at-spi2-atk/" rel="nofollow">ATK &lt;-&gt; AT-SPI bridge</a>...

Last, I would like to thanks <a title="Joanmarie Diggs's blog" href="http://blog.grain-of-salt.com/">Joanmarie Diggs</a> from <a title="Igalia" href="http://www.igalia.com">Igalia</a> for her help with this blog post. One certainly feels more confident writing a long article like this one about a very specific topic when you have one of the most experienced persons on the matter reviewing it!
