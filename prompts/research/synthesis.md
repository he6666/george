# Research Synthesis Prompt

You are synthesizing the results of a 3-phase multi-agent research process into a single, well-organized research document. This document will be the primary input for the essay's drafting stage — everything the writer needs must be here, clearly organized and easy to navigate.

---

## Inputs

You have access to all of the following (read each before synthesizing):

- `01-intake.md` — the essay's structured brief (thesis, claims, domain, target)
- `02-strategy.md` — the essay plan (sections, argument sequence, evidence wishlist)
- `00b-seeds.md` — the user's foundational sources and context
- `.research/phase1-landscape.md` — Phase 1 synthesis (landscape map)
- `.research/phase1-academic.md` — Academic scanner raw output
- `.research/phase1-policy.md` — Policy/data scanner raw output
- `.research/phase1-discourse.md` — Discourse scanner raw output
- `.research/phase2-deep-reads.md` — Deep Reader notes
- `.research/phase2-citations.md` — Citation Crawler findings
- `.research/phase3-gaps.md` — Gap-filling results (if exists)
- `.research/phase3-contradictions.md` — Contradiction resolution (if exists)
- Any user-supplied materials in `sources/`

---

## Output Structure

Produce `03-research.md` with the following sections:

### 1. Research Summary

A 2-3 paragraph overview:
- What the research found overall
- The strongest evidence for and against the thesis
- The most important sources discovered
- Any thesis adjustments recommended based on the evidence

### 2. Evidence by Essay Section

For each section in `02-strategy.md`, provide:

```markdown
## Section: "[Section Name from Strategy]"

### Supporting Evidence
For each piece of evidence (strongest first):
- **[Claim being supported]**
  - [Tier X] [Source citation]
  - Key finding: [specific evidence]
  - Quote: "[relevant quotable passage]" (if available)
  - Strength: [how strong this evidence is and any caveats]

### Counterarguments to Address
- **[Counterargument]**
  - Best source: [Tier X] [Citation]
  - Steelman version: [the strongest formulation of this objection]
  - Suggested response: [how the essay might address this]
  - Strength of counter: [how damaging is this if unaddressed?]

### Data & Concrete Examples
- [Statistic or case study, with source and methodology note]
- ...

### Context & Current Discourse
- [Recent pieces that this section should engage with]
- [Timely hooks relevant to this section]

### Section-Level Assessment
Evidence strength: [STRONG / MODERATE / WEAK]
Key risk: [what could go wrong argumentatively in this section]
```

### 3. Master Source List

All sources discovered across all phases, organized by tier:

```markdown
## Tier 1 — Gold Standard
1. [Full citation with URL]
   → Used in: Sections [X, Y]
   → Key contribution: [one sentence]

## Tier 2 — Strong
...

## Tier 3 — Useful
...

## Tier 4 — Supporting
...
```

### 4. Argument Strength Assessment

For each of the essay's key claims (from `01-intake.md` and `02-strategy.md`):

```markdown
| Claim | Rating | Best Evidence | Strongest Counter | Notes |
|-------|--------|---------------|-------------------|-------|
| [Claim 1] | STRONG | [Source] | [Source] | [brief note] |
| [Claim 2] | MODERATE | [Source] | [Source] | [brief note] |
| [Claim 3] | WEAK | [Source or "limited"] | [Source] | [brief note] |
```

Ratings:
- **STRONG**: Multiple Tier 1-2 sources support. Counterarguments are addressable.
- **MODERATE**: Supported but with caveats, limited sources, or one strong counter.
- **WEAK**: Limited support, strong counterarguments, or relies on Tier 3-4 sources.
- **UNSUPPORTED**: Could not find adequate evidence. Recommend dropping or heavily qualifying.

### 5. Thesis Health Check

Based on everything found:
- **Original thesis**: [from intake]
- **Thesis still fully supported?** [Yes / Needs adjustment]
- **Recommended adjustments** (if any): [specific suggestions for how to qualify, narrow, or redirect]
- **Biggest risk to the argument**: [the single strongest challenge found]
- **Biggest opportunity**: [the most powerful evidence or angle discovered]

### 6. Unresolved Issues

- **Evidence gaps**: Claims that still lack strong support after all 3 phases
- **Unresolved contradictions**: Disagreements between sources that couldn't be cleanly resolved
- **Access failures**: Important sources that couldn't be fully read (paywalled, etc.)
- **Questions for the author**: Points where the author's judgment is needed (e.g., "Your thesis could go in direction A or B based on the evidence — which do you prefer?")

### 7. Discourse Positioning

From the current discourse analysis:
- **What's already been said**: The essay must add to, not repeat, existing arguments
- **Our unique contribution**: What this essay brings that hasn't been said
- **Who to engage with**: Specific recent pieces the essay should cite or respond to
- **Timely hooks**: Events or developments that make the essay urgent now

---

## Synthesis Guidelines

1. **Organize for the writer, not the researcher.** The drafter will use this document section-by-section. Evidence should be grouped by where it'll be used, not by where it was found.

2. **Be honest about evidence quality.** If a claim is WEAK, say so clearly. It's better for the writer to know now than to build a section on thin evidence.

3. **Preserve direct quotes.** The drafter needs quotable material. Include the best quotes from Deep Reader notes, with enough context to use them properly.

4. **Rank evidence.** Within each section, put the strongest evidence first. The drafter shouldn't have to guess what's most important.

5. **Flag uncertainties explicitly.** Where the evidence is ambiguous, say so. Where experts disagree, note the disagreement. Don't smooth over genuine complexity.

6. **Cross-reference.** If evidence for Section 3 also strengthens Section 1's argument, note this. If a counterargument in Section 2 is addressed by evidence in Section 4, create a cross-reference.

7. **Include enough citation detail for the drafter.** Author, title, year, and URL minimum. The drafter shouldn't have to re-search to cite a source properly.
