# Implementation Plan: Research Essay Co-Writer

## What We're Building

A prompt-based pipeline that runs inside Claude Code. You drop a hunch, walk through stages — each stage reads the previous stage's output, applies a prompt template, and writes its result to `essays/<essay-slug>/`. The research stage uses a multi-agent architecture for depth and speed. No external dependencies — just well-crafted prompts and style guides.

### Comparison with Other Session's Plan

The other session (branch `claude/research-essay-cowriter-E0sZf`) proposed a full-stack web app: FastAPI backend, vanilla HTML/JS frontend, SQLite database, Tavily API for search. That plan has 7 stages (splitting outline and counterargument into separate stages).

**What we're taking from that plan:**
- The idea of a dedicated counterargument pass (folded into research via a dedicated adversarial agent)
- The checkpoint/review model (already in our plan)
- The style profile structure (tone, structure conventions, citation style, vocabulary register, length)

**What we're not taking:**
- The web app architecture — overkill for a tool that lives in Claude Code. A prompt-based pipeline is lighter, faster to iterate on, and doesn't require running a server or managing API keys for Tavily.
- SQLite persistence — essays live as markdown files in `essays/<slug>/`, which is simpler and version-controllable.
- Tavily for research — Claude Code's built-in WebSearch and WebFetch tools handle research directly. No extra API key needed.

---

## Pipeline: 5 Stages

### Stage 1: Intake (`/intake`)
**Input:** `essays/<slug>/00-hunch.md` (your raw paragraph)
**Output:** `essays/<slug>/01-intake.md`

The intake prompt parses the hunch into:
- **Core thesis** — one sentence
- **Key claims** that need evidence (bulleted list, each tagged with how confident you seem)
- **Domain** and relevant academic/policy literatures
- **Target publication** (Foreign Affairs, LessWrong/EA Forum, Substack)
- **Open questions** — things you haven't decided yet
- **Scope check** — is this too broad for a single essay? Suggest narrowing if needed.

**User checkpoint:** Review the brief. Fix the thesis if it's wrong. Add context. Remove claims you don't actually want to make.

---

### Stage 2: Strategy (`/strategy`)
**Input:** `01-intake.md` + relevant style guide
**Output:** `essays/<slug>/02-strategy.md`

Designs the essay's architecture:
- **Section-by-section outline** — what each section accomplishes argumentatively
- **Argument sequence** — what the reader needs to believe at each stage, building to the conclusion
- **Rhetorical approach** tuned to venue:
  - Foreign Affairs → authority, historical framing, policy implications
  - LessWrong/EA Forum → epistemic rigor, explicit uncertainty, quantitative where possible
  - Substack → personal voice, narrative hooks, conversational depth
- **3-5 strongest counterarguments** and where to engage them
- **Evidence wishlist** — specific types of data, papers, case studies, or expert positions needed for each claim
- **Target length** appropriate for the venue

**User checkpoint:** Reorder sections, adjust emphasis, add counterarguments you know about, refine the evidence wishlist.

---

### Stage 3: Research (`/research`) — Multi-Agent
**Input:** `01-intake.md` + `02-strategy.md` + optional `essays/<slug>/sources/` (user-supplied materials)
**Output:** `essays/<slug>/03-research.md` + raw agent outputs in `essays/<slug>/.research/`

This is the most intensive stage. The orchestrator decomposes the strategy's evidence wishlist into independent research tasks, then **spawns 4 parallel sub-agents** via the Task tool:

#### Sub-Agent 1: Literature Agent
- Searches for academic papers, books, and expert positions relevant to each key claim
- Focuses on the strongest evidence *for* the thesis
- Prioritizes authoritative, citable sources
- Output: `essays/<slug>/.research/literature.md`

#### Sub-Agent 2: Counter-Argument Agent
- **Adversarial role** — its job is to break the thesis
- Searches for critics, skeptics, and alternative frameworks
- Steelmans each counterargument with the best available evidence and citations
- Identifies which counterarguments are genuinely damaging vs. addressable
- Output: `essays/<slug>/.research/counterarguments.md`

