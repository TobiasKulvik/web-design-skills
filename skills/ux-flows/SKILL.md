---
name: ux-flows
description: User experience flows, journey design, and conversion thinking for web projects. Use this skill when planning how users move through a site, designing signup/onboarding/checkout flows, placing CTAs and trust signals, reducing friction, or thinking about what users expect and need at each stage. Trigger whenever the agent is building a multi-page site, landing page, e-commerce flow, SaaS onboarding, or any experience where guiding users toward a goal matters.
---

# UX Flows: User Journeys, Conversion & Friction

## Think Entry → Goal → Exit

Every page exists to move the user closer to a goal. Before designing, answer three questions:

1. **Where did the user come from?** (Search, ad, social, direct, internal link)
2. **What do they want?** (Information, a product, to sign up, to compare)
3. **What should they do next?** (Click CTA, fill form, add to cart, read more)

If you can't answer all three, the page doesn't have a clear purpose yet.

## User Intent by Page Type

Different pages serve different mindsets. Match the design to the intent:

| Page type | User intent | What they expect to see |
|-----------|------------|------------------------|
| Landing page | Evaluate a pitch | Clear value prop, one CTA, social proof, no distractions |
| Product page | Decide whether to buy | Price, images, reviews, specs, add-to-cart |
| Pricing page | Compare options | Plans side by side, highlighted recommendation, FAQ |
| Blog/article | Learn something | Readable text, clear headings, related content |
| Documentation | Solve a problem | Search, sidebar nav, code examples, copy buttons |
| Homepage | Understand what this is | Hero with value prop, trust signals, clear paths forward |
| Dashboard | Get status and act | Key metrics visible, actions within reach, no clutter |

## The Friction Checklist

Friction is anything that makes the user pause, think, or give up. Audit every flow for these:

- **Too many steps**: Can any steps be combined or removed?
- **Too many fields**: Ask only for what you need right now — collect the rest later
- **Unclear next action**: Is there exactly one obvious thing to do next?
- **Surprise costs or requirements**: Price, shipping, account creation — show these early, not at the last step
- **Slow feedback**: Does the UI respond instantly? (See interaction-patterns for optimistic UI)
- **Dead ends**: Does every page have a clear next step? Never leave users stranded

## Progressive Disclosure

Don't show everything at once. Reveal complexity as the user needs it:

- **Multi-step forms**: Break long forms into 2-4 steps with a progress indicator. Users who see 3 fields are more likely to start than users who see 15
- **Expandable sections**: Summary visible, details on click (FAQ, feature specs, advanced settings)
- **Staged onboarding**: Collect essentials at signup (email + password), then gather profile details over the first few sessions
- **Contextual help**: Show tooltips and hints near the field that needs them, not in a separate help page

## Cognitive Load

The brain processes ~4 items at a time. Reduce choices to reduce effort:

- One primary CTA per view — if everything is important, nothing is
- Group related options (max 5-7 items per group)
- Use smart defaults so users can accept rather than choose
- Pre-fill what you can (location, currency, returning user data)
- Remove decisions that don't matter to the user (auto-select the best option, let them change later)

## Trust & Social Proof Placement

Trust signals work best placed exactly where hesitation happens:

- **Next to CTAs**: "30-day money-back guarantee" beside the buy button
- **Next to forms**: "We'll never share your email" near the signup field
- **Next to pricing**: Client logos, user count, or review score
- **Early on the page**: 2-3 strong testimonials with real names and faces beat 10 anonymous quotes
- **Checkout**: Security badges, payment provider logos, return policy

### What builds trust

- Real testimonials with names, photos, and specifics ("Increased our conversion by 34%")
- Third-party review scores (Google, Trustpilot, G2)
- Client/partner logos
- Case studies with measurable results
- "As seen in" press mentions
- Active user counts or social proof counters

### What erodes trust

- Stock photos of fake people
- Vague testimonials ("Great product!")
- No contact information or hidden pricing
- Aggressive popups and dark patterns
- Broken pages, outdated content, dead links

## CTA Strategy

- **One primary CTA per section** — don't compete with yourself
- **Action-oriented text**: "Start free trial" not "Submit", "Get the report" not "Click here"
- **Repeat the main CTA** at natural decision points (after hero, after features, after social proof, in footer)
- **Secondary CTAs** for users not ready yet: "See pricing" / "Watch demo" / "Read case study"
- **Sticky CTA** on mobile for long pages — keeps the action always reachable
- **Match CTA to intent**: a blog reader wants "Read more", not "Buy now"

## Signup & Login Flows

- Minimize fields: email + password is enough to start. Name, company, role — collect later
- Offer social login (Google, GitHub, etc.) — reduces drop-off by ~8%
- Show the value before asking for signup (let users explore first)
- Confirm success clearly: redirect to the product, not a "check your email" dead end
- Magic link / passwordless login reduces friction for returning users

## Onboarding Flows

- **First-run experience**: Guide new users to their first success moment as fast as possible
- **Progress indicators**: Show users how far along they are (step 2 of 4)
- **Skippable**: Never block the user from reaching the product — let them skip and come back
- **Contextual, not front-loaded**: Teach features when the user first encounters them, not all at once in a tutorial
- **Empty states that guide**: When a dashboard is empty, don't show a blank page — show what to do first ("Create your first project", "Import your data")

## Checkout & Payment Flows

- Show total cost (including shipping/tax) as early as possible — surprise costs are the #1 reason for cart abandonment
- Guest checkout option — don't force account creation to buy
- Minimize steps: shipping → payment → confirm (3 steps max)
- Auto-fill addresses and payment where possible
- Show security indicators (lock icon, "Encrypted", payment logos)
- Save cart state — if the user leaves and comes back, the cart should still be there
- Confirmation page with clear order summary, expected delivery, and next steps

## Multi-Step Flow Patterns

For any flow longer than one screen:

- **Progress bar or step indicator**: Users need to know where they are and how much is left
- **Back button that preserves input**: Never lose what the user already entered
- **Validation per step**: Check before advancing, not all at the end
- **Save draft / resume later**: For longer flows (applications, onboarding, complex forms)
- **Summary before submit**: Let users review everything before committing

## Drop-Off Prevention

- If users frequently abandon at a specific step, that step has too much friction — simplify it
- Exit-intent: offer to save progress, not a desperate discount popup
- Reduce "registration walls" — let users do as much as possible before requiring an account
- For e-commerce: abandoned cart emails with a direct link back to their cart
- For SaaS: re-engagement emails highlighting what they haven't tried yet

## Page-Level Flow Thinking

Within a single page, content should flow like a conversation:

1. **Hook**: What's in it for the user? (Hero / value prop)
2. **Credibility**: Why should they trust you? (Social proof / logos)
3. **Substance**: What exactly do you offer? (Features / benefits)
4. **Evidence**: Does it work? (Case studies / testimonials / data)
5. **Action**: What should they do now? (CTA)
6. **Objections**: What might hold them back? (FAQ / guarantees)
7. **Final push**: Last CTA for those who scrolled all the way

This mirrors how a conversation works: you don't ask someone to buy before they know what you're selling.
