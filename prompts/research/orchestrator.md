# Research Orchestrator

This prompt defines the orchestration logic for the 3-phase research pipeline. It is executed by the main Claude Code session (not a sub-agent) and coordinates all research agents.

---

## Prerequisites

Before running research, ensure these exist:
- `essays/{{SLUG}}/01-intake.md` — Structured brief from the intake stage
- `essays/{{SLUG}}/02-strategy.md` — Essay plan from the strategy stage
- `essays/{{SLUG}}/00b-seeds.md` — User's foundational sources and context (from seeding step)
- Optionally: `essays/{{SLUG}}/sources/` — User-supplied materials (PDFs, URLs, documents)

---

## Step 0: User Seeding

Before any research agents are dispatched, present the user with the seeding questions. Use AskUserQuestion or direct conversation:

```
I'm about to begin the research phase for your essay. Before I deploy my research agents,
I'd like to build on what you already know. Please share as much or as little as you'd like:

1. FOUNDATIONAL SOURCES: What are the 2-5 most important works (papers, books, articles)
   you already know about on this topic? Titles, authors, or URLs are all helpful.

2. KEY THINKERS: Who are the most important voices in this debate? Who would you cite
   if forced to name 3-5 authorities?

3. KNOWN DEBATES: What are the major fault lines or disagreements in this area?
   What camps exist?

4. YOUR POSITION: Where does your thesis sit relative to existing positions?
   Is it novel, or does it align with an existing camp?

5. ANTI-SOURCES: Are there specific works or thinkers whose arguments you want
   to engage with or rebut?

6. QUALITY FLOOR: What kind of sources count as "good enough" for this essay?
   (Only peer-reviewed? Policy reports fine? Smart blog posts acceptable?)

Don't worry about being exhaustive — even partial answers help the research agents
start from a stronger foundation than cold search.
```

Save the user's responses to `essays/{{SLUG}}/00b-seeds.md`.

---

## Step 1: Prepare Agent Contexts

Read the following files and prepare context packages for Phase 1 agents:
- `essays/{{SLUG}}/01-intake.md`
- `essays/{{SLUG}}/02-strategy.md`
- `essays/{{SLUG}}/00b-seeds.md`
- `prompts/research/source-evaluation.md` (the tier rubric)

Each Phase 1 agent receives: intake + strategy + seeds + the rubric (appended where the template says `{{SOURCE_EVALUATION_RUBRIC}}`).

---

## Step 2: Phase 1 — Landscape Mapping

Dispatch **3 Task agents in parallel**:

1. **Academic Scanner** — Use prompt from `prompts/research/phase1-academic.md`
   - Write output to `essays/{{SLUG}}/.research/phase1-academic.md`

2. **Policy & Data Scanner** — Use prompt from `prompts/research/phase1-policy.md`
   - Write output to `essays/{{SLUG}}/.research/phase1-policy.md`

3. **Discourse Scanner** — Use prompt from `prompts/research/phase1-discourse.md`
   - Replace `{{TARGET_PUBLICATION}}` with the target venue from `01-intake.md`
   - Write output to `essays/{{SLUG}}/.research/phase1-discourse.md`

**Wait for all three to complete.**

---

## Step 3: Phase 1 Synthesis

Read all three Phase 1 outputs. Produce `essays/{{SLUG}}/.research/phase1-landscape.md` containing:

### 3a. Merged Landscape Map
Combine the three agents' findings into a unified view:
- All sources found, deduplicated, with their tier ratings
- Key authors (merged across agents)
- The debate landscape (synthesizing academic, policy, and discourse perspectives)

### 3b. Top 8-12 Sources for Deep Reading
Select using these criteria (in order of priority):
1. **User-seeded sources** that haven't been fully read yet
2. **Survey papers / literature reviews** (highest information density)
3. **Convergence sources** — appeared in multiple agents' results
4. **Evidence wishlist matches** — directly address a specific claim in the strategy
5. **Strongest counterargument sources** — the best case against our thesis
6. **Highest-tier sources** on contested points

For each selected source, note: title, author, URL, why selected, and which essay section it's most relevant to.