#### Sub-Agent 3: Data & Cases Agent
- Searches for quantitative data, statistics, historical precedents, and case studies
- Focuses on concrete evidence rather than theoretical positions
- Looks for natural experiments, before/after comparisons, cross-country data
- Output: `essays/<slug>/.research/data-and-cases.md`

#### Sub-Agent 4: Context Agent
- Maps the current discourse landscape: recent articles, policy debates, public positions
- Identifies what's being said *now* — ensures the essay is timely and engages live debates
- Finds potential hooks and news pegs
- Output: `essays/<slug>/.research/context.md`

#### Orchestrator Synthesis
After all agents complete, the orchestrator:
- Reads all four agent outputs (+ any user-supplied sources in `sources/`)
- Synthesizes into `03-research.md` organized by essay section (matching the strategy)
- Cross-references: did agents find contradictory evidence?
- Ranks evidence by strength and relevance
- Flags **gaps** — claims that couldn't be well-supported, or where evidence cuts against the thesis
- Notes where the counterargument agent found genuinely strong objections that might require thesis adjustment

**Why multi-agent?** A single research pass tends to be shallow and thesis-confirming. The adversarial counter-argument agent forces honest engagement with opposing views. Separating data/cases from literature avoids all-theory-no-evidence. The context agent keeps the essay timely. Running them in parallel saves time.

**User checkpoint:** Review research quality. Add your own sources to `sources/`. Flag weak areas. Decide how to handle gaps.

---

### Stage 4: Draft (`/draft`)
**Input:** `01-intake.md` + `02-strategy.md` + `03-research.md` + style guide + voice samples
**Output:** `essays/<slug>/04-draft.md`

Writes the full essay:
- Follows the strategy's section structure
- **Integrates research naturally** — no "according to a study" every paragraph; weave evidence into the argument flow
- **Advances the argument in every section** — no filler, no throat-clearing
- **Engages counterarguments honestly** — shows understanding of opposing views before responding
- **Matches author's voice** — if voice samples exist, mirrors sentence rhythm, formality level, use of analogy, argumentation style
- Produces a working title and subtitle

**User checkpoint:** This is the heaviest editing pass. Your voice matters most here. Rewrite sections, adjust tone, strengthen weak arguments.

---

### Stage 5: Polish (`/polish`)
**Input:** `04-draft.md` + style guide + voice samples
**Output:** `essays/<slug>/05-polished.md`

Final editorial pass:
- **Tighten prose** — cut filler words, weak verbs, hedging that doesn't serve epistemic honesty
- **Check argument flow** — does each paragraph earn the next? Are transitions smooth?
- **Verify citations** — are claims properly attributed? Any unsupported?
- **Match publication conventions** — word count, section formatting, citation style, tone
- **Suggest 3-5 title/subtitle options** ranked by strength
- **Revision summary** — what changed and why

For multi-venue essays: the polish stage can be run multiple times with different style guides to produce venue-specific versions (e.g., `05-polished-fa.md` and `05-polished-substack.md`).

**User checkpoint:** Final review. Publication-ready.

---

## Style Guides

### `style-guides/foreign-affairs.md`
- **Length:** 3,000–5,000 words
- **Tone:** Authoritative, declarative — avoid hedging unless necessary
- **Structure:** No numbered sections; subheadings optional. Open with the stakes, close with policy implications.
- **Framing:** Historical context is expected. Situate arguments in precedent.
- **Audience:** Educated generalists — minimal jargon, no unexplained acronyms
- **Citations:** Endnotes, not inline academic citations
- **Vocabulary:** Diplomatic, institutional register
- **What FA editors want:** Concrete policy implications, not just analysis. "So what?" must be answered.

### `style-guides/rationalist.md` (LessWrong + EA Forum — merged)
LessWrong and EA Forum share a common intellectual culture and tone. One style guide covers both, with minor venue-specific notes.

