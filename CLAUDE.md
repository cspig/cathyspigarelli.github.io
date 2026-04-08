# cathyspigarelli.github.io

Cathy Spigarelli's personal blog. EHS professional, writer, mom.

**Live site:** https://cathyspigarelli.com  
**CMS:** https://cathyspigarelli.com/admin/  
**Repo:** https://github.com/cspig/cathyspigarelli.github.io

---

## Stack

- **Hugo** (v0.160.1+, extended) — static site generator
- **Theme:** [hugo-theme-cleanwhite](https://github.com/zhaohuabing/hugo-theme-cleanwhite) — added as a git submodule at `themes/hugo-theme-cleanwhite`
- **CMS:** [Decap CMS](https://decapcms.org) v3 — served at `/admin/`, config at `static/admin/config.yml`
- **Hosting:** GitHub Pages (public repo, free tier) — deploys via GitHub Actions on push to `master`
- **Custom domain:** `cathyspigarelli.com` — CNAME file at root, A records already set in Google Domains (now managed via Squarespace)

---

## How deploys work

Push to `master` → GitHub Actions (`.github/workflows/hugo.yml`) builds with Hugo and deploys to GitHub Pages. The CMS commits directly to `master`, so publishing a post triggers a deploy automatically.

---

## CMS authentication

Decap CMS uses the **GitHub backend** with **Netlify as a free OAuth proxy** — no Netlify hosting required.

- `base_url: https://api.netlify.com`
- `site_domain: merry-sopapillas-0af08a.netlify.app` (blank placeholder Netlify site used solely as OAuth proxy)

**GitHub OAuth App** is registered under Cathy's GitHub account with:
- Callback URL: `https://api.netlify.com/auth/done`

**Netlify site** (`merry-sopapillas-0af08a.netlify.app`) has the GitHub OAuth provider configured with the Client ID + Secret from the OAuth App above.

Cathy logs into the CMS with her GitHub account.

---

## Content structure

```
content/
  post/           ← blog posts (markdown, YYYY-MM-DD-slug.md)
  about/
    index.md      ← about page
  archive/
    _index.md     ← archive page (auto-generated list)
static/
  img/            ← all images (referenced as /img/filename in front matter)
  admin/
    index.html    ← Decap CMS entry point
    config.yml    ← CMS configuration
```

### Post front matter

```yaml
---
layout: post
title: "Post Title"
subtitle: "Optional subtitle"
date: 2024-01-01
author: "Cathy Spigarelli"
image: "img/some-image.jpg"   # header background image
tags: ["EHS", "Writing"]
description: "Short description for SEO/previews"
---
```

---

## DNS

Apex domain A records (already set, do not change):
```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

`www` subdomain is intentionally not configured — site is apex-only.

---

## History

Migrated from Jekyll (simple theme, two posts) to Hugo + Decap CMS in April 2026. All original content and images were preserved.
