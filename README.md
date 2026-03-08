# /landing-page — Claude Code Skill

A collaborative Claude Code skill that generates high-fidelity landing pages. Works with mature codebases, product docs, or even just an idea in your head.

**Core principle: Listen first, build second.** The AI asks questions, absorbs your vision, and only starts building when it truly understands your product.

## What it does

| Phase | What happens | You decide |
|-------|-------------|------------|
| 0. Assess | Scans repo, asks what you're working with | Confirm your starting point |
| 1. Discovery | Understands your product (from code, docs, or conversation) | Confirm the Product Brief |
| 2. Style Direction | You pick reference sites, AI analyzes their design | Confirm the Style Guide |
| 3. Content Architecture | Plans sections, drafts copy | Confirm the Section Plan |
| 4. Build | Generates a single HTML file | Review + iterate |
| 5. Demo Video | Remotion composition → MP4 (optional) | Final review |

## Three input paths

The skill adapts to wherever you are:

| Your situation | What happens |
|----------------|-------------|
| **Working product** (code in the repo) | AI reads your codebase, extracts product intent, builds faithful mockups |
| **Product doc / PRD** (written description) | AI reads your doc, asks clarifying questions, fills gaps |
| **Just an idea** (nothing written yet) | AI interviews you in rounds until the idea is solid enough to build |

For the idea-first path, the AI will keep asking questions until it has: a clear one-liner, specific target user, user flow, 3+ features, and a differentiator. It won't start building with gaps.

## Install

```bash
# Global (available in all projects)
mkdir -p ~/.claude/skills/landing-page
curl -o ~/.claude/skills/landing-page/SKILL.md \
  https://raw.githubusercontent.com/Jaredw2289-svg/landing-page-skill/main/SKILL.md
```

Or install per-project:

```bash
mkdir -p .claude/skills/landing-page
curl -o .claude/skills/landing-page/SKILL.md \
  https://raw.githubusercontent.com/Jaredw2289-svg/landing-page-skill/main/SKILL.md
```

## Usage

In Claude Code, type:

```
/landing-page
```

The AI will ask you what you're working with, then guide you through the process.

## What you get

| File | Description |
|------|-------------|
| `landing-page.html` | Self-contained, responsive landing page (no build step) |
| `demo-video/out/demo.mp4` | Product demo video (if Phase 5) |
| `demo-video/src/` | Remotion source files (if Phase 5) |

## Design philosophy

- **Typography is the design** — Large serif headings, restrained color palette (3 colors max)
- **Product fidelity** — Mockups built from your actual source code, not generic placeholders
- **Reference-driven** — Learns from sites you admire instead of guessing aesthetics
- **Section separation** — Alternating backgrounds, dividers, generous whitespace
- **User-driven** — Questions at every checkpoint; your words matter more than AI assumptions

## Requirements

- [Claude Code](https://claude.com/claude-code) CLI
- No other dependencies (the generated page is pure HTML/CSS/JS)
- For demo video (Phase 5): Node.js + npm (Remotion)

## License

MIT
