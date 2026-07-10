---
title: 'Igalia and WebKit: status update and plans (2024)'
date: '2024-11-03T17:20:01+00:00'
slug: igalia-and-webkit-status-update-and-plans-2024
categories:
- Planet GNOME
- Planet GPUL
- Planet Igalia
- Planet WebKitGTK
- Planeta GNOME Hispano
- WebKit
- WebKitGTK
- WPE
wp_id: 3215
---

It's been more than 2 years since the last time I wrote something here, and in that time a lot of things happened. Among those, one of the main highlights was <strong>me moving back to <a href="https://www.igalia.com">Igalia</a>'s <a href="https://planet.igalia.com/webkit">WebKit team</a></strong>, but this time I moved as part of Igalia's support infrastructure to help with other types of tasks such as general coordination, team facilitation and project management, among other things.

On top of those things, I've been also <strong>presenting our work around WebKit in different venues</strong>, such as <a href="https://www.slideshare.net/slideshow/building-enduser-applications-on-embedded-devices-with-wpe/267644868" target="_blank" rel="noopener">in the Embedded Open Source Summit</a> or <a href="https://www.slideshare.net/slideshow/addthepowerofthewebtoyourembeddeddeviceswithwpewebkitpdf/262768577" target="_blank" rel="noopener">in the Embedded Recipes conference</a>, for instance. Of course, that included presenting our work in the <a href="https://www.webkit.org">WebKit community</a> as part of the <a href="https://webkit.org/meeting/" target="_blank" rel="noopener">WebKit Contributors Meeting</a>, a small and technically focused event that happens every year, normally around the Bay Area (California). That's often a pretty dense presentation where, over the course of 30-40 minutes, we go through all the main areas that we at Igalia contribute to in WebKit, trying to summarize our main contributions in the previous 12 months. This includes work not just from the <strong>WebKit team</strong>, but also from other ones such as our <strong>Web Platform</strong>, <strong>Compilers</strong> or <strong>Multimedia teams</strong>.

So far I did that a couple of times only, both <a href="https://www.slideshare.net/slideshow/igalia-and-webkit-status-update-and-plans/262768753" target="_blank" rel="noopener">last year on October 24rth</a> as well as this year, just <a href="https://www.slideshare.net/slideshow/igalia-and-webkit-status-update-and-plans-72bd/272669557" target="_blank" rel="noopener">a couple of weeks ago in the latest instance of the WebKit Contributors meeting</a>. I believe the session was interesting and informative, but unfortunately it does not get recorded so this time I thought I'd write a blog post to make it more widely accessible to people not attending that event.

This is a long read, so maybe grab a cup of your favorite beverage first...
<h2>Igalia and WebKit</h2>
So first of all, what is the <strong>relationship between Igalia and the WebKit project</strong>?
<p style="text-align: center;"><a href="https://www.igalia.com"><img class="alignnone wp-image-3288" src="/wp-content/uploads/2024/11/igalia-logo-800x325.jpg" alt="Igalia logo" width="345" height="140" /></a><a href="https://webkit.org"><img class="alignnone wp-image-3289" src="/wp-content/uploads/2024/11/webkit-logo-275x300.png" alt="WebKit logo" width="128" height="140" /></a></p>
In a nutshell, we are the <strong>lead developers and the maintainers of the two Linux-based WebKit ports</strong>, known as <a href="https://webkitgtk.org/"><strong>WebKitGTK</strong></a> and <a href="https://wpewebkit.org/"><strong>WPE</strong></a>. These ports share a common baseline (e.g. GLib, GStreamer, libsoup) and also some goals (e.g. performance, security), but other than that their purpose is different, with <strong>WebKitGTK being aimed at the Linux desktop</strong>, while <strong>WPE</strong> is mainly focused on <strong>embedded devices</strong>.

<a href="https://wpewebkit.org/"><img class="alignright wp-image-3259" style="margin-top: 0.857143rem; margin-bottom: 0.857143rem; margin-left: 1.71429rem;" src="/wp-content/uploads/2024/11/wpe-logo-300x140.png" alt="WPE logo" width="214" height="100" /></a>

