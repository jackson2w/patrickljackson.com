# Patrick Ian Jackson — Website

The homepage for Rev. Patrick Ian Jackson (pastor, author, speaker). Single-page static
site, no build step. Warm & personal design — Newsreader/Public Sans, terracotta palette.

## Structure

| Path | Purpose |
|------|---------|
| `index.html` | The single-page site (hero, mission, work, writing, sermons, about, contact) |
| `assets/` | Portrait (`.webp`), social share image (`og.webp`), source JPGs |
| `_headers` | Cloudflare Pages edge caching + security headers |

## Optimizations applied

- **Golden Ratio Typography** — body line-height derived from the GRT calculator
  (size × measure), not hand-picked.
- **Images** — hero cropped to a head-and-shoulders portrait and served as WebP
  (700×814, q80, ~86 KB); explicit `width`/`height` to prevent layout shift;
  `fetchpriority="high"` on the LCP hero; baseline `img { height: auto; }`.
- **SEO / social** — `description`, `canonical`, and Open Graph tags with a
  1200×630 `og.webp` share image.
- **Semantic HTML** — `<main>` landmark, single `<h1>`, descriptive `alt` text.
- **Edge headers** — immutable caching on `/assets/*`, security headers on HTML.

## Local preview

```bash
python3 -m http.server 8000   # then open http://localhost:8000
```

## Deploy

Static site, deploy directory is the repo root (no build command). Auto-deploys on push
to `main` via GitHub Actions (`.github/workflows/deploy.yml`). Manual deploy:

```bash
npx wrangler pages deploy . --project-name patrickljackson-mockups
```

The Cloudflare Pages project is named `patrickljackson-mockups` (project names can't be
renamed) but is served at the custom domain below.

Live: https://patrickljackson.com  (also https://patrickljackson-mockups.pages.dev)
