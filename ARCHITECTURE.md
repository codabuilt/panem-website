# Architecture

## Overview

panem-website is a static site — no server, no database, no runtime. Hugo compiles Markdown content and config files into plain HTML/CSS/JS at build time. Netlify serves the output and handles SSL and CDN distribution.

```
                        push to main
  Local dev  ──────────────────────────▶  GitHub (codabuilt/panem-website)
  hugo server                                        │
  localhost:1313                                     │ webhook
                                                     ▼
                                             Netlify build
                                          (hugo --minify)
                                                     │
                                                     ▼
                                          Netlify CDN / Edge
                                                     │
                                         ┌───────────┴───────────┐
                                         ▼                       ▼
                                    panemapp.com           www.panemapp.com
                                  (A record → Netlify)   (CNAME → Netlify)
```

## Build pipeline

1. Developer pushes to `main` on GitHub
2. GitHub notifies Netlify via webhook
3. Netlify clones the repo (including the Congo submodule) and runs `hugo --minify`
4. Hugo reads `config/_default/`, processes `content/`, applies the Congo theme from `themes/congo/`
5. Output lands in `public/` — Netlify deploys that directory to its CDN

Hugo version is pinned in `netlify.toml` (`HUGO_VERSION = "0.164.0"`) so local and CI builds are identical.

## Repository layout

```
panem-website/
├── config/_default/        # All site config (split across 4 files)
│   ├── hugo.toml           # Base URL, theme, privacy
│   ├── params.toml         # Layout, color scheme, feature flags
│   ├── languages.en.toml   # Locale, title, description
│   └── menus.en.toml       # Nav items
├── content/                # Markdown pages
│   ├── _index.md           # Homepage
│   └── contact.md          # Contact page
├── themes/congo/           # Congo theme (git submodule, main branch)
├── archetypes/             # Hugo content templates
├── hugo.toml               # (root-level, minimal — config lives in config/_default/)
├── netlify.toml            # Netlify build config + Hugo version pin
└── .gitignore              # Excludes public/, resources/, .hugo_build.lock
```

## DNS

Managed at GoDaddy. Two records point panemapp.com to Netlify:

| Type | Name | Value |
|---|---|---|
| A | `@` (apex) | `75.2.60.5` (Netlify load balancer) |
| CNAME | `www` | Netlify-assigned subdomain |

GoDaddy doesn't support ALIAS/ANAME records, so the apex domain uses Netlify's stable A record IP. Netlify auto-provisions SSL via Let's Encrypt once DNS propagates.

## Theme

Congo is installed as a git submodule at `themes/congo` tracking the `main` branch. The `stable` branch was incompatible with Hugo v0.164.0 at time of setup.

To update the theme:
```bash
git submodule update --remote themes/congo
git commit -am "Update Congo theme"
```

## No-cost design

Every layer is free tier:
- **GitHub**: free public repo
- **Netlify**: free tier (100GB bandwidth/month, 300 build minutes/month)
- **SSL**: free via Let's Encrypt (Netlify-managed)
- **Hugo**: open source

The only recurring cost is the panemapp.com domain registration at GoDaddy.