This means that, while <strong>WebKitGTK is the go-to solution to embed Web content in GTK applications</strong> (e.g. GNOME Web/Epiphany, Evolution), and therefore integrates well with that graphical toolkit, <strong>WPE</strong> does not even provide a graphical toolkit since its main <strong>goal is to be able to run well on embedded devices</strong> that often don't even have a lot of memory or processing power, or not even the usual mechanisms for I/O that we are used to in desktop computers. This is why WPE's architecture is designed with flexibility in mind with a backends-based architecture, why it aims for using as few resources as possible, and why it tries to depend on as few libraries as possible, so you can integrate it virtually in any kind of embedded Linux platform.

Besides that port-specific work, which is what our WebKit and Multimedia teams focus a lot of their effort on, we <strong>also contribute at a different level in the port-agnostic parts of WebKit</strong>, mostly around the area of <strong>Web standards</strong> (e.g. contributing to Web specifications and to implement them) and the <strong>Javascript engine</strong>. This work is carried out by our Web Platform and Compilers team, which tirelessly contribute to the different parts of WebCore and JavaScriptCore that affect not just the WebKitGTK and WPE ports, but also the rest of them to a bigger or smaller degree.

Last but not least, we also devote a considerable amount of our time to other topics such as <strong>accessibility, performance, bug fixing, QA.</strong>.. and also to make sure WebKit works well on <strong>32-bit devices</strong>, which is an important thing for a lot of WPE users out there.
<h2>Who are our users?</h2>
At Igalia we distinguish <strong>4 main types of users</strong> of the <strong>WebKitGTK and WPE</strong> ports of WebKit:

<strong>Port users</strong>: this category would include anyone that writes a product directly against the port's API, that is, apps such as a desktop Web browser or embedded systems that rely on a fullscreen Web view to render its Web-based content (e.g. digital signage systems).

<strong>Platform providers</strong>: in this category we would have developers that build frameworks with one of the Linux ports at its core, so that people relying on such frameworks can leverage the power of the Web without having to directly interface with the port's API. <a href="https://rdkcentral.com/"><em>RDK</em></a> could be a good example of this use case, with WPE at the core of the so-called <a href="https://rdkcentral.github.io/Thunder/"><em>Thunder</em> plugin</a> (previously known as <a href="https://wiki.rdkcentral.com/pages/viewpage.action?pageId=90117335"><em>WPEFramework</em></a>).

<strong>Web developers</strong>: of course, Web developers willing to develop and test their applications against our ports need to be considered here too, as they come with a different set of needs that need to be fulfilled, beyond rendering their Web content (e.g. using the Web Inspector).

<strong>End users</strong>: And finally, the end user is the last piece of the puzzle we need to pay attention to, as that's what makes all this effort a task worth undertaking, even if most of them most likely don't need what WebKit is, which is perfectly fine :-)
<p dir="auto" data-sourcepos="144:1-145:74">We like to make this distinction of 4 possible types of users explicit because we think it's important to understand the complexity of the amount of use cases and the diversity of potential users and customers we need to provide service for, which is behind our decisions and the way we prioritize our work.</p>

<h2>Strategic goals</h2>
Our <strong>main goal</strong> is that our product, the WebKit web engine, is useful for more and more people in different situations. Because of this, it is i<span style="font-size: 1rem;">mportant that the </span><span style="font-size: 1rem;">platform is homogeneous</span><span style="font-size: 1rem;"> and that it can be used reliably with all the engines available nowadays, and this is why </span><span style="font-size: 1rem;"><strong>compatibility</strong> and <strong>interoperability</strong> is a must, and why we </span>work with the the standards bodies to help with the design and implementation of several Web specifications.

With WPE, it is very important to be able to run the engine in small <strong>embedded</strong> devices, and that requires good <strong>performance</strong> and being efficient in <a href="https://wpewebkit.org/about/supported-hardware.html">multiple hardware architectures</a>, as well as great <strong>flexibility</strong> for specific hardware, which is why we provided WPE with a <a href="https://wpewebkit.org/about/architecture.html">backend-based architecture</a>, and reduced dependencies to a minimum.

Then, it is a<span style="font-size: 1rem;">lso important that the <strong>QA </strong></span><span style="font-size: 1rem;">Infrastructure is good enough</span><span style="font-size: 1rem;"> to keep the releases working and with good quality, which is why I regularly maintain, evolve and keep an eye on the <a href="https://ews-build.webkit.org/"><em>EWS</em></a> and <a href="https://build.webkit.org/">post-commit bots</a> that keep WebKitGTK and WPE building, running and passing the tens of thousands of tests that we need to check continuously, to ensure we don't regress (or that we catch issues soon enough, when there's a problem). Then of course it's also important to keep</span><span style="font-size: 1rem;"> doing </span><span style="font-size: 1rem;"><strong>security</strong> releases</span><span style="font-size: 1rem;">, making sure that we release stable versions with fixes to the different <em>CVEs</em> reported as soon as possible.</span>

