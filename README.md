# Tasks.AI — pre-launch site

The pre-launch site for **Tasks.AI**. *Teach once. Automate forever.*

Teach a digital coworker to do your browser work by showing it once — then it
runs forever, locally, with your data and know-how staying yours.

## Stack
Static site built with **Claude Design** (Design Components runtime). Each page
ships as an HTML file + the shared `support.js` runtime (generated — don't
hand-edit) and renders its `<x-dc>` template client-side. Hosted on **GitHub
Pages** at the custom domain `tasks.ai`.

## Structure
```
index.html         the landing page      (Claude Design export + injected SEO head)
privacy.html       the privacy policy    (Claude Design export + injected SEO head)
support.js         Design Components runtime (generated; do not edit)
assets/
  favicon.png                 site icon / apple-touch-icon
  logo_full.png               full lockup, used in the nav
  logo_mark.png               brand mark (∞ + checkmark)
  og-cover.png                1200×630 social share card
robots.txt  sitemap.xml  llms.txt  404.html  CNAME  .nojekyll   Pages + crawler essentials
```

## Hosting
Served by GitHub Pages from this org-root repo, on the custom domain
**https://tasks.ai** (`CNAME`). The host is declared once, in the sync tooling —
changing it there rewrites the canonical/OG URLs, `robots.txt`, `sitemap.xml` and
the 404 home link together.

## Updating the content
The source of truth is the **Claude Design** project *"Tasks.AI - Website"* —
`TasksAI Landing.dc.html` maps to `index.html`, `Privacy.dc.html` to
`privacy.html`. Edit there, re-export, then re-apply the deploy-only fixes the
design tool cannot do: the static SEO head (its `<helmet>` sits inside `<body>`,
so crawlers see nothing), the cross-page links (`*.dc.html` filenames only resolve
inside the editor), the policy's Last-updated date, and the early-access form
wiring. That pipeline lives in the local `sync-tasksai` Claude Code skill (not
published).

## Early-access form
Collects Company · Name · Work email · *"What would you teach it first?"* and
posts to the Google Apps Script Web App behind the shared Google Sheet, tagged
`source: prelaunch-landing`. Leads are mirrored to `localStorage` as a safety net.

---
© 2026 Tasks.AI — All rights reserved.
