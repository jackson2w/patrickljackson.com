# Patrick Ian Jackson — Website Concepts

Three homepage design directions for Rev. Patrick Ian Jackson (pastor, author, speaker),
presented for review. Static HTML, no build step.

## Structure

| Path | Direction |
|------|-----------|
| `index.html` | Concept chooser — links to all three |
| `example-1-classic/` | Classic & traditional — navy & cream, Cormorant/EB Garamond |
| `example-2-editorial/` | Modern & editorial — Fraunces/Inter, vermillion accent |
| `example-3-warm/` | Warm & personal — Newsreader/Public Sans, terracotta palette |
| `assets/` | Portrait (`.webp`), social share image (`og.webp`), source JPGs |
| `_headers` | Cloudflare Pages edge caching + security headers |

## Optimizations applied

- **Golden Ratio Typography** — body line-heights derived from the GRT calculator
  (size × measure), not hand-picked.
- **Images** — hero re-cropped to a head-and-shoulders portrait and served as WebP
  (700×814, q80, ~86 KB); explicit `width`/`height` to prevent layout shift;
  `fetchpriority="high"` on the LCP hero.
- **SEO / social** — per-page `description`, `canonical`, and Open Graph tags with a
  1200×630 `og.webp` share image.
- **Semantic HTML** — `<main>` landmark, single `<h1>` per page, descriptive `alt` text.
- **Edge headers** — immutable caching on `/assets/*`, security headers on HTML.

## Local preview

```bash
python3 -m http.server 8000   # then open http://localhost:8000
```

## Deploy

Static site, deploy directory is the repo root (no build command).

```bash
npx wrangler pages deploy . --project-name patrickljackson-mockups
```

Live: https://patrickljackson-mockups.pages.dev
