---
name: frontend-implementation
description: Frontend implementation principles for translating designs into production-quality web interfaces. Use this skill when building any web project — regardless of CSS approach (Tailwind, vanilla CSS, CSS-in-JS, etc.). Covers design tokens, resets, layout patterns, performance, dark mode strategy, and production readiness. Trigger whenever the agent is writing frontend code, choosing implementation approaches, or shipping a web project.
---

# Frontend Implementation

This skill is about **what to implement**, not which CSS framework to use. The values,
patterns, and principles here apply equally to Tailwind, vanilla CSS, CSS modules, Styled
Components, or any other approach. Focus on the design outcome.

## Design Tokens

Define these token categories at the start of every project. How you store them (CSS
custom properties, Tailwind config, theme object, SCSS variables) doesn't matter — having
them defined and used consistently does. This is the canonical token reference — see
`layout-and-spacing` for spacing principles and `color-systems` for color theory.

### Typography Tokens

| Token | Value | Use |
|-------|-------|-----|
| font-display | A distinctive display/heading font | Headlines, hero text |
| font-body | A legible body font | Paragraphs, UI text |
| font-mono | A monospace font | Code, technical content |
| text-xs | 0.75rem (12px) | Fine print, captions |
| text-sm | 0.875rem (14px) | Secondary text, labels |
| text-base | 1rem (16px) | Body text default |
| text-lg | 1.125rem (18px) | Lead text, emphasis |
| text-xl | 1.25rem (20px) | Section headings |
| text-2xl | 1.5rem (24px) | Page headings |
| text-3xl | 2rem (32px) | Hero subheadings |
| text-4xl | 2.5rem (40px) | Hero headlines |

### Spacing Tokens (base-4 scale)

| Token | Value | Use |
|-------|-------|-----|
| space-1 | 0.25rem (4px) | Icon gaps, tight pairs |
| space-2 | 0.5rem (8px) | Inline element gaps |
| space-3 | 0.75rem (12px) | Button vertical padding |
| space-4 | 1rem (16px) | Default gap, card padding |
| space-6 | 1.5rem (24px) | Section inner padding |
| space-8 | 2rem (32px) | Section gaps |
| space-12 | 3rem (48px) | Major section breaks |
| space-16 | 4rem (64px) | Page section spacing |
| space-24 | 6rem (96px) | Hero-level spacing |
| space-32 | 8rem (128px) | Maximum spacing, full-page breaks |

### Color Tokens (define by role, not by value)

| Token | Purpose | Example value |
|-------|---------|--------------|
| bg-primary | Main page background | white or near-black |
| bg-secondary | Alternate section bg | 4-5% lighter/darker than primary |
| bg-elevated | Cards, raised surfaces | Slightly offset from bg-primary |
| text-primary | Headings, important text | 90-95% contrast (not pure black/white) |
| text-secondary | Supporting text | ~40-60% lightness |
| text-muted | Captions, placeholders | ~60-70% lightness |
| accent | Primary CTA, links | One distinctive brand color |
| accent-hover | Hover state of accent | Slightly darker/lighter than accent |
| border | Dividers, input borders | Subtle, low contrast |
| shadow | Elevation shadows | Semi-transparent black (8-12% opacity) |

### Other Tokens

| Token | Value | Purpose |
|-------|-------|---------|
| radius-sm | 0.25rem (4px) | Subtle rounding (inputs, tags) |
| radius-md | 0.5rem (8px) | Default rounding (buttons, cards) |
| radius-lg | 0.75rem (12px) | Prominent rounding (modals, panels) |
| radius-xl | 1rem (16px) | Large rounding (feature cards) |
| radius-full | 9999px | Pills, avatars |
| transition-fast | 150ms ease | Hover states, toggles |
| transition-base | 200ms ease | General interactions |
| transition-slow | 300ms ease | Reveals, modals |

## CSS Reset Principles

Regardless of framework, ensure these resets are in place:

- **Box sizing**: Everything uses border-box (content + padding + border = declared width)
- **Margins stripped**: Remove default margins from all elements
- **Text size adjust**: Prevent mobile browsers from inflating text
- **Line height**: Set a sensible default (1.5 for body)
- **Font smoothing**: Enable antialiased rendering
- **Images responsive**: All images/video/canvas default to `max-width: 100%; display: block`
- **Form inheritance**: Inputs, buttons, textareas inherit font from parent
- **Word wrapping**: Headings and paragraphs wrap gracefully (overflow-wrap: break-word)

