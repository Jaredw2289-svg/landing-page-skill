# /landing-page — Claude Code Skill

A collaborative Claude Code skill that generates high-fidelity landing pages for any product repo. It reads your codebase, studies reference websites you admire, and builds a polished, self-contained HTML landing page — with an optional Remotion demo video.

**The AI drives the process, but you steer at 4 checkpoints.**

## What it does

| Phase | What happens | You decide |
|-------|-------------|------------|
| 1. Discovery | Reads your codebase, extracts product intent | Confirm the Product Brief |
| 2. Style Direction | You pick reference sites, AI analyzes their design | Confirm the Style Guide |
| 3. Content Architecture | Plans sections, drafts copy | Confirm the Section Plan |
| 4. Build | Generates a single HTML file | Review + iterate |
| 5. Demo Video | Remotion composition → MP4 (optional) | Final review |

## Install

Copy the skill into your Claude Code skills directory:

```bash
# Global (available in all projects)
mkdir -p ~/.claude/skills/landing-page
curl -o ~/.claude/skills/landing-page/SKILL.md \
  https://raw.githubusercontent.com/junyu-boston/landing-page-skill/main/SKILL.md

# Or clone the repo
git clone https://github.com/junyu-boston/landing-page-skill.git
cp landing-page-skill/SKILL.md ~/.claude/skills/landing-page/SKILL.md
```

Or install per-project:

```bash
mkdir -p .claude/skills/landing-page
cp SKILL.md .claude/skills/landing-page/SKILL.md
```

## Usage

In Claude Code, just type:

```
/landing-page
```

The AI will:
1. Read your codebase to understand your product
2. Ask you for 1-3 reference websites to study
3. Build a landing page that combines your product's identity with the reference design
4. Iterate with you until you're happy

## What you get

| File | Description |
|------|-------------|
| `landing-page.html` | Self-contained, responsive landing page (no build step) |
| `demo-video/out/demo.mp4` | Product demo video (if Phase 5) |
| `demo-video/src/` | Remotion source files (if Phase 5) |

## Design philosophy

This skill was built by studying what makes landing pages actually good:

- **Typography is the design** — Large serif headings, restrained color palette (3 colors max)
- **Product fidelity** — Mockups are built from your actual source code, not generic placeholders
- **Reference-driven** — Learns from sites you admire instead of guessing aesthetics
- **Section separation** — Alternating backgrounds, dividers, generous whitespace
- **Responsive** — Mobile-first with `clamp()` for fluid sizing
- **Self-contained** — Single HTML file with Google Fonts CDN, no build tools needed

## Example output

The skill generates pages like this (built for [Hate to Call](https://github.com/shaling-ai/ai_call_m2)):

- Fraunces serif + Inter sans font pairing
- Cream background with coral accent
- Dark featured card with terminal + browser mockups
- Scroll reveal animations via IntersectionObserver
- Embedded demo video modal
- Responsive down to mobile

## Checkpoint questions

The skill asks focused questions at each stage:

**Product Brief** — "What's the ONE thing that makes this different?"
**Style Guide** — "Do you prefer sections clearly separated or flowing?"
**Section Plan** — "Is there a section you'd cut? Less is usually more."
**Review** — "Do the mockups match your actual UI?"

## Requirements

- [Claude Code](https://claude.com/claude-code) CLI
- No other dependencies (the generated page is pure HTML/CSS/JS)
- For demo video (Phase 5): Node.js + npm (Remotion)

## License

MIT
