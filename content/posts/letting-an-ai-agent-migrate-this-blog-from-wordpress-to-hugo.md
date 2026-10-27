---
title: "Letting an AI agent migrate this blog from WordPress to Hugo"
date: 2026-11-04T10:00:00+00:00
draft: true
slug: letting-an-ai-agent-migrate-this-blog-from-wordpress-to-hugo
categories:
  - General
  - Tools
---

If you are reading this through an RSS reader, chances are you didn't notice anything different, which is exactly the point. But behind the scenes, this blog is **no longer running on WordPress**: as of July, this is a **static site generated with [Hugo](https://gohugo.io)**, and the way I got there is probably worth a few paragraphs, since **most of the actual work was done by an AI coding agent**, with me mostly answering questions, making a few decisions and reviewing the results.

<p style="text-align: center;"><a href="https://wordpress.org"><img src="/images/2026/10/wordpress-logo.svg" alt="WordPress logo" width="100" height="100" style="display: inline-block; vertical-align: middle; width: 20%; max-width: 100px; height: auto; margin: 0 3%;" /></a><span style="font-size: 2rem; vertical-align: middle;">&rarr;</span><a href="https://gohugo.io"><img src="/images/2026/10/hugo-logo.svg" alt="Hugo logo" width="300" height="82" style="display: inline-block; vertical-align: middle; width: 55%; max-width: 300px; height: auto; margin: 0 3%;" /></a><br /><small><em>WordPress logo (GPLv2+) by the WordPress project; Hugo logo &copy; 2014 Steve Francia (Apache 2.0)</em></small></p>

I know that AI is a topic that tends to bring strong opinions in both directions, so I'll try to stick to the facts and let you draw your own conclusions...

## Why move away from WordPress at all?

This blog has been around for quite some time now: the [first post](/2006/06/25/starting-to-blog/) dates back to June 2006, so that's almost 20 years of mostly technical ramblings about GNOME, WebKit, Chromium and other things I was working on at the time, plus some personal posts here and there.

All that time it had been running on **WordPress** on shared hosting, which means a MySQL database, PHP, a customized WordPress theme that I wrote many years ago, and a handful of plugins. And of course, the never-ending stream of updates too, as well as the occasional hardening. None of that is a big deal on its own, but for a blog that gets a new post every now and then (and sometimes not even that, as the two-year gap before [my last post](/2024/11/03/igalia-and-webkit-status-update-and-plans-2024/) proves), it felt like way too many moving pieces to maintain.

