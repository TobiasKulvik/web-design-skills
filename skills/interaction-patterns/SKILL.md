---
name: interaction-patterns
description: Web interaction patterns, UX conventions, and user behavior guidelines. Use this skill when designing user flows, interactive elements, microinteractions, animations, hover states, or any behavior-driven design decisions. Trigger whenever the agent is building forms, navigation flows, e-commerce experiences, onboarding sequences, or any interface where user behavior and expectations matter.
---

# Interaction Patterns: Web UX Conventions & User Behavior

## Respect User Expectations

- Buttons look like buttons, links look like links
- Navigation at top or side, logo top-left, search with magnifying glass
- These patterns exist because they WORK — users feel comfortable with conventions
- "Sticking to standard design won't make your work boring — it makes it good"
- The goal isn't to reinvent the wheel, just make it roll better

## Satisficing (How Users Actually Behave)

- Users don't analyze the whole UI — they scan and click the first reasonable option
- If it doesn't work, they go back and try again
- Design for "first reasonable click" being the right one
- Map user flows: track the shortest path from entry → goal completion

## The Three Fundamentals of Web Animation

Animation is not decoration. It communicates meaning, follows real-world physics, and
choreographs the user's attention. Get these three right and even simple animations feel
professional. Get them wrong and the fanciest effects feel off.

### 1. Meaning — Animation Should Match the Brand

Every animation should communicate the character of the site:

- **Kids' website / playful brand**: Fun, quirky, bouncy animations
- **Elegant brand / luxury**: Slow-paced, delicate fades, soft transitions
- **Productivity app / dashboard**: Snappy, minimal, functional transitions
- **Creative agency**: Bold, expressive, cinematic reveals

Before animating anything, ask: "If this business were a person, how would they move?"
The answer determines your animation style. A 3-2-1 movie countdown for a video production
company's loading screen has meaning. A random spinner does not.

Also consider: can the animation tie to the brand's visual identity? (e.g., a company logo
that doubles as a loading animation, or page transitions shaped like the product)

### 2. Physics — Make It Feel Real

Objects in real life don't appear and disappear instantly. Animations that respect physics
feel natural; those that don't feel jarring.

**Consistent direction**: All elements in a transition should move in the SAME direction.
If a slider swipes right-to-left, every element within it (images, text, buttons) should
also move right-to-left. Multiple conflicting directions feel chaotic.

**Mass affects speed**: Bigger elements should animate SLOWER (they have more visual
"mass"), smaller elements should animate FASTER. A CTA button snaps into place in 150ms.
A hero image glides in over 600-800ms. This mirrors how physical objects with different
weights behave — a feather moves differently than a boulder.

**Never use linear easing**: Linear motion (constant speed) looks robotic and unnatural.
The only exception is looping digital/pixel-art effects. For everything else, use curves
with steep acceleration: fast start → gradual deceleration (ease-out), or slow start →
snap to position (ease-in). A recommended all-purpose curve: cubic-bezier(0.9, 0, 0, 0.1)
for a steep, natural-feeling motion.

### 3. Choreography — Animation Order = Hierarchy

Choreography is a coordinated sequence of motion that maintains the user's focus as the
interface changes. It establishes hierarchy through animation:

- **What doesn't move** = lowest priority (nav items, structural chrome)
- **What animates first** = secondary elements (buttons, labels — they snap in quickly)
- **What animates LAST** = most important element (hero image, main content)

The most important element should finish its animation last, so it's the final thing the
eye settles on. Everything else is supporting choreography leading up to that moment.

**Anticipation** (borrowed from Disney animation): Before an action happens, hint at it.
On hover, slightly scale up the element to signal "this will become the focus if you click."
On click, briefly compress before expanding (like a spring). This prepares the user for
what's about to happen.

### Don't Animate Everything

Be selective. Animate the important elements and leave the rest static. Nav items, small
icons, and structural elements usually don't need animation. If everything moves, nothing
stands out — it's visual noise. Choose:

- **Important elements**: Hero content, CTAs, key transitions between states
- **Character details**: Small delightful touches (a logo animation, a hover spark on a CTA)
- **Leave static**: Navigation, footer, background elements, metadata

### Animation Reference Values

| Feel | Duration | Easing | Use for |
|------|----------|--------|---------|
| Snappy | 150-200ms | ease-out | Hovers, toggles, button states, small elements |
| Smooth | 250-300ms | cubic-bezier(0.4, 0, 0.2, 1) | Panel opens, material-style transitions |
| Cinematic | 500-800ms | cubic-bezier(0.9, 0, 0, 0.1) | Hero reveals, page transitions, large images |
| Bouncy | 400-500ms | cubic-bezier(0.16, 1, 0.3, 1) | Playful entrances, fun brands |

**Duration rule of thumb**: Small elements (buttons, icons) = 150-200ms. Medium elements
(cards, panels) = 250-400ms. Large elements (hero images, full-section reveals) = 500-800ms.

Only animate `transform` and `opacity` for best performance (GPU-accelerated). Animating
layout properties (width, height, margin) causes reflow and jank.

### High-Impact Animation Strategy

- One well-orchestrated page load with staggered reveals > scattered microinteractions
- Use staggered `animation-delay` to create a sequence: nav appears → headline fades in → CTA slides up → image reveals last
- Scroll-triggered animations (via Intersection Observer) engage users as they scroll — ~50% of web animations use viewport detection
- Smooth scroll libraries (like Lenis) prevent the janky feeling of scroll-linked animations on mouse wheels

### Hover States

- Every interactive element needs a hover state — no exceptions
- Buttons: darken/lighten background, subtle scale, shadow shift
- Links: underline, color change
- Cards: lift with shadow, slight translateY(-2px)
- Images: subtle zoom, overlay appearance
- Use anticipation: slight scale-up on hover signals "this is clickable and something will happen"

## Optimistic UI Updates

- Update the UI immediately when success is likely
- Reconcile with the server response when it arrives
- On failure: show an error and roll back, or provide Undo
- This makes the interface feel instant and responsive

## Form Interactions

- Submit on Enter when there's a single text input
- Show validation feedback as the user types (debounced)
- Inline errors next to the relevant field, not at the top of the form
- Celebrate success: show confirmation clearly, not just a flash message
- Auto-focus the first field when a form appears

## Scroll Behavior

- Smooth scrolling for in-page navigation: `scroll-behavior: smooth`
- Anchor links with smooth scroll and offset for sticky headers
- Infinite scroll or "Load more" instead of pagination for feeds
- Progress indicators for long pages

## Loading States

- Skeleton screens > spinners (they feel faster)
- Show existing content immediately, load additional data progressively
- Indicate loading inline, near the content that's loading
- Never block the entire UI for a single loading operation

## Error Handling

- Clear, human language: "We couldn't save your changes" not "Error 500"
- Actionable: tell users what to do next
- Non-destructive: preserve user input on error
- Inline where possible: highlight the specific field, not a generic alert

## Feedback Patterns

- Confirmation after successful actions
- Progress for multi-step processes
- Undo for destructive actions (delete, archive)
- Inline validation (green check, red X) as users fill forms

## Click and Touch

- Underline clickable text to distinguish from plain text
- Make clickable areas generous (larger than the text)
- On mobile: swipe gestures should have button alternatives
- Double-tap zoom: ensure it doesn't conflict with interactions

