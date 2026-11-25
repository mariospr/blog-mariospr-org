---
title: "Igalia and WebKit: status update and plans (2026)"
date: 2026-11-25T10:00:00+00:00
slug: igalia-and-webkit-status-update-and-plans-2026
categories:
  - Planet GNOME
  - Planet GPUL
  - Planet Igalia
  - Planet WebKitGTK
  - Planeta GNOME Hispano
  - WebKit
  - WebKitGTK
  - WPE
---

Two years ago I wrote a [long post summarizing Igalia's work on WebKit](/2024/11/03/igalia-and-webkit-status-update-and-plans-2024/), based on my presentation at the [WebKit Contributors Meeting](https://webkit.org/meeting/), and I closed the post saying that I *might* be writing another post in 12 months. Well, that didn't happen, but here I am again :-)

Fast-forward to today: a bit over a month ago, I attended the **WebKit Contributors Meeting 2026** in Cupertino, where once again I presented [an overview of what we at Igalia did in WebKit over the past 12 months](https://speakerdeck.com/mariospr/igalia-and-webkit-status-update-and-plans-2026), and what we are planning to do next. The session was not recorded, so this post is a more accessible version of that presentation.

<p style="text-align: center;"><a href="https://www.igalia.com"><img src="/images/2026/11/igalia-logo.png" alt="Igalia logo" width="300" height="108" style="display: inline-block; vertical-align: middle; width: 50%; max-width: 300px; height: auto; margin: 0 3%;" /></a><a href="https://webkit.org"><img src="/images/2026/11/webkit-logo.svg" alt="WebKit logo" width="100" height="108" style="display: inline-block; vertical-align: middle; width: 17%; max-width: 100px; height: auto; margin: 0 3%;" /></a></p>

## Igalia and WebKit, in a nutshell

In case you're new to this: we at [Igalia](https://www.igalia.com) are the **maintainers of the two Linux-based WebKit ports**: [WebKitGTK](https://webkitgtk.org), aimed at the Linux desktop and GTK applications (e.g. GNOME Web), and [WPE](https://wpewebkit.org), mainly focused on **embedded devices**. On top of that, we also contribute to the port-agnostic parts of WebKit, such as **Web standards** and **JavaScriptCore**, and this work is spread across several teams at Igalia (WebKit, Web Platform, Compilers, Multimedia...).

As for the embedded side of things, WPE runs on a surprising variety of devices nowadays: set-top boxes and TVs, smart home appliances, digital signage, car infotainment systems, audio systems... and sometimes even devices without a screen at all!

<p style="text-align: center;"><img src="/images/2026/11/wpe-based-products.png" alt="Examples of WPE-based products: a smart TV, a tablet, a smart fridge, a car infotainment system, a digital signage totem and a set-top box" width="1400" height="238" /></p>

This variety of devices and users (port users, platform providers, Web developers and end users) is what drives our **strategic goals**, which haven't changed much since last time:

* **Compatibility and interoperability**: a homogeneous Web platform, reliable across engines.
* **Performance on embedded devices**: efficient on small hardware, flexible for specific hardware.
* **Quality assurance and security**: green bots, timely releases and security advisories.
* **Tools, documentation and collaboration**: better tooling, ports alignment and working together upstream.

## The numbers

The usual disclaimer first: the number of commits is not a great metric, so please bear that in mind. Still, I think it gives a reasonable idea of the general trends, so here's what we got for the period between October 1st 2025 and October 1st 2026:

<p style="text-align: center;"><img src="/images/2026/11/webkit-commits-2026.png" alt="Donut charts of the commits to WebKit between October 2025 and October 2026: Apple 81.25%, Igalia 13.11%, Bun 2.28% and Other 3.35%; excluding Apple, Igalia accounts for ~70% of the commits" width="1100" height="560" /></p>

* Igalia landed **2831 commits**, **~53% more than last year** (1854), while the total number of commits grew ~33% (from 16293 to 21591).
* We are still the **2nd biggest contributor after Apple**, with **13.11%** of all the commits.
* If we leave Apple out of the picture, **~70% of the remaining commits** came from Igalia.
* **46 different Igalians** committed to WebKit in this period.

Another interesting change this year is that [Bun](https://bun.sh) (Oven) is now the 3rd biggest committer, mostly with work on JSC, while Sony and Red Hat are now part of the "Other" category.

## Main areas of work

As in previous years, there was a lot going on, so I've grouped our work into these areas:

<ul class="work-areas">
  <li><a href="#web-platform"><span class="work-area-icon" aria-hidden="true">🌐</span>Web Platform</a></li>
  <li><a href="#graphics"><span class="work-area-icon" aria-hidden="true">🎨</span>Graphics</a></li>
  <li><a href="#multimedia"><span class="work-area-icon" aria-hidden="true">🎧</span>Multimedia</a></li>
  <li><a href="#javascriptcore"><span class="work-area-icon" aria-hidden="true">⚙️</span>JavaScriptCore</a></li>
  <li><a href="#wpeplatform-api"><span class="work-area-icon" aria-hidden="true">🧩</span>WPEPlatform API</a></li>
  <li><a href="#webkit-on-android"><span class="work-area-icon" aria-hidden="true"><img src="/images/2026/11/android-head.svg" alt="" width="28" height="16" /></span>WebKit on Android</a></li>
  <li><a href="#swift-in-the-linux-ports"><span class="work-area-icon" aria-hidden="true"><img src="/images/2026/11/swift-logo.svg" alt="" width="22" height="22" /></span>Swift in the Linux ports</a></li>
  <li><a href="#quality-assurance"><span class="work-area-icon" aria-hidden="true">✅</span>Quality assurance</a></li>
  <li><a href="#security"><span class="work-area-icon" aria-hidden="true">🛡️</span>Security</a></li>
  <li><a href="#development-tools"><span class="work-area-icon" aria-hidden="true">🧰</span>Development tools</a></li>
</ul>

For each of them, I'll go through the highlights of the past 12 months, followed by what we're planning to do next.

### Web Platform {#web-platform}

We worked on a wide range of Web Platform features in this cycle, such as:

* **MathML**: implemented and improved CSS features (e.g. `math-depth`), and added support for the `<a>` element. With this, **MathML Core support is now on par with other engines**.
* **Close Watcher API**: updated to align with the latest specification changes, and **shipped in stable** together with the new `<dialog closedby>` attribute.
* **CSS**: `scroll-axis-lock` and `scroll-state()` queries (behind a flag), `line-clamp`, `max-lines` and `block-ellipsis` aligned with the spec, and `scrollbar-color` support for the Linux ports.
* **WebXR on Linux**, based on OpenXR: implemented the **Hit Testing**, **Layers** and **Hand Input** modules (see [Sergio's blog post](https://blogs.igalia.com/svillar/post/wpe-webxr/) for more details).
* **Atomic move DOM API** (`moveBefore()`) and **Compression Dictionary Transport**, both in progress behind a runtime flag.
* **Other**: fixes to align **Trusted Types** with the specification, more work on porting the **WebExtensions** code from Objective-C++ to C++ so it can be exposed on Linux, shipped the `:open` pseudo-class and `ToggleEvent.source`, a new `aamtest` test type in WPT (see [Manuel's blog post](https://blogs.igalia.com/mrego/aamtest-testing-accessibility-in-wpt/)), and the Storage and File System APIs on the Linux ports.

#### Next steps

On the MathML side, we want to enable the new `mathvariant` behavior and the MathML Core features by default. We also plan to finish `moveBefore()`, `scroll-state()` queries and `scroll-axis-lock` so that they can be enabled, and to complete `line-clamp` so that it passes all the WPT tests. Compression Dictionary Transport should be enabled by default as well, once Apple ports are supported.

As for WebXR, the plan is to implement the **Plane Detection** and **Anchors** modules.

### Graphics {#graphics}

<a href="https://skia.org"><img class="alignright" src="/images/2026/11/skia-logo.svg" alt="Skia logo" width="160" height="88" /></a>

This was a big year on the graphics front, starting with the fact that **Cairo is gone**: [Skia](https://skia.org) is now the only 2D rendering backend for the Linux ports, with 2.54 being the first release without Cairo.

On top of that:

* **New Skia-based compositor** replacing TextureMapper, **enabled by default since 2.54**. It brought better damage tracking (only the damaged region is recomposited now, crucial for embedded), rendering fixes for 3D transforms and `backdrop-filter`, blend modes and faster filters. Carlos and Niko wrote about it in their blogs ([here](https://blogs.igalia.com/carlosgc/2026/09/21/skia-compositor-for-wpe-webkit-and-webkitgtk/) and [here](https://blogs.igalia.com/nzimmermann/posts/2026-09-21-skia-compositor-damaging/)).
* **Skia painting performance**: 2D canvas operations are now recorded and replayed in batches, many small image uploads are turned into one thanks to a GPU texture atlas, and painting workers no longer use GL thanks to Deferred Display Lists.
* **Frame scheduling** is now driven by **RunLoop observers**, like in Apple's ports.
* **Async scrolling** improved for wheel events, and now also supports touch events.
* **Zero-copy GPU buffers** (dma-buf/GBM): more robust memory-mapped buffers (e.g. no more hangs on v3d), and support for Vivante super-tiled formats.
* **Layer-Based SVG Engine** (LBSE): a big push in this cycle, creating layers only when needed (less memory) and bringing it on par with the legacy engine in MotionMark's *Suits* test, plus many correctness fixes. Check out Niko's posts on [conditional layers](https://blogs.igalia.com/nzimmermann/posts/2026-07-14-lbse-conditional-layers/) and [paint order segments](https://blogs.igalia.com/nzimmermann/posts/2026-07-22-lbse-paint-order-segments/) for the details. He also recently wrote an amazingly detailed blog post about the same content he presented at the WKCM: ["Making LBSE performant"](https://blogs.igalia.com/nzimmermann/posts/2026-10-21-lbse-performance/).
* **Other**: fixed the performance of the WebGL implementation in the **GPUProcess**, improved font rendering with Skia, a non-composited mode for devices with weak or no GPU, dynamic MSAA and Display-P3 support for accelerated 2D canvas, and some (experimental) groundwork for Vulkan.

All this work is reflected in the performance numbers. For instance, these are the MotionMark results on a 64-bit Raspberry Pi 4, compared to July 2024, when we started tracking them in our [performance dashboard](https://wpe-perf-dashboard.igalia.com):

<p style="text-align: center;"><img src="/images/2026/11/motionmark-rpi4-2026.png" alt="Bar chart of MotionMark 1.3 scores on a 64-bit Raspberry Pi 4, relative to July 2024: the overall score is 2.5 times higher in October 2025 and 3.2 times higher in October 2026" width="1200" height="600" /></p>

The overall score grew **~29% in the last year** (from 639.41 to 824.51), and it's now **~3.2× higher than in July 2024**. The biggest gains in the past year came from the Skia painting work mentioned above, with *Canvas lines* (+91%), *Design* (+74%), *Leaves* (+40%) and *Canvas arcs* (+32%) leading the way.

#### Next steps

We want to bring the composition-related WPT failures down to zero and remove TextureMapper completely. Beyond that, we're planning to switch to Skia *Graphite*, to isolate the composition state from rendering to allow for more parallelism, and to support zero-copy offscreen canvas in workers.

We'll also keep moving parts of the graphics pipeline to the GPUProcess, try Skia's GPU backend with Vulkan, and close the remaining gap between LBSE and the current engine.

### Multimedia {#multimedia}

* **Switched from GstWebRTC to LibWebRTC** in the Linux ports, plugging GStreamer-based **hardware encoders and decoders** into it. The GstWebRTC backend was removed from the main branch in July 2026, and WebRTC is disabled in 2.54, to be enabled by default again in 2.56.
* **Player suspension** in pages with many media elements: hidden, muted or off-viewport players are now suspended, which frees up decoders.
* **Other**: MSE and EME improvements (e.g. `changeType()`, H.264 edit lists in MP4), hardware video decoding and encoding on Qualcomm platforms, and the usual maintenance and bug fixing.

#### Next steps

On the WebRTC side, we'll work on AV1 encoding, mDNS support and fixes for MediaStream track cloning, and LibWebRTC will be enabled by default in 2.56.

Like with the graphics pipeline, we also want to run media playback in the **GPUProcess** (as Apple ports do), and to make **quality changes smoother** in MSE video playback by switching quality without flushing the pipeline (so, no more stuttering).

### JavaScriptCore {#javascriptcore}

* **32-bit support**: we added BBQ/OMG optimizations for **the last release with a 32-bit JIT** (2.52), and then removed the ARMv7 JIT tiers, WebAssembly and big-endian support, among other things. WebKitGTK and WPE 2.54+ still work on 32-bit, but **only with CLoop**, which is slow.
* **Memory improvements** for long-running apps, which helps with embedded use cases where WPE is not restarted *for months*.
* **Temporal API** aligned with the **Stage 4** spec (22 PRs landed), with full support for `PlainMonthDay` and `PlainYearMonth`. We also completed `ZonedDateTime` and relative time computations, although that work was superseded by the move to a port of the `temporal_rs` library, for which our extensive tests of Temporal edge cases served as a safety net. More details in [this blog post](https://blogs.igalia.com/compilers/2026/02/02/implementing-the-temporal-proposal-in-javascriptcore/).
* **Other**: profiling and debugging tooling (e.g. samply, sysprof integration), PGO builds with Yocto, better Linux integration (e.g. time zone change notifications) and some small wins on JetStream.

#### Next steps

We'll keep working on memory and performance improvements for embedded (feedback from WPE users is critical here), as well as on better tooling to find memory leaks between JavaScript and native code in long-running apps.

### WPEPlatform API {#wpeplatform-api}

<a href="https://wpewebkit.org"><img class="alignright" src="/images/2026/11/wpe-logo.svg" alt="WPE logo" width="160" height="75" /></a>

The new WPEPlatform API, which I already talked about [two years ago](/2024/11/03/igalia-and-webkit-status-update-and-plans-2024/) as "the new WPE API", is now **stable**, and has been **enabled by default since WPE 2.54**. This means that the legacy API (i.e. libwpe) will be **deprecated soon**, so embedders should start migrating now.

Before declaring it stable, we added the last bits of API that were still missing (e.g. toplevels, clipboard, accessibility settings, gamepad rumble...) and validated its design with several out-of-tree platforms, such as WPE Android, [wpe-platform-gtk](https://github.com/Igalia/wpe-platform-gtk) and the [Wig browser](https://github.com/Igalia/wig). We also fixed many issues with touch, gestures, scrolling and memory safety, and **completed the documentation**, including guides on writing a launcher or a platform implementation, and on migrating from libwpe. You can find it all at [wpewebkit.org/reference](https://wpewebkit.org/reference/2.54.0/wpe-platform-2.0/).

#### Next steps

The plan is to deprecate the legacy API, since 2.56 will always enable WPEPlatform, and to close the remaining gaps (e.g. a replacement for the video plane extension, input methods and cursors). We also want to add more API tests, finish the documentation and help embedders migrate from the old API.

### WebKit on Android {#webkit-on-android}

<img class="alignright" src="/images/2026/11/wpe-android-minibrowser.jpg" alt="WPE Android's MiniBrowser showing igalia.com on a phone" width="180" height="400" />

[WebKit on Android](https://github.com/Igalia/wpe-android) made a lot of progress this year as well:

* **Migrated to WPEPlatform**: libwpe, WPEBackend-android and the legacy API have been removed.
* **Native integration** with Android graphics (e.g. zero-copy `AHardwareBuffer` backing store, `AChoreographer` for vsync).
* **New Java API** modeled after `android.webkit.WebView`, to which the MiniBrowser, MediaPlayer, WebDriver and the tests were ported.
* **Testing and QA**: our own external CI, running the W3C and WebDriver tests, and gardening after every (roughly weekly) rebase on WebKit's trunk.
* **WebXR on Android**, via OpenXR, opening the door to more XR devices.

Interestingly enough, testing on Android devices also exposed issues in the Skia compositor and in scrolling, whose fixes benefit all the Linux ports. Still, keep in mind that this is an ongoing effort, and the support is still **experimental**.

#### Next steps

We want to close the remaining platform gaps, such as input methods, permission dialogs, scrolling and `AHardwareBuffer` readback for snapshots, and to add more APIs (e.g. permissions, screenshots, SSL errors, media and capture callbacks...).

We'll also keep improving testing and get WebKit on Android into **WebKit's own CI**.

<div style="clear: both;"></div>

### Swift in the Linux ports {#swift-in-the-linux-ports}

<img class="alignright" src="/images/2026/11/swift-logo.svg" alt="Swift logo" width="80" height="80" />

As Apple is adopting Swift (with C++ interoperability) in WebKit, the Linux ports need to be able to build it too. On this front, we enabled **Clang by default in the CI** (with one GCC builder remaining), enabled building with Swift in the CI, added the **Swift toolchain to the WebKit Container SDK** (switching to our own build of it to fit our needs, e.g. a working `lldb`), fixed several build issues, and ran some early experiments to cross-build it with Yocto.

#### Next steps

The goal is to **enable Swift by default** in the next stable release of the Linux ports (2.56, expected in March 2027), and to support the Swift toolchain in the [meta-webkit](https://github.com/Igalia/meta-webkit) Yocto layer as well.

### Quality assurance {#quality-assurance}

The main highlight here is that the **bots are green again** 🟢, after a lot of gardening work on x86_64 and ARM64, and a cleanup of stale expectations for flaky tests. This was a lot of work as well, and it's probably better explained with a picture: the number of unexpected regressions per run went from over 100 at the end of 2025 to single digits:

<p style="text-align: center;"><img src="/images/2026/11/regressions-2026.png" alt="Line chart of unexpected regressions per run over time, for the GTK and WPE bots, going from over 100 at the end of 2025 to single digits for all bots by autumn 2026" width="1713" height="1048" /></p>

Note that this didn't happen at the expense of test coverage, as the number of passing tests kept growing at the same time, both in Release and Debug builds of the Linux ports:

<p style="text-align: center;"><img src="/images/2026/11/passing-tests-2026.png" alt="Line chart of passing tests over time for the GTK and WPE bots, growing steadily from around 77,000-79,000 in October 2025 to 86,000-89,000 in October 2026" width="1753" height="1048" /></p>

On top of that, **API test results are now uploaded to [results.webkit.org](https://results.webkit.org)** (with the right version and architecture fields), we **improved the CI infrastructure** (hybrid cloud and bare metal, centralized monitoring, 3 new ARM64 WPE testers, and the [WPE performance dashboard](https://wpe-perf-dashboard.igalia.com)), and we **improved the management of stable branches**, with a better backporting workflow, EWS testing and ARM64 post-commit bots.

#### Next steps

Besides keeping the bots green, we plan to detect flaky tests in EWS in a smarter way (using the history from results.webkit.org), to add Safer C++ post-commit bots and a WebDriver EWS for the Linux ports, and to set up PGO-enabled performance bots.

On top of that, we'll work on adapting the bots to the changes coming in 2.56, and add **hardware-accelerated** post-commit bots to test GPU-dependent code paths.

### Security {#security}

* We continued with the **same release cadence**: feature releases every 6 months in March and September, and minor and development releases when needed (e.g. security fixes).
* We published **9 WebKit Security Advisories** (WSA) covering **99 CVEs**, mostly on the same day as the release or the next one. You can find them at [webkitgtk.org/security.html](https://webkitgtk.org/security.html) and [wpewebkit.org/security](https://wpewebkit.org/security/).
* **~66% fewer `WTF_ALLOW_UNSAFE_BUFFER_USAGE`** in port-specific code, more smart pointers and safer string types, and `-Wthread-safety` enabled.

#### Next steps

We want to make the WebProcess sandboxing stricter by moving more parts of the graphics and multimedia pipelines to the GPUProcess, and to replace libgcrypt with OpenSSL ([bug 216201](https://bugs.webkit.org/show_bug.cgi?id=216201)). And, of course, we'll keep doing all of the above: sticking to the release cadence, publishing timely advisories, reducing unsafe buffer usage...

### Development tools {#development-tools}

Besides development itself, we also paid special attention to the developer experience, with improvements in several areas:

* **Sysprof**: new `webkit-sysprof` tool to analyze traces in an automated way, and correct durations for overlapping and recursive marks.
* **[WebKit Container SDK](https://github.com/Igalia/webkit-container-sdk)**: ephemeral containers for the host-side wrappers and the CI, and regular rebases (e.g. Ubuntu 26.04, GStreamer 1.28, the Swift-enabled toolchain).
* **WebDriver** (classic and BiDi): stability work in the driver, the browser and the test bots (fewer crashes, hangs and failures), plus other improvements such as pointer-action attributes and closed shadow roots.
* **Build system**: fewer stale-cache problems, GCC build fixes, and a new `BUILD_WEBKIT_PRE_SCRIPT` hook (e.g. to set up a remote `ccache`).

## Final thoughts

Once again, this turned out to be a long post, which I guess is a good sign: in summary, this has been quite a busy year for WebKit here at Igalia, with some long-running efforts reaching important milestones (e.g. Skia-only rendering, the new compositor, a stable WPEPlatform API, green bots...), and quite a lot of exciting work ahead. But if you prefer a more concise version, you can always check [the slides of the presentation](https://speakerdeck.com/mariospr/igalia-and-webkit-status-update-and-plans-2026).

Before finishing, though, I'd like to acknowledge once again that none of this would be possible without the work of the many Igalians involved across different teams, nor without the support of our customers who fund this work. And of course special thanks to the rest of the WebKit community, who also collaborated and made this possible through reviews, feedback, discussions and fixes across ports.

Thank you, everyone!