So I had wanted to move to something static for years, but I never found the time to sit down and do it properly, mainly because "properly" here means **not breaking anything**: there are many links out there pointing to posts in this blog, and several *planets* (e.g. [Planet GNOME](https://planet.gnome.org), [Planet Igalia](https://planet.igalia.com)) that poll per-category feeds, and those can break silently if you are not careful.

## Letting an AI agent drive

This summer I decided to give it a go using an AI coding agent, and to see how far I could get by letting it drive the whole process instead of using it as a glorified autocomplete. In a nutshell, what I provided it with was:

* A full copy of the files from the FTP server (WordPress core, themes, plugins and the `wp-content/uploads/` directory, plus some static directories with slides, videos and other files I had been linking to over the years).
* A MySQL dump of the database.
* A short list of requirements: **preserve all the content**, **keep all existing URLs working** (especially the feeds), keep the title and the tagline, and make it look nice and simple, without needing to be a 1:1 copy of the old theme.

From there, the agent explored the dump and the files, and came back with a plan. That included **suggesting Hugo** as the static site generator, as well as [PaperMod](https://github.com/adityatelange/hugo-PaperMod) as the theme, mainly because Hugo can reproduce WordPress' `/YYYY/MM/DD/slug/` permalinks and `/category/<slug>/` archives natively, and because it's a single binary with no runtime dependencies, which matched what I was looking for. I didn't have a strong preference for any static site generator, so I went with its recommendation.

The decisions that were actually mine were few, and mostly about scope:

* **Comments**: keep the 252 comments from readers as **read-only static HTML** (threaded, as they were), and drop the 61 pingbacks.
* **No analytics** (the old Google Analytics was the *Universal Analytics* kind anyway, which is long dead), so the Cookie Policy page could go away too.
* **Drop a few private posts** that were never meant to be published.
* **Hosting**: stay with the same hosting provider for now, simply serving static files.

## How the migration went

Rather than trying to parse a 20 MB SQL file as text, the agent spun up a **throwaway MariaDB container** with podman, imported the dump, queried it from a 260-line Python script and generated the Hugo content from there: one Markdown file per post, YAML files with the comments of each post, and an index file for each category, so that their slugs (and therefore their feed URLs) would match the old ones. Once done, the container was removed.

<p style="text-align: center;"><a href="/images/2026/10/wordpress-to-hugo-pipeline.svg"><img src="/images/2026/10/wordpress-to-hugo-pipeline.svg" alt="Diagram of the migration: WordPress backup, throwaway MariaDB container, extract.py, Hugo sources, and then a GitHub Actions workflow building the site and uploading it via SFTP to the same host as before" /></a></p>

Interestingly, the transformations of the actual content were kept to a minimum: the posts were written with WordPress' *classic editor*, so the bodies are mostly raw HTML already, and Hugo can render that as it is. The script converted the `[caption]` shortcodes into `<figure>` elements, made all the internal links relative, stripped a few leftover bits of Gutenberg and Jetpack markup and... that's pretty much it. Embedded videos and slides from YouTube, Vimeo, SpeakerDeck and SlideShare are still the original `<iframe>` elements, with a bit of CSS to make them responsive.

The trickiest part was, as expected, **the feeds**. On one hand, WordPress serves them at `/feed/` and `/category/<slug>/feed/`, while Hugo generates `index.xml` files instead, and there is no clean way to make Hugo produce 50+ feeds at those exact paths. The solution was a **single server-side rewrite rule** that serves `index.xml` whenever `.../feed/` is requested, which is invisible to the planets.

On the other hand, there's a detail I'm pretty sure I would not have thought about before it was too late: RSS readers and aggregators use the `<guid>` element to tell whether an item is new, and WordPress uses URLs like `https://mariospr.org/?p=1234` for that. Had the new feeds used different GUIDs, every planet aggregating this blog could have treated the last 10 posts as brand new ones and re-published them. So the RSS template was overridden to **keep the same GUIDs WordPress was generating**, which is why you (hopefully) didn't see a burst of old posts from me back in July :-)

Other than that, there were a few rough edges along the way that needed some extra work:

* The latest PaperMod release at the time (v8.0) didn't build with the latest Hugo, so the agent pinned the theme to a specific (newer) commit of the main branch instead.
* WordPress automatically turns line breaks into `<br>` and `<p>` tags when rendering a post (the so-called *wpautop*), which Hugo obviously doesn't, so some content needed some tweaks to look right again (e.g. the [Talks](/talks/) page, which got a few CSS rules ported from my old theme).
* The rest was mostly small cosmetic changes, such as removing some items from the navigation bar, or changing the date format to the one I was using before.

As for the verification, the generated site was checked against a list of the URLs extracted from the database: **all 101 posts are served at byte-identical URLs**, the few old URLs that posts had before being renamed (plus `/other-stuff/`, the old address of the [Work](/work/) page) redirect to their current locations, and the author archives still redirect to the front page.

And as a result of all this I finally have what I'd wanted for years but never found the time to do: everything lives in a [git repository](https://github.com/mariospr/blog-mariospr-org), and writing a new post is just a matter of creating a Markdown file and pushing it to the main branch. That triggers a GitHub Actions workflow that builds the site and uploads it via SFTP to the same host as before, only now without the database, PHP or plugins.

## So, how much did I actually do?

Not much, if I'm completely honest. Leaving aside the time it took me to prepare the backup, most of my involvement was answering a few questions about scope, previewing the site locally a couple of times, asking for some cosmetic changes and reviewing the important bits (e.g. the redirects and the feeds). The whole thing happened over a couple of days, and only a small fraction of that time was actual work from my side.

That said, I think a few things are worth pointing out too:

* I knew what I wanted to preserve and what could break (e.g. the planet feeds), so I could ask for the right things and check the parts that mattered. I'm not sure the result would have been the same with vaguer instructions.
* The agent did a pretty thorough job verifying its own work (e.g. comparing all the URLs), but I still reviewed it, and I'd still recommend doing that: it's my blog after all, and I'm the one who will have to maintain it from now on.
* There's still some work left that I decided not to do for now, such as downloading the few Flickr images that some old posts embed from external URLs, so they don't eventually disappear. I don't think that's a big deal, though.

In any case, I'm happy with the result. The blog is now simpler, faster and cheaper to maintain, and it feels like a weight off my shoulders not having to think about WordPress updates anymore. Whether that also means I'll be writing more often from now on... well, that's a different story ;-)
