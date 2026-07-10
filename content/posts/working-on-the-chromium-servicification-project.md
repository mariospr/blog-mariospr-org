---
title: Working on the Chromium Servicification Project
date: '2019-01-29T18:35:44+00:00'
slug: working-on-the-chromium-servicification-project
categories:
- Fosdem
- Planet GNOME
- Planet GPUL
- Planet Igalia
- Planeta GNOME Hispano
- Chromium
- Servicification
wp_id: 2660
---

<p><a href="https://www.igalia.com/browsers-webkit-chromium"><img class="alignright wp-image-2687" src="/wp-content/uploads/2019/01/igalia-chromium-logos-vertical-147x300.png" alt="Igalia &amp; Chromium" width="108" height="220" /></a>It's been a few months already since I (re)joined <a href="https://www.igalia.com/">Igalia</a> as part of its <a href="https://www.igalia.com/browsers-webkit-chromium/">Chromium team</a> and I couldn't be happier about it: right since the very first day, I felt perfectly integrated as part of the team that I'd be part of and quickly started making my way through the -fully upstream- project that would keep me busy during the following months: the <strong><a href="https://www.chromium.org/servicification">Chromium Servicification Project</a></strong>.</p>



<p>But what is this "<a href="https://www.chromium.org/servicification">Chromium servicification project</a>"? Well, according to the <a href="https://en.wiktionary.org/wiki/servicification">Wiktionary</a> the word <em>"servicification"</em> means, applied to computing, <em>"the migration from monolithic legacy applications to service-based components and solutions"</em>, which is exactly what this project is about: as described in the <a href="https://www.chromium.org/servicification">Chromium servicification project's website</a>, the whole purpose behind this idea is <em>"to migrate the code base to a more modular, service-oriented architecture"</em>, in order to <em>"produce reusable and decoupled components while also reducing duplication"</em>.</p>



<p>Doing so would not only make Chromium a more manageable project from a source code-related point of view and create better and more stable interfaces to embed chromium from different projects, but should also enable teams to experiment with new features by combining these services in different ways, as well as to ship different products based in Chromium without having to bundle the whole world just to provide a particular set of features. </p>



<p>For instance, as <a href="https://www.linkedin.com/in/camille-lamy-2506a459">Camille Lamy</a> put it in the <a href="https://www.youtube.com/watch?v=AHlZ_T74nOo">talk delivered</a> (<a href="https://webengineshackfest.org/2018/slides/servicification-modularizing-chromium-by-camille-lamy-colin-blundell-and-robert-kroeger.pdf">slides here</a>) during the <a href="https://webengineshackfest.org/2018/">latest Web Engines Hackfest</a>,  <em>"it might be interesting long term that the user only downloads the bits of the app they need so, for instance, if you have a very low-end phone, support for VR is probably not very useful for you"</em>. This is of course not the current status of things yet (right now everything is bundled into a big executable), but it's still a good way to visualise where this idea of moving to a services-oriented architecture should take us in the long run.</p>
<p><a href="/wp-content/uploads/2019/01/chromium-s13n-layers-1.png"><img class="size-medium wp-image-2711 alignright" src="/wp-content/uploads/2019/01/chromium-s13n-layers-1-269x300.png" alt="Chromium Servicification Layers" width="269" height="300" /></a></p>



<p>With this in mind, the idea behind this project would be to work on the migration of the different parts of Chromium depending on those components that are being converted into services, which would be part of a "foundation" base layer providing the core services that any application, framework or runtime build on top of chromium would need.</p>



<p>As you can imagine, the whole idea of refactoring such an enormous code base like Chromium's is daunting and a lot of work, especially considering that currently ongoing efforts can't simply be stopped just to perform this migration, and that is where our focus is currently aimed at: we integrate with different teams from the Chromium project working on the migration of those components into services, and we make sure that the clients of their old APIs move away from them and use the new services' APIs instead, while keeping everything running normally in the meantime.</p>