- **Tone:** Formal but not stiff — intellectual conversation among peers
- **Epistemic standards:** Explicit about uncertainty. Use probability language where appropriate. Bayesian framing welcome.
- **Structure:** Numbered sections encouraged. TL;DR or summary at top. Epistemic status header expected.
- **Evidence:** Quantitative where possible. Cost-effectiveness framing when relevant (especially EA Forum).
- **Counterarguments:** Must be steelmanned. Readers will notice if you strawman.
- **Citations:** Inline links preferred over endnotes
- **Length:** 2,000–6,000+ words — depth valued over brevity
- **EA-specific notes:** Cause-area awareness, explicit about assumptions and sensitivity, connect to EA priorities where relevant
- **LW-specific notes:** Engage with existing sequences/concepts where relevant, original thinking valued over summaries

### `style-guides/substack.md`
Modeled on the best Substack newsletters — personal, substantive, narrative-driven.

- **Tone:** Conversational but substantive. First person freely. The author's personality is the product.
- **Structure:** Flexible. Can open with anecdote, question, or provocation. Subheadings help scanability.
- **Hooks:** Strong opening line is critical — Substack readers decide in 2 sentences whether to keep reading.
- **Length:** 1,500–4,000 words typical. Can go longer if the writing sustains it.
- **Voice:** This is where personal voice comes through strongest. Asides, humor, speculation, and tangents are fine if they serve the piece.
- **Evidence:** Links inline. Casual citation style — "as [Name] argues in [linked piece]" rather than formal references.
- **Narrative:** Story-driven where possible. Abstract arguments land better when grounded in a specific example or scene.
- **Formatting:** Short paragraphs. White space. Bold for emphasis. Pull-quotes or callouts for key points.
- **Email-first:** Remember Substack essays arrive in inboxes. The opening must work as an email preview.

---

## Voice System

### `voice/README.md`
Place 2-3 of your best essays here as markdown files. The drafting and polish stages reference these to match:
- Sentence length and rhythm
- Level of formality
- Use of analogy and metaphor
- How you handle uncertainty and hedging
- Argumentation style (build incrementally? lead with the thesis? Socratic?)
- Characteristic phrases, sentence constructions, or tics

---

## Directory Structure

```
prompts/
  intake.md              # Stage 1 template
  strategy.md            # Stage 2 template
  research.md            # Stage 3 template (multi-agent orchestrator)
  draft.md               # Stage 4 template
  polish.md              # Stage 5 template
style-guides/
  foreign-affairs.md     # Foreign Affairs conventions
  rationalist.md         # LessWrong + EA Forum (merged)
  substack.md            # Substack newsletter style
voice/
  README.md              # Instructions for adding voice samples
essays/
  README.md              # How the essay directory works
CLAUDE.md                # Updated project instructions
```

**Total: 11 new files** to create (+ CLAUDE.md update).

---

## How It Works in Practice

```
1. Create essays/<slug>/00-hunch.md with your raw idea
2. "run intake on <slug>"     → 01-intake.md      → you review/edit
3. "run strategy on <slug>"   → 02-strategy.md    → you review/edit
4. "run research on <slug>"   → 03-research.md    → you review, add sources
5. "run draft on <slug>"      → 04-draft.md       → you heavily edit
6. "run polish on <slug>"     → 05-polished.md    → publication-ready
```

Each stage is human-in-the-loop. You review and edit before proceeding. The essay is yours — the pipeline provides structure, research, and a strong first draft.

---

## Open Design Decisions

1. **Voice calibration depth:** Use example essays as-is, or also generate an explicit "voice profile" doc analyzing your patterns? (Recommendation: start with examples, add profile extraction later if matching is weak.)

2. **User-supplied sources:** Support a `essays/<slug>/sources/` folder for papers/links you've already found? (Recommendation: yes — the research agents should incorporate these alongside their web search results.)

3. **Iterative refinement:** After polish, you may want to loop back (e.g., "counterargument section is weak, redo research on X"). Handle ad hoc or build explicit re-run support? (Recommendation: ad hoc for now — just tell Claude to re-run a specific stage.)

4. **Multi-venue branching:** Run polish with different style guides to produce `05-polished-fa.md` and `05-polished-substack.md` from the same draft? (Recommendation: yes, already described above.)