Finally, we also make sure that we keep evolving our <strong>tooling</strong> as much as possible (see for instance the release of the <a href="https://github.com/Igalia/webkit-container-sdk">new SDK</a> earlier this year), as well as improving the <strong>documentation</strong> for both ports.

Last, all this effort would not be possible if not because we also consider a goal of us to maintain an <strong>efficient collaboration</strong> with the rest of the WebKit community in different ways, from making sure we re-use and contribute to other ports as much code as possible, to making sure we communicate well in all the forums available (e.g. Slack, mailing list, annual meeting).
<h2>Contributions to WebKit in numbers</h2>
Well, first of all the usual disclaimer: number of commits is for sure not the best possible metric,  and therefore should be taken with a grain of salt. However, the point here is not to focus too much on the actual numbers but on the more general conclusions that can be extracted from them, and from that point of view I believe it's interesting to take a look at this data at least once a year.

<img class="aligncenter size-large wp-image-3229" src="/wp-content/uploads/2024/10/webkit-contributors-all-2024-800x453.png" alt="Igalia contributions to WebKit (2024)" width="625" height="354" />

With that out of the way, it's interesting to confirm that once again <a href="https://www.slideshare.net/slideshow/igalia-and-webkit-status-update-and-plans-72bd/272669557#12">we are still the <strong>2nd biggest contributor to WebKit after Apple</strong></a>, with ~13% of the commits landed in this past 12-month period. More specifically, we landed 2027 patches out of the 15617 ones that took place during the past year, only surpassed by Apple and their 12456 commits. The remaining 1134 patches were landed mostly by Sony, followed by RedHat and several other contributors.

<img class="aligncenter size-large wp-image-3226" src="/wp-content/uploads/2024/10/webkit-contributors-2024-800x433.png" alt="Igalia contributions to WebKit (2024)" width="625" height="338" />Now, if we remove Apple from the picture, we can observe how <a href="https://www.slideshare.net/slideshow/igalia-and-webkit-status-update-and-plans-72bd/272669557#13">this year our contributions represented <strong>~64% of all the non-Apple commits</strong></a>, a figure that grew about ~11% compared to the past year. This confirms once again our commitment to WebKit, a project we started contributing about 14 years ago already, and where we have been systematically being the 2nd top contributor for a while now.
<h2>Main areas of work</h2>
<div>

The <strong>10 main areas</strong> we have contributed to in WebKit in the past 12 months are the following ones:
<ul>
 	<li>Web platform</li>
 	<li>Graphics</li>
 	<li>Multimedia</li>
 	<li>JavaScriptCore</li>
 	<li>New WPE API</li>
 	<li>WebKit on Android</li>
 	<li>Quality assurance</li>
 	<li>Security</li>
 	<li>Tooling</li>
 	<li>Documentation</li>
</ul>
In the next sections I'll talk a bit about what we've done and what we're planning to do next for each of them.

</div>
<h3>Web Platform</h3>
<strong>content-visibility:auto</strong>

This feature allows skipping painting and rendering of off-screen sections, particularly u<span style="font-size: 1rem;">seful to avoid the browser spending time rendering parts in large pages, as content outside of the view doesn't get rendered until it gets visible.</span>

We c<span style="font-size: 1rem;">ompleted the implementation and it's now enabled by default.</span>

<strong>Navigation API</strong>

This is a new API to manage browser navigation actions and examine history, which we started working on in the past cycle. There's been a lot of work happening here and, while it's not finished yet, the current plan is that Apple will continue working on that in the next months.

<strong>hasUAVisualTransition</strong>

This is an attribute of the <a href="https://developer.mozilla.org/en-US/docs/Web/API/NavigateEvent">NavigateEvent interface</a>, which is meant to be <code>True</code> if the <em>User Agent</em> has performed a visual transition before a navigation event. It was something that we have also finished implementing and is now also enabled by default.

<strong>Secure Curves in the Web Cryptography API</strong>

In this case, we worked on fixing several <a href="https://wpt.fyi/interop-2024?stable">Web Interop</a> related issues, as well as on increasing test coverage within the <a href="https://web-platform-tests.org/">Web Platform Tests</a> (<em>WPT</em>) <a href="https://wpt.fyi">test suites</a>.

