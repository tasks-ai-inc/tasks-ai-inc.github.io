# Tasks.AI — pre-launch site

The pre-launch site for **Tasks.AI**. *Teach once. Automate forever.*

## Stack

Static site built with **Claude Design** (Design Components runtime). Each page ships as an HTML file plus the shared `support.js` runtime (generated, don't hand-edit) and renders its `<x-dc>` template client-side. Hosted on **GitHub Pages** at the custom domain `tasks.ai`.

## Structure

```
index.html       the entry point "/": picks one of the three landing versions and shows it in place
builder.html     landing v5, for a builder        (Claude Design: "Landing v5 Builder")
team-lead.html   landing v5, for a team lead      (Claude Design: "Landing v5 Team Lead")
executive.html   landing v5, for an executive     (Claude Design: "Landing v5 Executive")
privacy.html     the privacy policy               (Claude Design export + injected SEO head)
404.html         unknown address: noindex, sent to "/"
support.js       Design Components runtime (generated; do not edit)
assets/          favicon.png, logo_full.png, logo_mark.png, og-cover.png
robots.txt  sitemap.xml  llms.txt  CNAME  .nojekyll   Pages + crawler essentials
```

## How "/" works

`index.html` carries the static SEO head (title, description, canonical, Open Graph, JSON-LD) and a short script. The script picks a version that is not the one shown on the previous visit in this browser (kept in `localStorage`, key `tasksai-landing`), fetches that page and writes it in place, so the address stays `/` and each refresh shows a different version. Without JavaScript, a `<noscript>` block gives the text and links to the three versions. If the fetch fails, the script falls back to `builder.html`.

The `I'm: a builder / a team lead / an executive` selector on each page links to a fixed version, so a reader who picks one keeps it on refresh. The three version pages have `canonical` set to `https://tasks.ai/`, and only `/` and `/privacy.html` are in `sitemap.xml`.

## Unknown addresses

GitHub Pages cannot send a 301. An address that does not exist is answered by `404.html` (status 404, `noindex`), which redirects to `/` at once, with a meta refresh as a fallback. Search engines therefore drop those addresses instead of treating them as moved.

## Hosting

Served by GitHub Pages from this org-root repo, on the custom domain **https://tasks.ai** (`CNAME`). The host appears in the canonical and Open Graph URLs of `index.html` and the three version pages, in `robots.txt`, `sitemap.xml`, `llms.txt` and the 404 page.

## Updating the content

The source of truth is the **Claude Design** project *"Tasks.AI - Website"*. Each `Landing v5 *.dc.html` page there is deployed as the matching `*.html` here. `*.dc.html` files are git-ignored: they are the sync source, not deployed. After re-exporting a page, re-apply what the design tool cannot do:

- the static `<head>` block (title, description, canonical, Open Graph, Twitter);
- the selector and footer links, which use `*.dc.html` names inside the editor and must point at `builder.html`, `team-lead.html`, `executive.html` and `privacy.html`.

## Early access

Every "Get Early Access" button links to `https://dev.app.tasks.ai/`. The earlier on-page form (Company, Name, Work email) and its Google Apps Script backend were removed with the v5 landing; `google-apps-script.gs` stays local and unpublished.

---
© 2026 Tasks.AI — All rights reserved.
