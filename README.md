# panem-website

Marketing site for [Panem](https://panemapp.com) — an iOS app that helps you track food, reduce waste, and save money.

Built with [Hugo](https://gohugo.io) + [Congo theme](https://jpanther.github.io/congo/), deployed via Netlify, served at panemapp.com.

## Stack

| Layer | Tool |
|---|---|
| Static site generator | Hugo v0.164.0 |
| Theme | Congo (main branch, git submodule) |
| Hosting | Netlify (free tier) |
| CI/CD | Netlify ← GitHub (auto-deploy on push to `main`) |
| Domain | panemapp.com (GoDaddy DNS → Netlify) |
| SSL | Netlify (auto-provisioned via Let's Encrypt) |

## Local development

**Prerequisites:** Hugo v0.164.0+ installed ([download](https://github.com/gohugoio/hugo/releases))

```bash
git clone --recurse-submodules https://github.com/codabuilt/panem-website.git
cd panem-website
hugo server --buildDrafts
```

Site runs at http://localhost:1313. Live-reloads on save.

> If you cloned without `--recurse-submodules`, run `git submodule update --init` to pull the Congo theme.

## Deploying

Push to `main` — Netlify picks it up automatically and rebuilds. No manual steps needed.

Build config is in `netlify.toml`. Hugo version is pinned there to match local.

## Content

All content lives in `content/`:

| File | Page |
|---|---|
| `content/_index.md` | Homepage (panemapp.com) |
| `content/contact.md` | Contact page (/contact) |

Pages use standard Hugo front matter. To add a new page, create a new `.md` file in `content/`.

**Pending:** Replace `#` placeholder links in `_index.md` and `contact.md` with the real App Store URL once the app is live.

## Config

Site config lives in `config/_default/`:

| File | Purpose |
|---|---|
| `hugo.toml` | Base URL, theme, privacy settings |
| `params.toml` | Color scheme, layout options, feature flags |
| `languages.en.toml` | Site title, description, author |
| `menus.en.toml` | Nav items (Home, Contact) |