On top of that we also moved the <em>X25519</em> feature to the <em>"prepare to ship"</em> stage.

<strong>Trusted Types</strong>

This work is related to reducing DOM-based <a href="https://developer.mozilla.org/es/docs/Glossary/Cross-site_scripting"><em>XSS</em></a> attacks. Here we finished the implementation and this is now pending to be enabled by default.

<strong>MathML</strong>

We continued working on the <a href="https://w3c.github.io/mathml/">MathML specification</a> by working on the support<span style="font-size: 1rem;"> for padding, border and margin, as well as by increasing the </span><a href="https://wpt.fyi/results/mathml?label=master&amp;label=experimental&amp;aligned&amp;q=mathml"><em>WPT</em> score</a> by ~5%.

The plan for next year is to continue working on core features and improve the interaction with CSS.

<strong>Cross-root ARIA</strong>

Web components have accessibility-related issues with native <a href="https://developer.mozilla.org/en-US/docs/Web/API/Web_components/Using_shadow_DOM">Shadow DOM</a> as you cannot reference elements with <a href="https://www.w3.org/WAI/standards-guidelines/aria/">ARIA</a> attributes across boundaries. We haven't worked on this in this period, but the plan is to work in the next months on implementing the<span style="font-size: 1rem;"> Reference Target proposal to solve those issues.</span>

<strong>Canvas Formatted Text</strong>

Canvas has not a solution to add formatted and multi-line text, so we would like to also work on e<span style="font-size: 1rem;">xploring and prototyping the <a href="https://github.com/WICG/canvas-place-element">Canvas Place Element proposal</a> in WebKit, which allows better text in canvas and more extended features.</span>
<h3>Graphics</h3>
<strong>Completed migration from Cairo to Skia for the Linux ports</strong>

If you have followed the latest developments, you probably already know <a href="https://blogs.igalia.com/carlosgc/2024/02/19/webkit-switching-to-skia-for-2d-graphics-rendering/">that the Linux WebKit ports (i.e. WebKitGTK and WPE) have moved from Cairo to Skia for their 2D rendering library</a>, which was a pretty big and important decision taken after a long time trying different approaches and experiments (including developing our own HW-accelerated 2D rendering library!), as well as running several tests and measuring results in different benchmarks.

<a href="https://skia.org/"><img class="alignright wp-image-3274" src="/wp-content/uploads/2024/11/skia-logo-300x166.png" alt="Skia logo" width="181" height="100" /></a>The results in the end were pretty overwhelming and we decided to give <a href="https://skia.org/">Skia</a> a go, and we are happy to say that, as of today, the <strong>migration has been completed</strong>: we covered<span style="font-size: 1rem;"> all the use cases in Cairo, achieving <strong>feature parity</strong>, and we are now working on implementing <strong>new features and improvements</strong> built on top of Skia (e.g. GPU-based 2D rendering).</span>

On top of that, <strong>Skia is now the default backend for WebKitGTK and WPE since 2.46.0</strong>, released on September 17th, so if you're building a recent version of those ports you'll be already using Skia as their 2D rendering backend. Note that Skia is using its GPU-based backend only on desktop environments, on embedded devices the situation is trickier and for now the default is the CPU-based Skia backend, but we are actively working to narrow the gap and to enable GPU-based rendering also on embedded.

<strong>Architecture changes with buffer sharing APIs (DMABuf)</strong>

We did a lot of work here, such as a big refactoring of the fencing system to control the access to the buffers, or the continued work towards integrating with Apple's DisplayLink infrastructure.

On top of that, we also enabled more efficient composition using damaging information, so that we don't need to pass that much information to the compositor, which would slow the CPU down.

<strong>Enablement of the GPUProcess</strong>

On this front, we enabled by default the compilation for WebGL rendering using the GPU process, and we are currently working in performance review and enabling it for other types of rendering.

<strong>New SVG engine (<em data-sourcepos="476:23-476:28">LBSE</em>: <em data-sourcepos="476:31-476:70">Layer-Based SVG Engine</em>)</strong>

If you are not familiar with this, here the idea is to make sure that we reuse the graphics pipeline used for HTML and CSS rendering, and use it also for SVG, instead of having its own pipeline. This means, among other things, that SVG layers will be supported as a 1st-class citizen in the engine, enabling HW-accelerated animations, as well as support for 3D transformations for individual SVG elements.

