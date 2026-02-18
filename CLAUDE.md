# Research Essay Co-Writer

A multi-agent research and writing pipeline that turns rough idea hunches into well-researched, publication-ready essays. Designed to produce research quality exceeding single-pass AI tools through systematic literature identification, full-text source reading, adversarial review, and iterative refinement.

## Target Publications

- **Foreign Affairs** — Policy-focused, authoritative tone, structured argumentation
- **LessWrong / EA Forum** — Rigorous reasoning, explicit epistemic status, Bayesian framing, quantitative where possible
- **Substack** — Conversational, narrative-driven, personal voice

## Workflow

The pipeline has 5 stages with a multi-agent architecture. Each stage uses prompt templates from `prompts/` and produces output in `essays/<slug>/`.

### Stage 1: Intake
Drop your hunch (a paragraph or rough idea). The system extracts:
- Core thesis (one arguable sentence)
- Key claims that need evidence (with confidence tags)
- Domain and relevant literatures
- Target publication
- Open questions and scope check

### Stage 2: Strategy
Given the intake brief + style guide, produce:
- Section-by-section outline with argumentative purpose
- Argument sequence and logical dependencies
- Rhetorical approach tuned to the target venue
- 3-5 strongest counterarguments (steelmanned)
- Specific evidence wishlist driving the research stage

### Stage 3: Research (Multi-Agent, 3-Phase)

**User Seeding**: Before research begins, the system asks for your foundational sources, key thinkers, known debates, and quality standards.

**Phase 1 — Landscape Mapping** (3 parallel agents):
- Academic Scanner: survey papers, seminal works, key authors, field chronology
- Policy & Data Scanner: government reports, think tanks, datasets, statistics
- Discourse Scanner: recent articles, live debates, current conversation map

**Phase 2 — Deep Dive** (2-4 parallel agents):
- Deep Readers: full-text reading of 8-12 key sources via WebFetch
- Citation Crawler: follows reference chains to find works keyword search missed

**Phase 3 — Gap Filling** (1-2 agents):
- Gap Filler: targeted searches for evidence gaps
- Contradiction Resolver: diagnoses why credible sources disagree

**Synthesis**: All findings organized by essay section with evidence strength ratings (STRONG/MODERATE/WEAK/UNSUPPORTED) and a 5-tier source evaluation rubric.

### Stage 4: Draft (Multi-Agent)
- Section Drafters: one agent per section, writing in parallel
- Assembler: stitches sections, smooths transitions, ensures consistency
- Red Team Reviewer: attacks every claim, grades each section A-F
- Revision Agent: responds to every Red Team critique
- Flow Checker: verifies the argument builds properly end-to-end

Adversarial review loop runs up to 2 iterations.

### Stage 5: Polish
Final editorial pass:
- Line-level prose tightening
- Publication-specific formatting
- Citation verification against research notes
- 3-5 title/subtitle options
- Can produce multiple venue-specific versions from the same draft

## Directory Structure

```
prompts/
  intake.md                       # Stage 1
  strategy.md                     # Stage 2
  research/
    orchestrator.md               # Research phase orchestration logic
    source-evaluation.md          # 5-tier source quality rubric
    phase1-academic.md            # Academic literature scanner
    phase1-policy.md              # Policy & data scanner
    phase1-discourse.md           # Current discourse scanner
    phase2-deep-reader.md         # Full-text source reader
    phase2-citation-crawler.md    # Citation network crawler
    phase3-gap-filler.md          # Targeted evidence gap filler
    phase3-contradiction.md       # Contradiction resolver
    synthesis.md                  # Research synthesis prompt
  draft/
    section-drafter.md            # Per-section essay drafter
    assembler.md                  # Draft assembly and continuity
  review/
    red-team.md                   # Adversarial review
    revision.md                   # Revision in response to Red Team
    flow-check.md                 # Argument flow verification
  polish.md                       # Final editorial pass
style-guides/
  foreign-affairs.md              # Foreign Affairs conventions
  rationalist.md                  # LessWrong + EA Forum (merged)
  substack.md                     # Substack newsletter style
voice/                            # Author voice samples
  README.md
essays/                           # One folder per essay
  README.md
```

### Per-Essay Output

```
essays/<slug>/
  00-hunch.md                     # Raw idea (you write this)
  00b-seeds.md                    # Your foundational sources and context
  01-intake.md                    # Structured brief
  02-strategy.md                  # Essay plan
  03-research.md                  # Synthesized research (by section)
  04-draft.md                     # Revised draft
  05-polished.md                  # Publication-ready
  sources/                        # Your own materials (optional)
  .research/                      # Agent working papers (transparency)
```

## Adding Your Voice

Place 2-3 of your best essays in `voice/` as markdown files. The drafting and polish stages will reference these to match your tone, sentence structure, and argumentation style.

## How It Works in Practice

```
1. Create essays/<slug>/00-hunch.md with your raw idea
2. "run intake on <slug>"     → 01-intake.md      → you review/edit
3. "run strategy on <slug>"   → 02-strategy.md    → you review/edit
4. "run research on <slug>"   → 03-research.md    → you review, add sources
5. "run draft on <slug>"      → 04-draft.md       → you heavily edit
6. "run polish on <slug>"     → 05-polished.md    → publication-ready
```

Each stage is human-in-the-loop. You review and edit before proceeding. The essay is yours — the pipeline provides structure, deep research, and a strong first draft.
