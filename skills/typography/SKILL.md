---
name: typography
description: Typography system and rules for professional web design. Use this skill when choosing fonts, setting font sizes, configuring line heights, letter spacing, or text styling for any web project. Trigger whenever the agent is writing CSS for text, creating type scales, pairing fonts, or building any UI where text is a primary element—which is virtually every web project since typography IS 80% of UI design.
---

## Why Typography Matters

- Most UIs are just text, buttons, and icons. Typography gives you 80% of the design results.
- Removing font styles from any popular UI instantly breaks hierarchy and usability
- Typography creates hierarchy, guides attention, and communicates tone

## Font Selection

- Choose distinctive, characterful fonts - avoid generic defaults (Arial, Inter, Roboto, system fonts)
- Major font categories: serif (traditional, trustworthy), sans-serif (modern, clean), script (decorative), display (attention-grabbing), monospace (technical)
- Display fonts for headlines and hero text (grabbing attention)
- Body fonts prioritize legibility - rule of thumb: anything longer than 7-10 words should prioritize readability
- Get quality free fonts from Google Fonts
- Variable fonts are strongly recommended (see below)

## Font Pairing: X-Height Harmony

"Looking good together" isn't enough — fonts need to work together at a structural level.
The key metric is **x-height** (the height of lowercase letters like "a", "e", "o"):

- Fonts with matching x-heights align naturally on the same baseline and feel proportional
- A display serif with a SHORT x-height next to a geometric sans with TALL uniform lowercase looks awkward — the visual rhythm is broken
- Best combo for body + subheading: match x-height proportionally, not just aesthetically
- Tools like x-heightable.com help compare ratio differences between font pairs
- When in doubt: pick fonts from the same foundry or superfamily — they're designed to pair

## Variable Fonts

Variable fonts contain multiple weights/widths in a single file and unlock responsive typography:

- **Desktop**: Use expanded letter forms for better readability on wide screens
- **Mobile**: Switch to condensed forms without loading a separate font family
- **Dynamic weight**: Reduce font weight at larger sizes so headings don't overpower the layout (e.g., weight 700 at 16px, but 600 at 40px)
- **Performance**: One variable font file replaces 4-6 static font files
- **Axis control**: Weight, width, slant, and optical size can all be tuned per breakpoint

## Type Scale (The Practical System)

- Pick a base font size: 14px or 16px (1rem), regular weight, 100% lightness
- Design everything at that size first
- When you need to go up or down, move in 2px increments: that's your type scale
- You only need 3-4 font sizes for 90% of UIs: base (14-16px), one heading size, one small size
- Don't create elaborate type scales with 8+ sizes - it leads to messy, inconsistent designs
- Alternative: golden ratio scale (multiply by 1.618) - e.g., 16px → 26px → 42px

## Creating Hierarchy Without Many Sizes

- You DON'T need many font sizes to create hierarchy
- Combine size + weight + color to differentiate: same 16px can look radically different
- Emphasize titles: larger size, heavier weight, higher contrast color
- De-emphasize secondary text: reduce lightness to ~60% (HSL), lighter weight, smaller size
- Use HSL lightness to control emphasis: 100% for titles on dark bg, 60% for secondary text

## Line Height

- Headings: 1.0x to 1.3x the font size (larger text = smaller line height ratio)
- Body text: 1.3x to 1.5x the font size
- The larger the font size, the smaller the relative line height should be
- Line height acts as margin-bottom between text elements - you often don't need extra gap/margin
- Reference: Google headings ~2x, Dropbox ~2x, Uber ~1.5-2x body text

## Letter Spacing

- Headings: use negative letter spacing (-1% to -2%) for a tight, premium feel
- Body text: leave at default or very slightly positive
- Negative letter spacing on body text decreases readability - only use for headings
- Depends on the font, but -1% to -2% for headings is a safe starting point

## Text Width

- Optimal line length: 50-75 characters per line (Baymard Institute research)
- ~18px body text ≈ 600px max-width for desktop
- Long lines are "intimidating and overwhelming" - users avoid reading them
- Less reading = less conversion = less money

## Text Alignment

- Left-align paragraphs and anything over 3 lines of text
- Center alignment OK for headings and short text chunks (1-2 lines)
- NEVER mix center-aligned headings with left-aligned body text (or vice versa)
- Keep alignment consistent between headings and their body text

## Typography Tokens (define once, use everywhere)

| Token | Value | Use |
|-------|-------|-----|
| font-size-base | 1rem (16px) | Body text default |
| font-size-sm | 0.875rem (14px) | Captions, secondary text |
| font-size-lg | 1.125rem (18px) | Lead paragraphs |
| font-size-xl | 1.5rem (24px) | Section headings |
| font-size-2xl | 2rem (32px) | Page headings |
| font-weight-normal | 400 | Body text |
| font-weight-medium | 500 | Emphasis, labels |
| font-weight-bold | 700 | Headings, CTAs |
| line-height-tight | 1.1 | Headings |
| line-height-normal | 1.5 | Body text |

How you store these (CSS variables, Tailwind config, theme object) doesn't matter.
Having them defined and using them consistently does.

## Using rem Units

- Convert px to rem for accessibility: users can adjust base font size
- 1rem = 16px by default
- rem values respect user preferences; px values don't

## Semantic vs Visual Hierarchy

- HTML tags (h1, h2, h3) define document hierarchy for SEO and screen readers
- Visual styling defines what the user sees - these don't have to match
- Use h1 for document hierarchy but style it however the context demands
- A visually large h3 is fine if the document structure calls for it

## Dark Mode Typography

- Lightness inversion formula: dark mode L value → light mode = (100 - L)
- Headings: ~90-95% lightness (NOT pure white 100% — too harsh, causes eye strain)
- Secondary text: ~60% lightness on dark backgrounds (the de-emphasis sweet spot)
- Body text: ~75-80% lightness for comfortable reading
- Swap via your framework's theming mechanism (Tailwind `dark:`, CSS variables, theme provider)

## Micro-Movement in Body Copy (Advanced)

For editorial content, long-form pages, or storytelling layouts:

- Pick 2-3 keywords per paragraph and apply subtle styling differences
- Increase weight by one step OR size by 3-5% OR shift the color slightly
- This creates "micro movement" — the eye stutters slightly on those words, increasing engagement
- It doesn't feel like a highlight — it feels like a pulse, a rhythm in the text
- Use sparingly: works well for editorial, landing page copy, and storytelling — not for app UI or dashboards