Most frameworks (Tailwind's Preflight, Normalize.css) handle this. If using vanilla CSS,
apply a reset like Josh Comeau's CSS Reset or Andy Bell's Modern Reset.

## Layout Implementation Patterns

### Page Container
- Max width: 1200px (or 1280px for wider layouts)
- Centered with auto margins
- Horizontal padding: 1rem on mobile, 2rem on desktop
- This gives content breathing room without touching screen edges

### Responsive Grid
- Use CSS Grid `auto-fit` with `minmax(300px, 1fr)` for cards that auto-reflow
- This eliminates the need for most breakpoint-specific column rules
- Gap between grid items: 1.5rem–2rem

### Flex Row
- Default for component-level layouts (nav items, button groups, icon + text)
- Center vertically, gap between items
- Use wrap to let items flow to next line on small screens

### Stack (Vertical Rhythm)
- Siblings separated by consistent spacing using gap or the lobotomized owl (`* + *`)
- Default vertical gap: 1rem between paragraphs, 2rem between sections

### Text Containers
- Max width for body text: 600px or 65ch (keeps line length at 50-75 characters)
- Center text containers for readability
- Don't constrain headings to the same width — they can span wider

## Naming Things

- Name by **role**, not by value: "accent" not "blue", "bg-elevated" not "gray-100"
- Be descriptive: "card-header" not "ch"
- Pick one convention (BEM, utility-first, component scoping) and stick with it
- Consistency matters more than which convention you choose

## CSS Architecture

Use CSS cascade layers (`@layer`) to manage specificity and prevent style conflicts:

- **Layer order**: `@layer reset, base, components, utilities;` — later layers override earlier ones
- **Resets** go in the lowest layer so they never override component styles
- **Base** styles (typography defaults, link colors) sit above resets
- **Components** hold your actual UI styles
- **Utilities** (overrides, Tailwind-style helpers) go last so they always win
- This eliminates specificity wars — a utility class always beats a component class regardless of selector complexity
- Most frameworks handle this for you (Tailwind v4 uses layers natively), but understanding the concept helps when debugging

## Performance

### Core Web Vitals (what Google actually ranks on)

- **LCP** (Largest Contentful Paint): target < 2.5s — optimize your hero image/heading, preload critical assets
- **CLS** (Cumulative Layout Shift): target < 0.1 — always set width/height on images, reserve space for dynamic content, avoid injecting content above the fold after load
- **INP** (Interaction to Next Paint): target < 200ms — keep main thread unblocked, defer heavy computation, use `requestIdleCallback` for non-urgent work

### Asset Optimization

- **Images**: Use WebP/AVIF formats, lazy-load below-fold images, always set width/height to prevent layout shift, target ~300KB max per image
- **Fonts**: Preload critical fonts, use `font-display: swap`, limit to 2-3 font files. Subset fonts to remove unused character ranges (significant savings for non-Latin scripts)
- **Scripts**: Minimize third-party scripts, defer non-critical JS
- **CSS**: Purge unused styles in production. Use `content-visibility: auto` on below-fold sections to skip rendering until needed
- **Audit**: Use Lighthouse — target Performance >90, Accessibility >90

## Use Real Content, Not Lorem Ipsum

- Design with realistic content lengths and word counts
- Lorem ipsum hides spacing, hierarchy, and wrapping problems
- Real text reveals how the design actually performs
- Test with both short and long content to verify flexibility

## Production Checklist

Before shipping, verify:

- All images have descriptive alt text
- Favicon and meta tags (title, description) are set
- Open Graph and social meta tags are configured
- No broken links (check with a crawler or Lighthouse)
- Mobile-friendly at 320px, 768px, 1024px, 1920px
- Lighthouse: Performance >90, Accessibility >90
- Touch targets are at least 44x44px
- Forms validate properly and preserve input on error
- Dark mode works (system preference or manual toggle)
- 301 redirects set for any changed URLs
- Font loading doesn't cause layout shift
- No horizontal scroll at any viewport width
