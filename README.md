# Web Design Skills

A modular skill library that helps AI agents build better websites. Framework-agnostic — focuses on design values and outcomes, not specific CSS approaches.

## Skills

| Skill | What it covers |
|-------|---------------|
| **layout-and-spacing** | Grid systems, spacing scale, white space, spatial echo |
| **typography** | Font selection, type scale, x-height pairing, variable fonts |
| **color-systems** | HSL/OKLCH palettes, dark/light mode, 60-30-10 rule |
| **visual-hierarchy** | Emphasis, scanability, visual compression |
| **responsive-design** | Flexbox/grid essentials, breakpoints, mobile-first |
| **ui-components** | Buttons, cards, navigation, forms, modals, images |
| **interaction-patterns** | Animation fundamentals, hover states, loading, errors |
| **ux-flows** | User journeys, conversion, onboarding, checkout, trust signals |
| **seo** | Meta tags, Open Graph, structured data, sitemaps, crawling |
| **app-patterns** | App shells, sidebar nav, tabs, command palettes, app-specific components |
| **internationalization** | Multi-language design, RTL, text expansion, cultural sensitivity |
| **content-structure** | Page anatomy, heading hierarchy, information density |
| **accessibility** | Contrast, keyboard nav, ARIA, touch targets |
| **frontend-implementation** | Design tokens, resets, performance, production checklist |

## Install

### Quick install

```bash
npx skills add TobiasKulvik/web-design-skills
```

Works with Cursor, Claude Code, Codex, Windsurf, and other agents.

### Manual install (Claude Code)

Clone the repo into your project's `.claude/skills/` directory:

```bash
git clone https://github.com/TobiasKulvik/web-design-skills.git .claude/skills/web-design-skills
```

Or for personal use across all projects:

```bash
git clone https://github.com/TobiasKulvik/web-design-skills.git ~/.claude/skills/web-design-skills
```

### Usage

The orchestrator skill (`SKILL.md`) guides which sub-skills to read based on what you're building. For new projects, start with content-structure → layout-and-spacing → typography → color-systems → frontend-implementation, then consult the others as needed.
