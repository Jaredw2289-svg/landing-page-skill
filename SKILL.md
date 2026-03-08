# /landing-page — Generate a Product Landing Page

A collaborative, 5-phase workflow that produces a high-fidelity landing page + demo video for any product repo. The AI drives the process but pauses at **4 checkpoints** for user alignment.

---

## Overview

| Phase | What happens | Checkpoint |
|-------|-------------|------------|
| 1. Discovery | Read codebase → extract product intent | Confirm Product Brief |
| 2. Style Direction | User picks references → analyze + synthesize | Confirm Style Guide |
| 3. Content Architecture | Plan sections + draft copy | Confirm Section Plan |
| 4. Build | Generate landing page HTML | Review + Iterate |
| 5. Demo Video | Remotion composition → embed MP4 | Final review |

---

## Phase 1: Discovery (no user input needed)

**Goal**: Understand the product deeply enough to write its marketing copy.

**Read these files** (adapt paths to the repo):
- `README.md`, `package.json` / `pyproject.toml` — what it is
- Main UI components — what the product looks like
- CSS / design tokens / tailwind config — existing visual language
- Entry point / skill definition — how users interact with it
- Any existing docs, PRDs, or plans

**Produce a Product Brief** (show to user):
```
Product: [name]
One-liner: [what it does in one sentence]
Target user: [who it's for]
Key flow: [the main user journey, step by step]
Core features: [3-6 bullet points]
Tech stack: [what it's built with]
Design tokens: [fonts, colors, spacing from existing CSS]
```

**🔴 CHECKPOINT 1**: Show the Product Brief. Ask:
> "Does this accurately capture your product? Anything to add or correct?"

---

## Phase 2: Style Direction

**Goal**: Establish the visual identity by combining the user's taste with the product's existing design system.

