# Tasks.AI — pre-launch landing page

The one-page pre-launch site for **Tasks.AI**. *Teach once. Automate forever.*

Teach a digital coworker to do your browser work by showing it once — then it
runs forever, locally, with your data and know-how staying yours.

## Stack
Static site built with **Claude Design** (Design Components runtime). The page
ships as `index.html` + `support.js` (the runtime — don't hand-edit) and renders
its `<x-dc>` template client-side. Hosted on **GitHub Pages**.

## Structure
```
index.html        the landing page (Claude Design export + injected SEO head)
support.js         Design Components runtime (generated; do not edit)
assets/
  logo_mark_transparent.png   brand mark (∞ + checkmark)
  og-cover.png                1200×630 social share card
robots.txt  sitemap.xml  404.html  .nojekyll   GitHub Pages essentials
```

## Hosting
- **Phase 1 (now):** GitHub Pages (org-root site) at
  `https://tasks-ai-inc.github.io/` — no custom DNS yet.
- **Phase 2 (later):** point `tasks.ai` at it (add a `CNAME`, update `SITE` in the
  sync tooling, re-run, set the Pages custom domain).

## Updating the content
The source of truth is the **Claude Design** project *"Tasks.AI - Website"*. Edit
there, re-export the page to `index.html`, then re-apply the deploy-only fixes
(static SEO head, early-access form wiring) the design tool can't do. That
pipeline lives in the local `sync-tasksai` Claude Code skill (not published).

## Early-access form
Collects Company · Name · Work email · *"What would you teach it first?"* and
posts to a Google Apps Script Web App (a Google Sheet backend). Until that's
wired it captures leads in `localStorage` as a fallback.

---
© 2026 Tasks.AI — All rights reserved.