<a href="https://wpewebkit.org/blog/status-of-lbse-in-webkit.html"><img class="alignright wp-image-3265 size-thumbnail" src="/wp-content/uploads/2024/11/lbse-logo-wide-e1730466411905-150x150.png" alt="LBSE logo" width="150" height="150" /></a>

<span style="font-size: 1rem;">On this front, on this cycle we </span><strong style="font-size: 1rem;">a<span style="font-size: 1rem;">dded support for the missing features</span></strong><span style="font-size: 1rem;"><strong> in the LBSE</strong>, namely:</span>
<ul>
 	<li>Implemented support for gradients &amp; patterns (applicable to both fill and stroke)</li>
 	<li>Implemented support for clipping &amp; masking (for all shapes/text)</li>
 	<li>Implemented support for markers</li>
 	<li>Helped review implementation of SVG filters (done by Apple)</li>
</ul>
Besides all this, we also <strong>improved the performance of the new layer-based engine</strong> by reducing<span style="font-size: 1rem;"> repaints and re-layouts as much as possible (further optimizations still possible), narrowing the </span>performance gap with the current engine for MotionMark. While we are still not at the same level of performance as the current SVG engine, we are confident that there are several key places where, with the right funding, we should be able to improve the performance to at least match the current engine, and therefore be able to push the new engine through the finish line.

<strong>General overhaul of the graphics pipeline, touching different areas (WIP):</strong>

On top of everything else commented above, we also worked on a general refactor and simplification of the graphics pipeline. For instance, we have been working on the removal of the Nicosia layer now that we are not planning to have multiple rendering implementations, among other things.
<h3>Multimedia</h3>
<strong>DMABuf-based sink for HW-accelerated video</strong>

We merged the <strong data-sourcepos="506:10-506:30">DMABuf-based sink</strong> for HW-accelerated video in the GL-based GStreamer sink.

<strong>WebCodecs backend</strong>

We completed the implementation of  audio/video encoding and decoding, and this is now enabled<span style="font-size: 1rem;"> by default in 2.46. As for the next steps, we plan to keep working on the integration of <a href="https://developer.mozilla.org/en-US/docs/Web/API/WebCodecs_API">WebCodecs</a> with <a href="https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API">WebGL</a> and <a href="https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API">WebAudio</a>.</span>

<strong>GStreamer-based WebRTC backends</strong>

We continued working on <a href="https://gstreamer.freedesktop.org/documentation/webrtclib/index.html?gi-language=c">GstWebRTC</a>, bringing it to a point where it can be used in production in some specific use cases, and we will still be working on this in the next months.

<strong>Other</strong>

Besides the points above, we also added an <strong>optional text-to-speech backend based on <a href="https://github.com/project-spiel/libspiel">libspiel</a></strong> to the development branch, and worked on <strong>general maintenance</strong> around the support for <a href="https://www.w3.org/TR/media-source-2/"><em>Media Source Extensions</em></a> (<em>MSE</em>) and <a href="https://www.w3.org/TR/encrypted-media-2/"><em>Encrypted Media Extensions</em></a> (<em>EME</em>), which are crucial for the use case of WPE running in set-top-boxes, and is a permanent task we will continue to work on in the next months.
<h3>JavaScriptCore</h3>
<strong>ARMv7/32-bit support:</strong>

A lot of work happened around <strong>32-bit support in JavaScriptCore</strong>, especially around <a href="https://webassembly.org/">WebAssembly</a> (WASM): we p<span style="font-size: 1rem;">orted the WASM<em> BBQJIT</em> and p</span>orted/enabled concurrent JIT support, and we also <strong>completed 80% of the implementation for the <em>OMG</em> optimization level</strong> of <em>WASM</em>, which we plan to finish in the next months. If you are unfamiliar with what the <em>OMG</em> and <em>BBQ</em> optimization tiers in WASM are, I'd recommend you to take a look at this article in webkit.org: <em>"<a href="https://webkit.org/blog/7691/webassembly/">Assembling WebAssembly</a>"</em>.

