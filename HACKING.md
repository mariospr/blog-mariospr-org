# Working on the blog

Quick guide for day-to-day tasks. The blog is a **Hugo** site; everything lives in this repository.

---

## Preview locally

Start the live server (auto-reloads as you edit — just refresh the browser):

```
hugo server --baseURL "http://localhost:1313/" --appendPort=false
```

Then open **http://localhost:1313/**.

- To also preview **draft** posts, add `-D`.
- **Stop it:** press **Ctrl+C** in that terminal.
  (If it's running in the background and you lost the terminal: `pkill -f "hugo serv"`.)

---

## Write a new post

```
hugo new posts/my-post-title.md
```

That creates `content/posts/my-post-title.md` with this top block (the "front matter"):

```yaml
---
title: "My Post Title"
date: 2026-07-10T10:00:00+00:00
draft: true              # change to false (or delete the line) to publish
categories:
  - Planet GNOME         # add/remove as needed
# slug: custom-url-part  # optional — by default the URL uses the title
---

Write your post here (Markdown or HTML both work).
```

- The post's address becomes **`/YYYY/MM/DD/slug/`**, taken from the `date` and the slug/title.
- While `draft: true`, it shows only with `hugo server -D` and is left out of the built site.
- Set **`draft: false`** (or remove the line) when it's ready.

**Categories:** use the *exact* name of an existing category (a misspelled or new name silently
creates a brand-new category). To list the available names:

```
sed -n 's/^title: //p' content/categories/*/_index.md | sort
```

(or just browse http://localhost:1313/categories/). Add **more than one** by listing each on its
own line:

```yaml
categories:
  - Planet GNOME
  - WebKit
  - Igalia
```

An inline comma form also works: `categories: ["Planet GNOME", "WebKit"]`.

## Update a page or an existing post

Just edit the file and save (the preview refreshes automatically):

| What | File |
|---|---|
| Work / Talks / About pages | `content/work.md`, `content/talks.md`, `content/about.md` |
| Intro text at the top of /blog/ | `content/posts/_index.md` |
| An existing post | `content/posts/<name>.md` |
| Colors / styling | `assets/css/extended/custom.css` |

## Add an image

Put the file under `static/` (e.g. `static/images/photo.jpg`) and link it in the post with a
path that starts with `/`:

```
![description](/images/photo.jpg)
```

---

## Build the files to upload

The preview server rebuilds automatically, but to produce the final files for the web server,
always do a **clean rebuild** — wiping `public/` first so files you've deleted from the source
don't linger in the output:

```
rm -rf public resources && hugo --gc --minify
```

This regenerates the **`public/`** directory from scratch — upload the **contents of `public/`**
to your web server's document root.

(For a quick local check you can run plain `hugo --gc --minify` without wiping, but don't deploy
that output — it can still contain stale copies of files you've since removed.)

---

## Cheat sheet

| Task | Command |
|---|---|
| Preview | `hugo server --baseURL "http://localhost:1313/" --appendPort=false` |
| Preview incl. drafts | add `-D` |
| Stop preview | `Ctrl+C` |
| New post | `hugo new posts/name.md` |
| Build `public/` to deploy (clean) | `rm -rf public resources && hugo --gc --minify` |
| Quick local build (not for deploy) | `hugo --gc --minify` |