<p>At the beginning, we started working on the migration to the <a href="https://chromium.googlesource.com/chromium/src/+/master/services/network">Network Service</a> (which allows to run Chromium's network stack even without a browser) and managed to get it shipped in Chromium Beta by early October already, which was a pretty big deal as far as I understand. In my particular case, that stage was a very short ride since such migration was nearly done by the time I joined Igalia, but still something worth mentioning due to the impact it had in the project, for extra context.</p>



<p>After that, our team started working on the migration of the <a href="https://chromium.googlesource.com/chromium/src/+/master/services/identity">Identity service,</a> where the main idea is to encapsulate the functionality of accessing the user's identities right through this service, so that one day this logic can be run outside of the browser process. One interesting bit about this migration is that this particular functionality (largely implemented inside the <a href="https://chromium.googlesource.com/chromium/src/+/master/components/signin">sign-in component</a>) has historically been located quite high up in the stack, and yet it's now being pushed all the way down into that "foundation" base layer, as a core service. That's probably one of the factors contributing to making this migration quite complicated, but everyone involved is being very dedicated and has been very helpful so far, so I'm confident we'll get there in a reasonable time frame.</p>



<p>If you're curious enough, though, you can check this <a href="https://groups.google.com/a/chromium.org/forum/#!topic/identity-service-dev/c18zBMpaj-8">status report for the Identity service</a>, where you can see the evolution of this particular migration, along with the impact our team had since we started working on this part, back on early October. There are more reports and more information in the <a href="https://groups.google.com/a/chromium.org/forum/#!forum/identity-service-dev">mailing list for the Identity service</a>, so feel free to check it out and/or subscribe there if you like.</p>



<p>One clarification is needed, tough: for now, the scope of this migrations is focused on using the public C++ APIs that such services expose (see <code>//services/&lt;service_name&gt;/public/cpp</code>), but in the long run the idea is that those services will also provide <a href="https://chromium.googlesource.com/chromium/src/+/master/mojo/README.md">Mojo interfaces</a>. That will enable using their functionality regardless of whether you're running those services as part of the browser's process, or inside their own &amp; separate processes, which will then allow the flexibility that chromium will need to run smoothly and safely in different kind of environments, from the least constrained ones to others with a less favourable set of resources at their disposal.</p>



<p>And this is it for now, I think. I was really looking forward to writing a status update about what I've been up to in the past months and here it is, even though it's not the shortest of all reports.</p>



<div class="wp-block-image">
<figure class="alignright"><a href="https://fosdem.org"><img class="wp-image-2679" src="/wp-content/uploads/2019/01/fosdem-2019.png" alt="FOSDEM 2019" /></a></figure>
</div>



<p>One last thing, though: as usual, I'm <strong>going to <a href="https://fosdem.org/">FOSDEM</a></strong> this year as well, along with a bunch of colleagues &amp; friends from <a href="https://www.igalia.com/">Igalia</a>, so please feel free to drop me/us a line if you want to chat and/or hangout, either to talk about work-related matters or anything else really.</p>



<p>And, of course, I'd be also more than happy to talk about any of the <strong><a href="https://www.igalia.com/nc/about-us">open job positions at Igalia</a></strong>, should you consider applying. There are quite a few of them available at the moment for all kind of things (most of them available for remote work): from more technical roles such as <a href="https://www.igalia.com/nc/about-us/form/webkit-graphics-developer">graphics</a>, <a href="https://www.igalia.com/nc/about-us/form/compilers-developer">compilers</a>, <a href="https://www.igalia.com/nc/about-us/form/multimedia-developer">multimedia</a>, <a href="https://www.igalia.com/nc/about-us/form/javascript-engine-developer">JavaScript engines</a>, browsers (<a href="https://www.igalia.com/nc/about-us/form/webkit-developer">WebKit</a>, <a href="https://www.igalia.com/nc/about-us/form/chromium-developer">Chromium</a>, <a href="https://www.igalia.com/nc/about-us/form/web-platform-engineer">Web Platform</a>) or <a href="https://www.igalia.com/nc/about-us/form/senior-systems-administrator-galicia-spain">systems administration</a> (this one not available for remotes, though), to other less "hands-on" types of roles like <a href="https://www.igalia.com/nc/about-us/form/developer-advocate">developer advocate</a>, <a href="https://www.igalia.com/nc/about-us/form/sales-engineer">sales engineer</a> or <a href="https://www.igalia.com/nc/about-us/form/project-manager">project manager</a>, so it's possible there's something interesting for you if you're considering to join such an special company like this one.</p>
<p>See you in <strong><a href="https://fosdem.org/">FOSDEM</a></strong>!</p>