<a href="https://webassembly.org/"><img class="alignright wp-image-3281 size-thumbnail" src="/wp-content/uploads/2024/11/wasm-logo-150x150.png" alt="WASM logo" width="150" height="150" /></a>We also contributed to the <strong>JIT-less WASM,</strong> which is very u<span style="font-size: 1rem;">seful for embedded systems that can't support JIT for security or memory related constraints, and also did some</span><span style="font-size: 1rem;"><strong> work on the In-Place Interpreter (<em>IPInt</em>)</strong>, which is a new version of the WASM Low-level interpreter (LLInt) that uses less memory and e</span><span style="font-size: 1rem;">xecutes WASM bytecode directly without translating it to LLInt bytecode  (and should therefore be faster to execute).</span>

Last, we also contributed most of the implementation for the <a href="https://github.com/WebAssembly/gc"><strong>WASM GC</strong></a>, with the exception of some Kotlin tests.

As for the next few months, we plan to investigate and optimize heap/JIT memory usage in 32-bit, as well as to finish several other improvements on ARMv7 (e.g. IPInt).
<h3>New WPE API</h3>
The new WPE API is a <strong>new API that aims at making it easier to use WPE in embedded devices</strong>, by removing the hassle of having to handle several libraries in tandem (i.e. <a href="https://github.com/webKit/WebKit/"><em>WPEWebKit</em></a>, <a href="https://github.com/WebPlatformForEmbedded/libwpe"><em>libWPE</em></a> and <a href="https://github.com/Igalia/WPEBackend-fdo"><em>WPEBackend-FDO</em></a>, for instance), available from <a href="https://wpewebkit.org/release/">WPE's releases page</a>, and providing a more modern API in general, better aimed at the most common use cases of WPE.

A lot of effort happened this year along these lines, including the fact that we finally <strong>upstreamed and shipped its initial implementation with WPE 2.44</strong>, back in the first half of the year. Now, while we recommend users to give it a try and report feedback as much as possible, this new API is still not set in stone, with regular development still<span style="font-size: 1rem;"> ongoing, so if you have the chance to try it out and share your experience, comments are welcome!</span>

Besides shipping its initial implementation, we also <strong>added support for external platforms</strong>, so that other ones can be loaded beyond the <a href="https://wayland.freedesktop.org/"><em>Wayland</em></a>, <a href="https://www.kernel.org/doc/html/v4.15/gpu/drm-mm.html"><em>DRM</em></a> and "headless" ones, which are the default platforms already included with WPE itself. This means for instance that a <a href="https://docs.gtk.org/gtk4/">GTK4</a> platform, or another one for <em>RDK</em> could be easily used with WPE.

Then of course <strong>a lot of API additions</strong> were included in the new API in the latest months:
<ul>
 	<li><strong><span style="font-size: 1rem;">Screens management API</span></strong><span style="font-size: 1rem;">:  </span>API to handle different screens, ask the display for the list of screens with their device scale factor, refresh rate, geometry...</li>
 	<li><strong><span style="font-size: 1rem;">Top level management API</span></strong><span style="font-size: 1rem;">: </span>This API allows a greater degree of control, for instance by allowing more than one WebView for the same top level, as well as allowing to retrieve properties such as size, scale or state (i.e. full screen, maximized...).</li>
 	<li><strong>Maximized and minimized windows API</strong>: API to maximize/minimize a top level and monitor its state. mainly used by WebDriver.</li>
 	<li><span style="font-size: 1rem;"><strong>Preferred DMA-BUF formats API</strong>: enables asking</span> the platform (compositor or DRM) for the list of preferred formats and their intended use (scanout/rendering).</li>
 	<li><span style="font-size: 1rem;"><strong>Input methods API</strong>: </span>allows platforms to provide an implementation to handle input events (e.g. virtual keyboard, autocompletion, auto correction...).</li>
 	<li><span style="font-size: 1rem;"><strong>Gestures API</strong>: </span>API to handle gestures (e.g. tap, drag).</li>
 	<li><span style="font-size: 1rem;"><strong>Buffer damaging</strong>: </span>WebKit generates information about the areas of the buffer that actually changed and we pass that to DRM or the compositor to optimize painting.</li>
 	<li><span style="font-size: 1rem;"><strong>Pointer lock API</strong>: allows the WebView to lock the pointer so that the movement of the pointing device (e.g. mouse) can be used for a different purpose (e.g. first-person shooters).</span></li>
</ul>
Last, we also <strong>added support for testing automation</strong>, and we can support <strong>WebDriver</strong> now in the new API.