**🔴 ASK THE USER** (required, don't skip):
> 1. "Which 1-3 websites do you admire visually? I'll study their design and apply the same principles."
> 2. "What overall aesthetic do you want? (e.g., editorial/minimal, bold/dark, warm/organic, glass/futuristic, swiss/clean)"

**After user responds**:
1. `WebFetch` each reference URL → extract:
   - Typography: font families, sizes, weights, hierarchy
   - Color palette: background, text, accent, card backgrounds
   - Layout: spacing, grid, max-widths, section padding
   - Card/component patterns: borders, shadows, radius
   - Animation philosophy: restrained or expressive?
   - Navigation style
2. Synthesize a **Style Guide** combining:
   - Reference site principles (layout, typography, restraint level)
   - Product's existing design tokens (colors, fonts from Phase 1)
   - A coherent color palette (max 3-4 colors)
   - Font pairing (display + body + mono)

**🔴 CHECKPOINT 2**: Present the Style Guide summary. Ask:
> "Here's the style direction I'm going with: [summary]. Should I adjust anything before I start building?"

---

## Phase 3: Content Architecture

**Goal**: Decide what goes on the page and draft the copy.

**Standard landing page modules** (select what fits):

| Module | When to include | Content source |
|--------|----------------|---------------|
| Hero | Always | Product Brief one-liner + CTA |
| Featured/Demo card | If demo video exists | Dark card with product mockup |
| How it Works | Almost always | 3-4 steps from key flow |
| Features | If 3+ features | Feature list from Brief |
| Use Cases | If multiple audiences | Infer from product domain |
| Architecture | If technically impressive | Tech stack from Brief |
| Social Proof | If testimonials exist | External data |
| Pricing | If applicable | User input |
| CTA | Always | Repeat CTA with urgency |
| Footer | Always | Minimal |

**For each module**, draft:
- Headline (short, confident, serif if editorial style)
- Body copy (1-2 sentences max)
- What visual/mockup to include

**Product mockups must be faithful**:
- Read actual component source files
- Match exact colors, fonts, border-radius, spacing
- Show real content (not lorem ipsum)
- Terminal mockups: match the actual CLI interaction flow

**🔴 CHECKPOINT 3**: Present the section plan. Ask:
> "Here's the page structure I'm planning: [list of sections with headlines]. Want to add, remove, or reorder anything?"

---

## Phase 4: Build

**Goal**: Generate a single self-contained HTML file.

**Technical approach**:
- Single HTML file with `<style>` block (no build step needed)
- Tailwind via CDN, or pure CSS (user preference)
- Google Fonts `<link>` for typography
- Scroll reveal via IntersectionObserver
- Responsive: mobile-first with clamp() for fluid sizing
- Keep animations restrained: translateY + opacity for scroll reveals

**Design principles** (from the Anthropic study):
1. **Typography is the design** — large serif headings establish hierarchy
2. **Restraint** — 3 colors max, no decorative blobs/gradients unless style demands it
3. **Whitespace is premium** — generous section padding (100-160px)
4. **Contrast** — alternate light/dark sections for rhythm
5. **Content > decoration** — every element serves the copy

**Product mockups**:
- Read the actual component files from the repo
- Reproduce the exact layout, colors, and content
- Terminal mockups: show the real CLI flow
- Browser mockups: match the real app UI pixel-for-pixel

**🔴 CHECKPOINT 4**: Open the HTML in the browser. Ask:
> "Take a look. What should I change?"

Iterate until the user is satisfied. Common feedback:
- "Mockup doesn't match my product" → re-read component files
- "Too generic" → add more product-specific detail
- "Too busy" → remove decorative elements
- "Copy is wrong" → ask user for exact wording

---

## Phase 5: Demo Video (optional)

**Goal**: Generate a product demo video and embed it.

**When to include**: User asks for it, or the page has a "Watch Demo" button.

**Pipeline**:
1. Create `demo-video/` directory with Remotion project:
   ```bash
   mkdir -p demo-video/src/scenes demo-video/public
   npm init -y
   npm install remotion @remotion/cli @remotion/media react react-dom
   npm install -D typescript @types/react
   ```

2. Define scenes that show the product flow (3-5 scenes, 20-30s total):
   - Scene 1: Entry point (terminal, app launch, etc.)
   - Scene 2: Main interaction (the core product experience)
   - Scene 3: Key feature in action
   - Scene 4: Result / outcome
   - Scene 5: CTA / brand

3. Each scene:
   - Uses exact design tokens from the product
   - Animates with `useCurrentFrame()` + `interpolate()` (NO CSS animations)
   - Has guide text overlays (short phrases, fade in/out)
   - Matches the real product UI faithfully

4. Render: `npx remotion render ProductDemo out/demo.mp4`

5. Embed in landing page with a video modal

**Optional enhancements** (need API keys):
- Background music: `<Audio>` component with volume fade
- TTS voiceover: ElevenLabs `/with-timestamps` → word-level sync
- Captions: `@remotion/captions` → TikTok-style highlighting

---

## Lessons Learned (from real builds)

These patterns consistently produce better results. Follow them.

### What makes a landing page great

1. **Deep codebase reading is non-negotiable.** Read actual component files, CSS, config. Don't guess what the product looks like — reproduce it faithfully. Users instantly notice when mockups don't match their product.

2. **Reference-driven design beats imagination.** Studying 1-3 real sites and extracting their exact design system (font sizes, spacing values, color counts) produces far better results than inventing from scratch.

3. **User participation at checkpoints matters.** The user knows their product best. Asking focused questions at each checkpoint catches misunderstandings early.

4. **Section separation is critical.** Users consistently notice when sections blur together. Use strong visual breaks:
   - Alternate background colors (light/warm/dark)
   - Horizontal rules between major sections
   - Generous padding (100-160px per section)
   - Different card treatments per section (dark cards, light cards, bordered, borderless)

5. **Restraint > decoration.** Three colors + one serif font + whitespace beats a dozen gradients. The Anthropic principle: typography IS the design.

6. **Product-specific content defeats generic copy.** Show the real CLI command, the real UI, the real task flow. "Cancel my Xfinity" > "Make a phone call."

### Common user concerns (proactively address these)

- **"It doesn't look like my product"** — Always read component source files before building mockups
- **"Sections blend together"** — Use background alternation, dividers, and generous padding
- **"Too generic / AI slop"** — Use distinctive fonts, product-specific copy, real screenshots
- **"Copy is wrong"** — Ask the user for their exact positioning language
- **"Too busy"** — Remove decorative elements, increase whitespace
- **"Layout feels flat"** — Alternate between light sections, dark featured cards, warm gradient backgrounds

---

## Enhanced checkpoint questions

At each checkpoint, ask focused questions beyond the basics:

### Checkpoint 1 (Product Brief)
> "Does this capture your product? Specifically:"
> 1. "Is the one-liner positioning right? How do you explain this to people?"
> 2. "Who's the primary user — and what's the emotion they feel when they need this?"
> 3. "What's the ONE thing that makes this different from alternatives?"

### Checkpoint 2 (Style Guide)
> "Here's the style direction. Before I build:"
> 1. "Do you prefer sections to be clearly separated (alternating backgrounds) or flowing (uniform background)?"
> 2. "Should the tone be editorial/serious, playful/casual, or technical/precise?"
> 3. "Any colors, fonts, or visual elements from your existing product I should carry over?"

### Checkpoint 3 (Section Plan)
> "Here's the page structure. Quick questions:"
> 1. "Is there a section here you'd cut? Less is usually more."
> 2. "What's the primary CTA — signup, waitlist, download, or something else?"
> 3. "Do you have a demo video or screenshot I should feature prominently?"

### Checkpoint 4 (Review)
> "Take a look. Focus on:"
> 1. "Do the product mockups match your actual UI?"
> 2. "Does the copy sound like you?"
> 3. "Are sections distinct enough, or do they blur together?"
> 4. "Any section feel too long, too short, or unnecessary?"

---

## Quick-start command

When the user says `/landing-page`, begin with:

> "I'll build a landing page for your product. Let me start by reading your codebase to understand what you've built."

Then immediately start Phase 1 (Discovery) — read files, produce the Product Brief, and hit Checkpoint 1.

---

## File output

| File | Description |
|------|-------------|
| `landing-page.html` | Self-contained landing page |
| `demo-video/out/demo.mp4` | Product demo video (if Phase 5) |
| `demo-video/src/` | Remotion source (if Phase 5) |
