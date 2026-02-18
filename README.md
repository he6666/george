# Research Essay Co-Writer

A multi-agent pipeline that turns rough idea hunches into well-researched, publication-ready essays. Built to run inside Claude Code.

## What makes this different

Most AI writing tools do a single pass: search, skim, generate. This pipeline uses **9 specialized agents across 3 research phases** to produce essays with genuinely deep research:

- **3-phase research**: landscape mapping → full-text deep reading → targeted gap filling
- **Citation network crawling**: follows references to find works keyword search misses
- **User knowledge integration**: starts from your foundational sources and known thinkers
- **5-tier source evaluation**: every source rated, from peer-reviewed gold to avoid-tier noise
- **Adversarial review**: Red Team agent attacks every claim, grades each section A-F
- **Section-parallel drafting**: dedicated agents per section, then assembly and revision loops

## Quick start

1. Add 2-3 of your essays to `voice/` (optional but recommended)
2. Create `essays/<your-slug>/00-hunch.md` with your rough idea
3. Run the pipeline:

```
"run intake on <slug>"      → structured brief       → review/edit
"run strategy on <slug>"    → essay plan             → review/edit
"run research on <slug>"    → deep research notes    → review, add sources
"run draft on <slug>"       → full draft             → heavy editing pass
"run polish on <slug>"      → publication-ready      → final review
```

Every stage is human-in-the-loop. You review and edit before proceeding.

## Target publications

| Venue | Style Guide | Characteristics |
|-------|------------|-----------------|
| Foreign Affairs | `style-guides/foreign-affairs.md` | Policy-focused, authoritative, 3-5k words, endnotes |
| LessWrong / EA Forum | `style-guides/rationalist.md` | Epistemic rigor, Bayesian framing, 2-6k+ words, inline links |
| Substack | `style-guides/substack.md` | Conversational, narrative-driven, 1.5-4k words, email-first |

## Project structure

```
prompts/           # Agent prompt templates (intake, strategy, research, draft, review, polish)
style-guides/      # Publication-specific conventions
voice/             # Your writing samples for voice matching
essays/            # One folder per essay with full pipeline output
```

See `CLAUDE.md` for the full architecture and `essays/README.md` for per-essay folder structure.