With all this done so far, the plan now is to complete the new WPE API, with a focus on the Settings API and accessibility support, write API tests and documentation, and then also add an external platform to support GTK4. This is done on a best-effort basis, so there's no specific release date.
<h3>WebKit on Android</h3>
This year was also a good year for WebKit on Android, also known as WPE Android, as this is a project that sits on top of WPE and its public API (instead of developing a fully-fledged WebKit port).

<a href="https://www.android.org"><img class="alignright wp-image-3283" src="/wp-content/uploads/2024/11/android-logo-300x184.png" alt="Android logo" width="200" height="122" /></a>In case you're not familiar with this, the idea here is to provide a <strong>WebKit-based alternative to the Chromium-based Web view on Android devices</strong>, in a way that leverages HW acceleration when possible and that it integrates natively (and nicely) with the several Android subsystems, and of course with Android's native mainloop. Note that this is an experimental project for now, so don't expect production-ready quality quite yet, but hopefully something that can be used to start experimenting with selected use cases.

If you're adventurous enough, you can already try the APKs yourself from the releases page in GitHub at <a href="https://github.com/Igalia/wpe-android/releases">https://github.com/Igalia/wpe-android/releases</a>.

Anyway, as for the <strong>changes that happened in the past 12 months</strong>, here is a summary:
<ul>
 	<li><strong>Updated</strong> WPE Android to <strong>WPE 2.46 and NDK 27 LTS</strong></li>
 	<li>Added <strong>support for WebDriver</strong> and included <strong>WPT test suites</strong></li>
 	<li>Added <strong>support for instrumentation tests</strong>, and integrated with the GitHub CI</li>
 	<li>Added <strong>support for the remote Web inspector</strong>, very useful for debugging</li>
 	<li>Enabled the <strong>Skia backend,</strong> bringing HW-accelerated 2D rendering to WebKit on Android</li>
 	<li>Implemented <strong>prompt delegates</strong>, allowing implementing things such as alert dialogs</li>
 	<li>Implemented <strong>WPEView client interfaces</strong>, allowing responding to things such as HTTP errors</li>
 	<li>Packaged a <strong>WPE-based Android WebView in its own library and published in Maven Central</strong>. This is a massive improvement as now apps can use WPE Android by simply referencing the library from the gradle files, no need to build everything on their own.</li>
 	<li>Other changes: enabled HTTP/2 support (via the migration to libsoup3), added support for the device scale factor, improved the virtual on-screen keyboard, general bug fixing...</li>
</ul>
On top of that, we published <strong>3 different blog posts</strong> covering different topics, from a general intro to a more deep dive explanation of the internals, and showing some demos. You can check them out in Jani's blog at <a href="https://blogs.igalia.com/jani/bringing-webkit-back-to-android" target="_blank" rel="nofollow noreferrer noopener">https://blogs.igalia.com/jani</a>

As for the future, we'll focus on stabilization and regular maintenance for now, and then we'd like to work towards achieving production-ready quality for specific cases if possible.
<h3>Quality Assurance</h3>
On the QA front, we had a busy year but in general we could highlight the following topics.
<ul>
 	<li><strong>Fixed a<span style="font-size: 1rem;"> lot of </span></strong><span style="font-size: 1rem;"><strong>API tests failures</strong> in the bots that were limiting our test coverage.</span></li>
 	<li><strong>Fixed lots of assertions-related crashes</strong> in the bots, which were slowing down the bots as well as causing other types of issues, such as bots exiting early due too many failures.</li>
 	<li><strong>Enabled assertions in the release bots</strong>, which will help prevent crashes in the future, as well as with making our debug bots healthier.</li>
 	<li><strong>Moved all the WebKitGTK and WPE bots to building now with Skia</strong> instead of Cairo. This means that all the bots running tests are now using Skia, and there's only one bot still using Cairo to make sure that the compilation is not broken, but that bot does not run tests.</li>
 	<li><strong>Moved all the WebKitGTK bots to use GTK4 by default</strong>. As with the move to Skia, all the WebKit bots running tests now use GTK4 and the only one remaining building with GTK3 does not run tests, it only makes sure we don't break the GTK3 compilation for now.</li>
 	<li><strong>Working on moving all the bots to use the new SDK</strong>. This is still work in progress and will likely be completed during 2025 as it's needed to implement several changes in the infrastructure that will take some time.</li>
 	<li><strong>General gardening and bot maintenance</strong></li>
