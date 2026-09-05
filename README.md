# 101 Chauffeur

Marketing site for 101 Chauffeur — Sydney chauffeur hire.

Single self-contained `index.html`. No build step.

- English / 中文 toggle (all copy carries `data-en` / `data-zh`; choice persists in localStorage and auto-detects `zh-*` browsers)
- Photography served from the Unsplash CDN
- Scroll reveals, parallax bands, hero slideshow; all disabled under `prefers-reduced-motion`

## Local preview

    python3 -m http.server 8000

Then open http://localhost:8000

## Deploy

GitHub Pages serves `main` at the repository root.