### 3c. Evidence Gaps
List claims from the strategy's evidence wishlist that Phase 1 found NO or WEAK support for.

### 3d. Contradictions
List any points where Phase 1 agents found conflicting information or sources that disagree.

---

## Step 4: User Checkpoint (Recommended)

Present the user with:
1. The landscape summary (key findings, major sources, debate map)
2. The list of sources selected for deep reading
3. Any gaps or concerns

Ask: "Would you like to add any sources, remove any from the deep-reading list, or redirect the research focus?"

If the user provides feedback, update the deep-reading list and gap list accordingly.

---

## Step 5: Phase 2 — Deep Dive

### 5a. Dispatch Deep Readers

Divide the 8-12 selected sources into batches of 2-4. Dispatch **2-4 Deep Reader agents in parallel**:

- Use prompt from `prompts/research/phase2-deep-reader.md`
- Each agent receives: intake + strategy + its batch of sources + phase1-landscape.md + the rubric
- Agents write their outputs; collect all into `essays/{{SLUG}}/.research/phase2-deep-reads.md`

**Wait for all Deep Readers to complete.**

### 5b. Dispatch Citation Crawler

Collect all "Citations Worth Following" from the Deep Reader outputs. Deduplicate against the Phase 1 landscape. Dispatch **1 Citation Crawler agent**:

- Use prompt from `prompts/research/phase2-citation-crawler.md`
- Receives: intake + strategy + phase1-landscape.md + deep-reads.md + the deduplicated citation list + the rubric
- Writes output to `essays/{{SLUG}}/.research/phase2-citations.md`

**Wait for completion.**

---

## Step 6: Phase 3 — Gap Filling & Contradiction Resolution

### 6a. Identify Remaining Gaps

Review Phase 1 landscape + Phase 2 deep reads + citation crawl results. For each claim in the essay strategy:
- Is it now well-supported? → No action needed
- Is support weak or missing? → Add to gap list with: what's needed, what was already tried

### 6b. Identify Contradictions

Review all sources for points of disagreement. For each contradiction:
- Source A says X; Source B says Y
- The specific point of conflict
- URLs for both sources

### 6c. Dispatch Agents (in parallel if both are needed)

If there are gaps:
- **Gap Filler** — Use prompt from `prompts/research/phase3-gap-filler.md`
- Receives: intake + strategy + the gap list + the rubric
- Writes to `essays/{{SLUG}}/.research/phase3-gaps.md`

If there are contradictions:
- **Contradiction Resolver** — Use prompt from `prompts/research/phase3-contradiction.md`
- Receives: intake + strategy + the contradiction list + the rubric
- Writes to `essays/{{SLUG}}/.research/phase3-contradictions.md`

**Wait for completion.**

---

## Step 7: Final Research Synthesis

Read ALL research outputs:
- `phase1-landscape.md`
- `phase1-academic.md`, `phase1-policy.md`, `phase1-discourse.md`
- `phase2-deep-reads.md`
- `phase2-citations.md`
- `phase3-gaps.md` (if exists)
- `phase3-contradictions.md` (if exists)
- Any user-supplied materials in `essays/{{SLUG}}/sources/`

Use the synthesis prompt from `prompts/research/synthesis.md` to produce the final `essays/{{SLUG}}/03-research.md`.

---

## Step 8: User Checkpoint

Present the user with:
1. Summary of what was found
2. Argument strength ratings for each key claim
3. Any recommended thesis adjustments
4. Any unfilled gaps

The user reviews and edits `03-research.md` before proceeding to the draft stage.

---

## Error Handling

- **Agent returns empty/garbled output**: Re-dispatch once with the same prompt. If it fails again, note the failure in the synthesis and proceed.
- **WebSearch is unavailable**: Report to user. The research stage cannot proceed without search access.
- **Too many sources selected for Phase 2**: Cap at 12. If the landscape has more than 12 strong candidates, prioritize ruthlessly using the criteria above. The user can always request additional deep reads later.
- **No contradictions found**: Skip Agent 3B. This is normal for some topics.
- **No gaps found**: Skip Agent 3A. This means Phase 1-2 were thorough — a good outcome.
