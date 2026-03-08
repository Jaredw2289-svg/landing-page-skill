# /landing-page — Generate a Product Landing Page

A collaborative workflow that produces a high-fidelity landing page for any product. Works with mature codebases, early prototypes, or even just an idea in your head.

**Core principle: Listen first, build second.** The AI asks questions, absorbs the user's vision, and only starts building when it truly understands the product. The user participates at every decision point.

---

## Overview

| Phase | What happens | Checkpoint |
|-------|-------------|------------|
| 0. Assess | Scan repo → decide if code or idea-first | — |
| 1. Discovery | Understand the product (from code or conversation) | Confirm Product Brief |
| 2. Style Direction | User picks references → analyze + synthesize | Confirm Style Guide |
| 3. Content Architecture | Plan sections + draft copy | Confirm Section Plan |
| 4. Build | Generate landing page HTML | Review + Iterate |
| 5. Demo Video | Remotion composition → embed MP4 (optional) | Final review |

---

## Phase 0: Understand the Starting Point

**Before anything else**, ask the user what they're working with. Don't guess — confirm.

Quickly scan the repo to get a sense of what exists, then ask:

> "Before I start, let me confirm what we're working with. Which best describes your situation?"
>
> 1. **I have a working product** — there's code in this repo, and I want a landing page for it.
> 2. **I have a product doc / PRD** — no code yet, but I have a written description. (Share the file path and I'll read it.)
> 3. **I just have an idea** — nothing written yet. I'll describe it to you.

Wait for the user to answer. Then:

| User says | Path |
|-----------|------|
| "I have code" (or you can see substantial code) | → **Phase 1A: Code-First Discovery** |
| "I have a doc / PRD" | → **Phase 1B: Doc-First Discovery** — read the doc, then fill gaps with questions |
| "I just have an idea" | → **Phase 1C: Idea-First Discovery** — interview the user |
| Ambiguous (some code, some docs, unclear product) | → **Phase 1B** — read what exists, ask about the rest |

---

## Phase 1A: Code-First Discovery

**When**: The repo has a working or near-working product.

**Read these files** (adapt paths to the repo):
- `README.md`, `package.json` / `pyproject.toml` — what it is
- Main UI components — what the product looks like
- CSS / design tokens / tailwind config — existing visual language
- Entry point / main flow — how users interact with it
- Any existing docs, PRDs, or plans

**Produce a Product Brief** (show to user):
```
Product: [name]
One-liner: [what it does in one sentence]
Target user: [who it's for]
Problem: [the pain point it solves]
Key flow: [the main user journey, step by step]
Core features: [3-6 bullet points]
Tech stack: [what it's built with]
Design tokens: [fonts, colors, spacing from existing CSS]
```

**🔴 CHECKPOINT 1**: Show the Product Brief. Ask:
> 1. "Does this capture your product? How do YOU explain it to people?"
> 2. "Who's the primary user — and what emotion do they feel when they need this?"
> 3. "What's the ONE thing that makes this different from alternatives?"

---

## Phase 1B: Doc-First / Hybrid Discovery

**When**: The user has a PRD, product doc, pitch deck, or partial codebase — but not a fully working product.

**Step 1: Read everything available.**
- If user shared a doc path → read it thoroughly
- If there's partial code → scan it for product intent, UI patterns, design tokens
- If there's a README or any markdown → read it

**Step 2: Summarize what you understood.** Show the user:
> "Here's what I gathered from your [doc/code]. Let me check a few things:"

**Step 3: Fill the gaps by asking.** Adapt to what's missing — skip what's already clear:
1. "What does this product do, in one sentence? Who is it for?"
2. "Walk me through the main user flow — what happens step by step?"
3. "What's the core problem you're solving? Why do existing solutions fail?"
4. "What are the 3-5 key features? Which one is the hero feature?"
5. "Is there anything in the doc that's outdated or no longer the plan?"

Combine doc insights + user answers into a Product Brief. Then hit **CHECKPOINT 1** (same as 1A).

---

## Phase 1C: Idea-First Discovery

**When**: The repo is empty or has no meaningful product code. The product lives in the user's head.

**This is the most important phase to get right.** Don't rush. Your job is to be a curious interviewer who pulls out the user's vision through focused questions.

Start with:
> "I see this repo doesn't have much code yet — that's totally fine. I'll build the landing page from your idea. But I need to understand it well first. Let me ask you some questions."

### Round 1: The Big Picture

Ask these questions (wait for answers before continuing):

> 1. "What are you building? Describe it like you'd tell a friend over coffee."
> 2. "Who needs this? Describe one specific person and their problem."
> 3. "How does it work? Walk me through the user journey step by step."

### Round 2: Sharpening

Based on Round 1 answers, dig deeper. Typical follow-ups:

> - "You said [X] — can you give me a concrete example of that?"
> - "What happens if [edge case]? How does the product handle that?"
> - "What's the user's life like BEFORE vs. AFTER using this?"
> - "You mentioned [feature] — is that the thing people would pay for, or is there something else?"
> - "Are there competitors? What's the one thing you do that they don't?"

### Round 3: Readiness Check

Before moving on, verify you have ALL of these:

| Required | Status |
|----------|--------|
| Product name | ✓/✗ |
| One-liner (clear, specific) | ✓/✗ |
| Target user (specific person, not "everyone") | ✓/✗ |
| Core problem (emotional, not just functional) | ✓/✗ |
| User flow (step by step, at least 3 steps) | ✓/✗ |
| 3+ distinct features | ✓/✗ |
| Differentiator (why this, not alternatives) | ✓/✗ |

**If any are missing or vague**, ask more questions. Do NOT proceed with gaps.

**If the idea is still too fuzzy** after 2-3 rounds (e.g., the user can't articulate who it's for or what it does), say:
> "I want to build something great, but I think the idea needs a bit more definition first. Specifically, I'm unclear on [X]. Can you think about that and come back to me?"

**When the idea is solid**, produce a Product Brief and hit **CHECKPOINT 1**:
> "Here's what I'm hearing. Before I start designing, I want to make sure every word is right:"
>
> [Product Brief]
>
> 1. "Is the one-liner right? If you had to tweet this product, what would you say?"
> 2. "Does the feature list match your priorities? Anything missing?"
> 3. "What emotion should someone feel when they see this landing page — excited, reassured, curious, impressed?"

---

## Phase 2: Style Direction

**Goal**: Establish the visual identity by combining the user's taste with the product's existing design system (if any).

**🔴 ASK THE USER** (required, don't skip):
> 1. "Which 1-3 websites do you admire visually? I'll study their design and apply the same principles."
> 2. "What overall aesthetic do you want? Some options to get you started:"
>    - Editorial / minimal (like Anthropic, Stripe)
>    - Bold / dark (like Vercel, Linear)
>    - Warm / organic (like Notion, Calm)
>    - Glass / futuristic (like Raycast, Arc)
>    - Swiss / clean (like Apple, Figma)
>    - Or describe your own!
> 3. "Any colors or visual elements you already have in mind?"

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
   - Product's existing design tokens (if any, from Phase 1)
   - A coherent color palette (max 3-4 colors)
   - Font pairing (display + body + mono)

**🔴 CHECKPOINT 2**: Present the Style Guide summary. Ask:
> "Here's the style direction I'm going with: [summary]. Before I start building:"
> 1. "Do you prefer sections to be clearly separated (alternating backgrounds, dividers) or flowing (uniform background)?"
> 2. "Should the tone be editorial/serious, playful/casual, or technical/precise?"
> 3. "Anything feel off? Now's the easiest time to change direction."

---

## Phase 3: Content Architecture

**Goal**: Decide what goes on the page and draft the copy.

**Standard landing page modules** (select what fits):

| Module | When to include | Content source |
|--------|----------------|---------------|
| Hero | Always | Product Brief one-liner + CTA |
| Featured/Demo card | If demo video or mockup exists | Dark card with product mockup |
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

**Product mockups must be faithful** (if code exists):
- Read actual component source files
- Match exact colors, fonts, border-radius, spacing
- Show real content (not lorem ipsum)
- Terminal mockups: match the actual CLI interaction flow

**If no code exists** (idea-first path):
- Create conceptual mockups based on the user's described flow
- Use placeholder UI that matches the style guide
- Ask the user: "Since there's no UI built yet, I'll create mockups based on your described flow. Should I show [X] or [Y]?"

**🔴 CHECKPOINT 3**: Present the section plan. Ask:
> "Here's the page structure I'm planning: [list of sections with headlines]."
> 1. "Is there a section here you'd cut? Less is usually more."
> 2. "What's the primary CTA — signup, waitlist, download, or something else?"
> 3. "Do you have a demo video or screenshot I should feature prominently?"
> 4. "Any headline that doesn't sound like you? Tell me your words."

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

**Design principles**:
1. **Typography is the design** — large serif headings establish hierarchy
2. **Restraint** — 3 colors max, no decorative blobs/gradients unless style demands it
3. **Whitespace is premium** — generous section padding (100-160px)
4. **Contrast** — alternate light/dark sections for rhythm
5. **Content > decoration** — every element serves the copy
6. **Section separation** — Users hate when sections blur together. Use:
   - Alternating background colors (light/warm/dark)
   - Subtle horizontal dividers between sections
   - Different card treatments per section (dark cards, light cards, bordered, borderless)

**Product mockups**:
- If code exists: read the actual component files, reproduce exact layout/colors/content
- If idea-only: build conceptual mockups faithful to the described product

**🔴 CHECKPOINT 4**: Open the HTML in the browser. Ask:
> "Take a look. Focus on these:"
> 1. "Do the product mockups match your actual UI (or your vision, if it's not built yet)?"
> 2. "Does the copy sound like you?"
> 3. "Are sections distinct enough, or do they blur together?"
> 4. "Any section feel too long, too short, or unnecessary?"

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

## Quick-start command

When the user says `/landing-page`, begin with:

> "I'll build a landing page for you. Let me take a quick look at your repo first."

Then immediately start **Phase 0** — scan the repo, then **ask the user** which input path they're on (code / doc / idea). Don't assume.

**Never skip the questions.** Even with a full codebase, always ask the user to validate your understanding before building. The user's words and vision matter more than what the code says.

---

## File output

| File | Description |
|------|-------------|
| `landing-page.html` | Self-contained landing page |
| `demo-video/out/demo.mp4` | Product demo video (if Phase 5) |
| `demo-video/src/` | Remotion source (if Phase 5) |
