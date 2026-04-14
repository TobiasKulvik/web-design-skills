---
name: seo
description: Search engine optimization for web projects. Use this skill when setting up page metadata, Open Graph tags, structured data, sitemaps, or making any decisions about how a site appears in search results and social previews. Trigger whenever the agent is building pages that need to be discoverable — landing pages, marketing sites, blogs, e-commerce, documentation — or when configuring meta tags, canonical URLs, robots directives, or JSON-LD.
---

# SEO & Discoverability

## Core Principle

SEO is not a bolt-on — it's built into good web design. Semantic HTML, fast performance,
accessible markup, and clear content structure are already SEO fundamentals. This skill
covers the metadata and configuration layer that sits on top of those foundations.

## Page Metadata (Every Public Page Needs These)

### Title Tag

- Every page needs a unique, descriptive `<title>`
- Length: 50-60 characters (Google truncates beyond ~60)
- Format: `Page Topic — Brand Name` or `Brand Name | Page Topic`
- Front-load the important keywords — users scan from the left
- Don't stuff keywords — write for humans first, search engines second

### Meta Description

- `<meta name="description" content="...">` on every public page
- Length: 120-155 characters (Google truncates beyond ~155)
- Write it like ad copy — this is what appears in search results
- Include a value proposition and implicit call to action
- Unique per page — duplicate descriptions across pages hurt rankings

### Language

- Set `lang` attribute on `<html>` (e.g., `<html lang="en">`)
- For multilingual sites, use `hreflang` tags to indicate language alternatives
- Inline foreign-language content should use `lang` on the containing element

## Open Graph (Social Previews)

When someone shares your URL on Slack, Twitter, LinkedIn, Discord, or iMessage, Open Graph
tags control what the preview looks like. Missing OG tags = ugly link with no image.

### Required Tags

```html
<meta property="og:title" content="Page Title">
<meta property="og:description" content="Brief description of the page">
<meta property="og:image" content="https://example.com/og-image.jpg">
<meta property="og:type" content="website">
<meta property="og:url" content="https://example.com/page">
```

### Image Guidelines

- Recommended size: 1200x630px (1.91:1 ratio) — this is the universal safe zone
- Minimum: 600x315px
- File size: under 1MB, prefer WebP or JPEG
- Include text on the image sparingly — it should work as a visual, not a slide
- Test previews with sharing debuggers (LinkedIn Post Inspector, Facebook Sharing Debugger, opengraph.xyz)

### When to Skip OG Tags

**Authenticated/private pages** (dashboards, settings, admin panels) don't need Open Graph
tags — crawlers and social previews will never reach them. You can still set `<title>` and
`<meta description>` for browser tabs and history, but don't add `og:image`, JSON-LD, or
structured data to pages behind auth.

## Canonical URLs

- Every public page should have `<link rel="canonical" href="https://example.com/page">`
- Points search engines to the "official" version of the page
- Prevents duplicate content issues from: www vs non-www, trailing slashes, query parameters, HTTP vs HTTPS
- Self-referencing canonicals are fine and recommended (a page pointing to itself)
- For paginated content, each page gets its own canonical (don't point page 2 to page 1)

## Structured Data (JSON-LD)

Structured data helps search engines understand your content and can unlock rich results
(star ratings, FAQs, breadcrumbs, product info in search results).

### Implementation

- Use JSON-LD format: `<script type="application/ld+json">{...}</script>`
- Place in the `<head>` or at the end of `<body>`
- Always include `@context: "https://schema.org"` and `@type`

### Common Schemas

| Schema | Use When | Rich Result |
|--------|----------|-------------|
| `Organization` | Homepage, about page | Knowledge panel, logo in search |
| `Product` | Product pages | Price, availability, reviews in search |
| `Article` | Blog posts, news | Headline, date, author in search |
| `FAQ` | FAQ sections | Expandable Q&A directly in search results |
| `BreadcrumbList` | Sites with hierarchy | Breadcrumb trail in search results |
| `LocalBusiness` | Physical businesses | Map, hours, address in search |
| `HowTo` | Tutorial/guide pages | Step-by-step in search results |

### Validation

- Test with Google's Rich Results Test before shipping
- Check Search Console for structured data errors after deployment

## Robots & Crawling

### robots.txt

- Place at site root: `https://example.com/robots.txt`
- Allow crawling of public pages, block private/admin routes
- Reference your sitemap: `Sitemap: https://example.com/sitemap.xml`
- Don't block CSS/JS files — crawlers need them to render pages

### Meta Robots

- Public pages: no robots meta needed (indexable by default)
- Private/authenticated pages: `<meta name="robots" content="noindex, nofollow">`
- Staging/preview environments: block everything with `noindex` or `robots.txt`
- `noindex` prevents the page from appearing in search; `nofollow` prevents link equity from flowing through

## Sitemap

- Generate an XML sitemap at `/sitemap.xml` listing all public, canonical URLs
- Include `<lastmod>` dates so crawlers know what changed
- Most frameworks generate sitemaps automatically (Next.js `sitemap.ts`, Astro sitemap integration, etc.)
- Submit to Google Search Console after deploying
- Keep it under 50,000 URLs per sitemap file (split into multiple if larger)
- Don't include authenticated, `noindex`, or non-canonical pages

## URL Structure

- Readable, hierarchical URLs: `/products/shoes/blue-runner` not `/page?id=42`
- Use hyphens, not underscores: `/my-page` not `/my_page`
- Keep URLs short and descriptive — they appear in search results
- Lowercase only — mixed case causes duplicate content issues on some servers
- Set up 301 redirects when changing URLs — broken links hurt rankings and user trust

## Image SEO

- Descriptive filenames: `blue-running-shoes.webp` not `IMG_4382.webp`
- Descriptive `alt` text on every meaningful image (this also serves accessibility)
- Use `width` and `height` attributes to prevent layout shift (CLS)
- Lazy-load below-fold images with `loading="lazy"`
- Include key images in the XML sitemap for image-heavy sites
- Use modern formats (WebP, AVIF) for faster loading

## Internal Linking

- Link between related pages with descriptive anchor text
- "Read our pricing guide" beats "click here" — anchor text tells search engines what the linked page is about
- Every important page should be reachable within 3 clicks from the homepage
- Use breadcrumbs for deep hierarchies (also improves UX and structured data)
- Fix broken internal links promptly — they waste crawl budget and frustrate users

## Performance as SEO

Google uses Core Web Vitals as ranking signals. See `frontend-implementation` for the
complete performance section, but the SEO-critical metrics are:

- **LCP** < 2.5s (how fast the main content loads)
- **CLS** < 0.1 (how much the layout shifts during load)
- **INP** < 200ms (how fast the page responds to interaction)

Slow pages rank lower and have higher bounce rates — performance is both a UX and SEO concern.

## Common Mistakes

- Duplicate `<title>` or `<meta description>` across pages
- Missing `og:image` (results in ugly social previews)
- Blocking public pages in `robots.txt`
- Using JavaScript-only rendering without SSR/SSG (crawlers may not execute JS)
- Orphan pages with no internal links pointing to them
- Redirect chains (A → B → C instead of A → C)
- Mixed content (HTTP resources on HTTPS pages)
- Missing alt text on images (hurts both SEO and accessibility)

## See Also

- **`content-structure`** — page anatomy, heading hierarchy, content writing for the web
- **`accessibility`** — semantic HTML and alt text (shared foundation with SEO)
- **`frontend-implementation`** — Core Web Vitals, performance optimization, production checklist
