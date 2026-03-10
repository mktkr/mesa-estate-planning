# Mesa Estate Planning — Website

Built with [Astro](https://astro.build) for maximum SEO performance and deployed on [Vercel](https://vercel.com).

## Project Structure

```
mesa-estate-planning/
├── public/
│   ├── images/          ← Photos, logos (family-hero.jpg goes here)
│   ├── downloads/       ← PDFs, checklists for download
│   ├── robots.txt       ← SEO crawl rules
│   └── favicon.svg
├── src/
│   ├── components/      ← Reusable components (SEOHead, etc.)
│   ├── layouts/         ← Page templates
│   │   ├── BaseLayout.astro      ← Nav + footer wrapper (every page)
│   │   ├── ServiceLayout.astro   ← Service pages (wills, trusts, etc.)
│   │   ├── BlogLayout.astro      ← Blog posts / articles
│   │   └── LocationLayout.astro  ← Location pages (Mesa, Chandler, etc.)
│   ├── pages/           ← Every file here = a URL on your site
│   │   ├── index.astro           ← Homepage
│   │   ├── contact.astro         ← Contact page
│   │   ├── services/             ← /services/wills-and-trusts, etc.
│   │   ├── locations/            ← /locations/chandler, etc.
│   │   ├── about/                ← /about/mckay-tucker, etc.
│   │   └── blog/                 ← /blog/article-slug, etc.
│   ├── content/         ← Markdown content (for Clara to manage)
│   │   ├── blog/
│   │   ├── services/
│   │   └── locations/
│   └── styles/
│       └── global.css   ← All site styles
├── astro.config.mjs     ← Site config (your domain, sitemap)
├── package.json
└── tsconfig.json
```

## How to Deploy (One-Time Setup)

### Step 1: Push to GitHub
1. Go to github.com → New Repository → name it `mesa-estate-planning`
2. Upload all these files to the repository
3. Make sure `family-hero.jpg` is in `public/images/`

### Step 2: Connect to Vercel
1. Go to vercel.com → Sign up with your GitHub account
2. Click "Import Project" → Select your `mesa-estate-planning` repo
3. Vercel auto-detects Astro — just click "Deploy"
4. Your site is live at a `.vercel.app` URL within 60 seconds

### Step 3: Connect Your Domain
1. In Vercel dashboard → Settings → Domains
2. Add `mesaestateplan.com` and `www.mesaestateplan.com`
3. Vercel gives you DNS records to add at your domain registrar
4. SSL certificate is automatic

## How to Add Content

### New Blog Post
Create a file in `src/pages/blog/` like `my-new-post.astro`:
```astro
---
import BlogLayout from '../../layouts/BlogLayout.astro';
---
<BlogLayout
  title="Your Post Title"
  description="Brief description for Google"
  publishDate="2025-04-01"
  category="Trusts"
  readTime="5 min read"
>
  <p>Your content here...</p>
  <h2>Subheading</h2>
  <p>More content...</p>
</BlogLayout>
```

### New Service Page
Create a file in `src/pages/services/` — see `wills-and-trusts.astro` for the pattern.

### New Location Page
Create a file in `src/pages/locations/` — see `chandler.astro` for the pattern.

### New PDF Download
Drop the PDF in `public/downloads/`. It's instantly available at `mesaestateplan.com/downloads/filename.pdf`.

## For Clara (AI Agent)
Clara can manage this site by:
1. Creating/editing files in the repo
2. Pushing changes via `git add . && git commit -m "description" && git push`
3. Vercel auto-deploys every push within ~30 seconds

No CMS login, no API keys, no browser automation needed.

## SEO Features Built In
- Server-rendered HTML (Google sees full content immediately)
- Auto-generated sitemap at `/sitemap-index.xml`
- Schema.org markup on every page (LocalBusiness, Attorney, Article, LegalService)
- Open Graph + Twitter Card meta tags
- Canonical URLs
- Robots.txt
- Fast page loads (100/100 Lighthouse target)