</ul>
In the next months, our main focus would be a revamp of the QA infrastructure to make sure that we can get all the bots (including the debug ones) to a healthier state, finish the migration of all the bots to the new SDK and, ideally, be able to bring back the ready-to-use WPE images that we used to have available in wpewebkit.org.
<h3>Security</h3>
The current release cadence has been working well, so we continue issuing <strong>major releases every 6 months</strong> (March, September), and then <strong>minor and unstable development releases</strong> happening <strong>on-demand</strong> when needed.

As usual, we kept <strong>aligning releases for WebKitGTK and WPE</strong>, with both of them happening at the same time (see <a href="https://webkitgtk.org/releases">https://webkitgtk.org/releases</a> and <a href="https://wpewebkit.org/release">https://wpewebkit.org/release</a>), and then also publishing <strong style="font-size: 1rem;">WebKit Security Advisories (<em data-sourcepos="697:37-697:41">WSA</em>)</strong> when necessary, both <a href="https://webkitgtk.org/security.html">for WebKitGTK</a> and <a href="https://wpewebkit.org/security">for WPE</a>.

Last, we also <strong>shortened the time before including security fixes in stable releases</strong> this year, and we have removed support for <a href="https://wiki.gnome.org/Projects/libsoup"><em>libsoup2</em></a> from WPE, as that library is no longer maintained.
<h3>Tooling &amp; Documentation</h3>
On <strong>tooling</strong>, the main piece of news is that this year we r<span style="font-size: 1rem;">eleased the initial version of the <a href="https://github.com/Igalia/webkit-container-sdk">new SDK</a>,  which is developed on top of <a href="https://opencontainers.org/">OCI</a>-based containers. This new SDK fixes the issues with the current existing approaches based on <a href="https://www.freedesktop.org/wiki/Software/jhbuild/">JHBuild</a> and <a href="https://flatpak.org/">flatpak</a>, where one of them was great for development but poor for testing and QA, and the other one was great for testing and QA, but not very convenient for development.</span>

<span style="font-size: 1rem;">This new SDK is <strong>regularly maintained</strong> and currently runs on <a href="https://ubuntu.com/blog/tag/ubuntu-24-04-lts">Ubuntu 24.04 LTS</a> with <a href="https://gcc.gnu.org/gcc-14/">GCC 14</a> &amp; <a href="https://releases.llvm.org/18.1.0/tools/clang/docs/index.html">Clang 18</a>. It has been m</span>ade public on GitHub and <a href="https://blog.tingping.se/2024/05/23/Introducing-WebKit-Container-SDK.html">announced to the public in May 2024 in Patrick's blog</a>, and is <strong>now the officially recommended way</strong> of building WebKitGTK and WPE.

As for <strong>documentation</strong>, we didn't do as much as we would have liked here, but we still landed a few contributions in <a href="http://docs.webkit.org">docs.webkit.org</a>, mostly related to WebKitGTK (e.g. <a href="https://docs.webkit.org/Ports/WebKitGTK%20and%20WPE%20WebKit/ReleasesAndVersioning.html" target="_blank" rel="nofollow noreferrer noopener" data-sourcepos="723:5-723:118">Releases and Versioning</a>, <a href="https://docs.webkit.org/Ports/WebKitGTK%20and%20WPE%20WebKit/SecurityUpdates.html" target="_blank" rel="nofollow noreferrer noopener" data-sourcepos="724:5-724:105">Security Updates</a>, <a href="https://docs.webkit.org/Ports/WebKitGTK%20and%20WPE%20WebKit/Multimedia.html" target="_blank" rel="nofollow noreferrer noopener" data-sourcepos="725:5-725:94">Multimedia)</a>. We plan to do more on this regard in the next months, though, mostly by writing/publishing more documentation and perhaps also some tutorials.
<h2>Final thoughts</h2>
This has been a fairly long blog post but, as you can see, it's been quite a year for WebKit here at Igalia, with many exciting changes happening at several fronts, and so there was quite a lot of stuff to comment on here. This said, you can always check the <a href="https://www.slideshare.net/slideshow/igalia-and-webkit-status-update-and-plans-72bd/272669557">slides of the presentation in the WebKit Contributors Meeting here</a> if you prefer a more concise version of the same content.

In any case, what's clear it's that the next months are probably going to be quite interesting as well with all the work that's already going on in WebKit and its Linux ports, so it's possible that in 12 months from now I <em>might </em>be writing an equally long essay. We'll see.

Thanks for reading!
