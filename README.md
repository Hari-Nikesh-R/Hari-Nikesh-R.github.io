# Portfolio — Hari Nikesh

Hugo site (Blowfish theme): knowledge base + community site.

## Documentation

Detailed guides are in the **`document/`** folder:

- **[Deployment](document/deployment.md)** — Local dev, GitHub Pages, custom domain, troubleshooting.
- **[Adding content](document/adding-content.md)** — New posts, pages, images, sections, menu, and homepage.
- **[SEO & Indexing](document/seo-and-indexing.md)** — Google Search Console, Bing Webmaster, sitemaps, and indexing setup.

## Deploy to GitHub Pages

1. **Push this repo to GitHub** (e.g. `portfolio` under your user).

2. **Turn on GitHub Pages**
   - Repo → **Settings** → **Pages**
   - Under **Build and deployment**, set **Source** to **GitHub Actions**.

3. **Trigger a deploy**
   - Push to the `main` branch, or
   - **Actions** → **Deploy Hugo to GitHub Pages** → **Run workflow**.

4. **Site URL**
   - Custom domain:
     `https://harinikeshr.dev/`

## Local dev

```bash
cd mysite
hugo server
```

Open http://localhost:1313/
