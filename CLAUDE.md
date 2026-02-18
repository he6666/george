# Research Essay Co-Writer

This repository is a research essay co-writer pipeline. It turns rough idea hunches into well-researched, publication-ready essays.

## Target Publications

- **Foreign Affairs** — Policy-focused, authoritative tone, structured argumentation
- **LessWrong** — Rigorous reasoning, explicit epistemic status, Bayesian framing welcome
- **EA Forum** — Evidence-driven, cause-area aware, quantitative where possible
- **Standalone Blog** — Flexible format, can blend styles

## Workflow

The pipeline has 5 stages. Each stage lives in `prompts/` as a template and produces output in `essays/<essay-slug>/`.

### Stage 1: Intake (`/intake`)
Drop your hunch (a paragraph or rough idea). The system extracts:
- Core thesis
- Key claims that need evidence
- Domain and relevant literatures
- Target publication
- Open questions to resolve

### Stage 2: Strategy (`/strategy`)
Given the intake brief, produce:
- Essay structure (sections, argument sequence)
- Rhetorical approach tuned to the target venue
- Key counterarguments to address
- Evidence wishlist (what data/papers/examples would make this airtight)

### Stage 3: Research (`/research`)
Find and synthesize:
- Key papers, data, and expert positions
- Historical precedents and case studies
- Counterarguments and their strongest formulations (steelman them)
- Quotable sources and citations

### Stage 4: Draft (`/draft`)
Write the essay:
- Follow the strategy structure
- Integrate research naturally
- Advance the argument with each section
- Engage counterarguments honestly
- Maintain the author's voice

### Stage 5: Polish (`/polish`)
Final pass:
- Match publication style conventions
- Tighten prose, cut filler
- Verify citations and claims
- Check argument flow and coherence
- Suggest a compelling title and subtitle

## Directory Structure

```
essays/              # One folder per essay
  <slug>/
    00-hunch.md      # Raw hunch input
    01-intake.md     # Structured brief
    02-strategy.md   # Essay plan
    03-research.md   # Research notes
    04-draft.md      # Full draft
    05-polished.md   # Publication-ready version
prompts/             # Stage prompt templates
  intake.md
  strategy.md
  research.md
  draft.md
  polish.md
style-guides/        # Publication-specific conventions
  foreign-affairs.md
  lesswrong.md
  ea-forum.md
  blog.md
voice/               # Author voice samples (add your own writing here)
  README.md
```

## Adding Your Voice

Place 2-3 of your best essays in `voice/` as markdown files. The drafting and polish stages will reference these to match your tone, sentence structure, and argumentation style.
