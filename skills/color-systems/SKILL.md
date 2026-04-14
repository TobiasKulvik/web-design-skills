---
name: color-systems
description: Color system design and implementation for web interfaces. Use this skill when choosing colors, building color palettes, creating themes, implementing dark/light modes, or making decisions about visual emphasis through color. Trigger whenever the agent needs to pick UI colors, create CSS color variables, build a theming system, or ensure proper color contrast and harmony in a web project.
---

# Color Systems for Web Interfaces

## The Three Color Categories You Need

1. **Neutral colors**: Background, text, borders, and most UI elements
2. **Brand/primary color**: Main actions (buttons, links, active states) - adds character
3. **Semantic colors**: Success (green), warning (amber), error (red), info (blue) - communicate states

That's it. These are ALL the colors you need for apps and UIs.

## Use HSL (or OKLCH) Instead of Hex/RGB

- **Hex/RGB**: codes are meaningless — three grays look similar but the values tell you nothing
- **HSL** = Hue (0-360°), Saturation (0-100%), Lightness (0-100%) — the code describes the color
- **OKLCH** = L (0-1), C (0-0.4), H (0-360) — perceptually uniform, Tailwind v4 default

### Why OKLCH beats HSL

HSL has a significant flaw: colors lose saturation at extreme lightness values. A vibrant
blue at 50% L looks washed out at 90% L. OKLCH fixes this — equal lightness steps look
genuinely equal to the human eye, and colors maintain their vibrancy across the full range.
For UI work, chroma values rarely need to exceed 0.15-0.2.

## Building a Neutral Palette with Lightness

- Set hue and saturation to 0 (pure neutrals) or very low saturation for warm/cool tints
- Create shades using only lightness increments of 5-10%
- Dark mode base: start at 0% lightness, then 5%, then 10% for surfaces
- Light mode: subtract the dark mode L value from 100%

### Dark Mode Neutral Scale (lightness values)

The table below uses HSL lightness percentages for familiarity. If using OKLCH, L maps
similarly (0-100% or 0-1), but chroma (C) replaces saturation and typically stays under
0.15 for UI work. The inversion formula works the same in both color spaces.

| Role | Dark mode L (HSL) | Light mode L (HSL) |
|------|--------------------|--------------------|
| Base background | 0% | 100% |
| Surface (cards) | 5% | 95% |
| Elevated elements | 10% | 90% |
| Primary text | 90% | 10% |
| Secondary text | 60% | 40% |
| Borders | 15% | 85% |

**The lightness inversion formula:** light mode L = 100 - dark mode L. This single rule
generates a mathematically balanced color system without guesswork. Set hue and saturation
to 0 for pure neutrals, or add 5-15% saturation for warm/cool tinted neutrals.

### The 60% De-emphasis Sweet Spot

When you need to push text to the background (secondary labels, captions, metadata),
set its lightness to ~60% on dark backgrounds or ~40% on light backgrounds. This is the
sweet spot: readable but visually recessive. Going lower makes it unreadable; going higher
makes it compete with primary text.

## The 60-30-10 Rule

- **60%** dominant neutrals (background, large surfaces)
- **30%** brand/secondary colors (cards, sections, accents)
- **10%** accent/CTA color (buttons, links, key actions)
- Reserve one bold color exclusively for call-to-action elements so users instinctively know it means "click"

## Color for Emphasis and Hierarchy

- Highest contrast = most important (text on dark bg, bold colors in sea of neutrals)
- De-emphasize by reducing lightness contrast
- Bold colors in a sea of neutrals create instant focal points
- Use lightness to highlight active states: lighter shades appear on top/more important

## Implementing Dark/Light Mode

Two valid approaches (pick based on project):

1. **System preference**: Detect `prefers-color-scheme` and swap color tokens automatically
2. **Manual toggle**: User chooses via a UI toggle; store preference in local storage or a cookie

Either way, the mechanism is the same: define two sets of color tokens and swap them. If
you've built with semantic color tokens (bg-primary, text-primary, etc.) from the start,
dark mode is just a palette swap — no component changes needed.

Most frameworks support this natively (Tailwind's `dark:` prefix, CSS custom properties
with `prefers-color-scheme`, theme providers in CSS-in-JS).

## Adding Hue and Saturation

- Once neutrals are set, experiment with hue and saturation
- Even low saturation (5-15%) adds warmth or coolness to neutrals
- Check brand/primary colors especially on hover and active states
- Gradients: create using background colors, reveal full gradient on hover
- Border highlights: use lighter color on top edge to simulate light source from above

## Shadows Done Right

This is the canonical shadow reference — other skills reference this section.

- Never use pure black for shadows — it looks harsh and fake
- Use semi-transparent black: `rgba(0,0,0,0.08)` to `rgba(0,0,0,0.15)` for subtle, realistic elevation
- Layer two shadows for depth: a short tight one (1px blur, ~12% opacity) + a longer diffuse one (12px blur, ~6% opacity)
- On dark backgrounds, shadows are nearly invisible — use subtle lighter borders or faint glows instead
- Shadows and borders serve the same purpose (elevation) — use one or the other, rarely both

## Color Harmony Quick Reference

- **Analogous**: colors next to each other on the wheel (harmonious, low contrast)
- **Complementary**: colors opposite on the wheel (high contrast, vibrant)
- **Triadic**: three equally spaced colors (balanced, colorful)
- For most web projects, stick with one brand color + neutrals. Don't overcomplicate.

## Never Use Pure Black or White for Text

- Pure white (#fff) on pure black (#000) is too harsh
- Use 90-95% lightness for white text, 5-10% lightness for dark text
- The subtle softening is easier on the eyes over long reading sessions

## Image Color Integration

- Match image colors to the overall site palette where possible
- A neon pink hoodie on a sleek black-and-white site looks unprofessional
- Use images where people look toward key content (eyes naturally follow gaze)
- Images should support the design, not fight it

## See Also

- **`typography`** — dark mode text lightness values, font color hierarchy
- **`visual-hierarchy`** — using color contrast for emphasis and de-emphasis
- **`frontend-implementation`** — color token naming conventions and complete token reference
