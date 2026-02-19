# Session Record: Intelligence Peace Thesis
## Web Claude Code Session — 2026-02-18

> **Purpose:** This file captures the full context of a working session so a local Claude Code agent can continue seamlessly. Read this file, plus `session-notes.md` in this same directory, before doing any work on this essay.

---

## Session Summary

The user (Liu He, Research Fellow, Hoover Institution) built the Research Essay Co-Writer pipeline from scratch and began work on the first essay: "The Intelligence Peace Thesis." The session covered:

1. **Pipeline scaffolding** — Created the entire multi-agent research/writing pipeline: 22 prompt templates, 3 style guides, CLAUDE.md spec, directory structure
2. **Essay intake** — Processed the user's raw essay sketch (00-hunch.md) through the intake stage, producing a structured brief (01-intake.md)
3. **Deep editorial discussion** — Extensive back-and-forth on how to handle the Russia counterargument, academic frameworks (Copeland, Farrell & Newman), the axiomatic method, scope, and open-source AI
4. **Research planning** — Identified key sources for deep reading and structured the research approach

---

## Current Status

| File | Status |
|---|---|
| `00-hunch.md` | Complete — full 5-part essay sketch |
| `01-intake.md` | Complete — structured brief with 8 key claims, evidence needs, 6 open questions |
| `00b-seeds.md` | Not yet created — user seeding (foundational sources) should happen before research |
| `02-strategy.md` | **NEXT STEP** — run strategy on intelligence-peace |
| `03-research.md` | Not started |
| `04-draft.md` | Not started |
| `05-polished.md` | Not started |

### How to Continue

```
1. User reviews 01-intake.md (may already be done)
2. "run strategy on intelligence-peace"  → produces 02-strategy.md
3. User reviews and edits strategy
4. System asks user seeding questions → produces 00b-seeds.md
5. "run research on intelligence-peace" → produces 03-research.md
6. Continue through draft and polish stages
```

---

## Key Editorial Decisions Made in This Session

### 1. Method: Axiomatic, Bostrom-Style

The essay follows a **Bostrom-style axiomatic method** — state independently verifiable axioms, then show the conclusion follows as logical necessity. Like a physics paper: axioms, derivation, boundary conditions.

**The 5 Axioms:**
- **A1:** AI will become the substrate of economic and military power (observable trend)
- **A2:** Frontier AI requires hardware producible only at a small number of irreplaceable locations (TSMC, ASML — verifiable)
- **A3:** These locations cannot be quickly replicated (5-10 year fabs, 30+ years accumulated knowledge)
- **A4:** States that lose access lose their competitiveness (follows from A1)
- **A5:** Destroying supply chain nodes harms everyone including the attacker (follows from A2-A4 + non-substitutability)

**Theorem:** If A1-A5 hold simultaneously, rational incentive is to protect, not attack, the supply chain and the nations hosting it.

**Failure conditions = axiom breakdowns** — this is how the essay handles objections honestly.

### 2. The Russia Problem: Reframed

The session spent significant time on "What about Russia?" — the most immediate objection to IPT. The agreed framing:

**"Russia is NOT a counterexample to the IPT because the IPT's preconditions don't exist yet."**

Three reasons:
1. AGI isn't here — AI is not yet existentially important to Russia's economy
2. Russia has alternative supply from China — not fully dependent on Western AI chain
3. Export controls aren't tight enough — chokepoint not fully activated

The real question Russia raises: what happens when an irrational actor who IS dependent attacks anyway? Answer: in the post-AGI world, losing AI access isn't like losing gas — it's like losing electricity, internet, financial markets, healthcare, and military capability simultaneously. The bar for "irrational enough to attack anyway" is near-suicidal.

Additionally, the session produced a detailed **5-reason analysis of why Russia-Europe energy interdependence failed** and a **5-dimension structural comparison** showing why AI/semiconductor dependency is qualitatively different. Both are in `session-notes.md`.

### 3. Copeland's Trade Expectations Theory — MUST Address Head-On

**Source:** Dale Copeland, *Economic Interdependence and War* (Princeton 2015). ISA Best Book Award.

**Core insight:** What deters war isn't current dependency but *expectations about future access*. If an aggressor expects to be permanently locked out (via export controls, democracy-only policies), this creates negative expectations → triggers preventive war.

**Why it matters:** The essay's own policy recommendations could trigger the dynamic it wants to prevent.

**The essay's answer:** The supply chain must be *inclusive* rather than *exclusive*. IPT doesn't work by locking adversaries out — it works by making everyone dependent. Counter-intuitive Bostrom-style conclusion: the path to peace runs *through* interdependence with adversaries, not away from it.

**Important tension:** This conflicts with the "democracy-only club" recommendation in the hunch. The essay should acknowledge this explicitly. Perhaps: democracy preference applies to *new* supply chain entrants, while existing integrated parties (China) should remain integrated rather than expelled.

### 4. Farrell & Newman — Double-Edged Sword

**Validates IPT:** Network chokepoints confer real, exercisable power (SWIFT, Huawei sanctions, ASML export controls all prove it).

**Undermines IPT:** Chokepoint power is inherently *offensive*, not just defensive. The US already weaponizes chip supply chains. From China's perspective, the supply chain is a *threat*, not a peace mechanism.

The essay must engage both sides: F&N's framework validates IPT's structural logic but shows the US is currently using it wrong (offensive coercion instead of collective defense).

### 5. Open-Source AI

User raised this — the essay must address it. Resolution:
- Software is commoditizing; hardware is not
- DeepSeek showed compute-efficient training, but inference at scale still requires massive GPU clusters
- The chokepoint is in the physical layer (fabs, lithography, HBM), not the model layer
- Jevons paradox for AI: as AI becomes more central, compute demand grows faster than efficiency gains
- Post-AGI question isn't "can you run a model?" — it's "can you run the AI infrastructure your economy depends on?"

### 6. Scope Decision

User explicitly decided: **keep the full sketch — all 5 parts**. This is a Bostrom-style essay that takes premises to logical conclusions. FA publishes essays with this deductive scope (Mearsheimer's "Back to the Future," Fukuyama's "The End of History"). Strategy stage should organize the full argument into a tight logical sequence within **4,000-5,000 words**, not cut the scope.

The intake brief recommended narrowing to 3 core elements + 1 marquee policy recommendation. The user overruled this — keep everything but make it tight.

---

## Research Sources Identified

### Must Deep-Read (Critical)
- Dale Copeland, *Economic Interdependence and War* (Princeton 2015) — trade expectations theory
- Henry Farrell & Abraham Newman, "Weaponized Interdependence," *International Security* 44:1 (2019)
- Farrell & Newman, "The Weaponized World Economy," *Foreign Affairs* (Dec 2025)
- Chris Miller, *Chip War* (2022) — semiconductor supply chain structure

### Should Read (Important)
- "The War in Ukraine: The Deterrent Effect of Weaponized Interdependence," *Nationalities Papers* (Cambridge, 2024)
- "Inside Putin's Hall of Mirrors," *Nationalities Papers* (Cambridge)
- European Politics and Society (2024) — academic assessment of the Silicon Shield argument
- OECD, "Vulnerabilities in the Semiconductor Supply Chain" (2023)
- CFR: "Will China's Reliance on Taiwanese Chips Prevent a War?"
- The Diplomat: "Silicon Shield 2.0: A Taiwan Perspective" (2024)
- Stimson Center: "Taiwan Fears America First Risks Eroding Its Silicon Shield" (2025)

### Good to Skim (Context)
- Gartzke & Lupu on why WWI is not a counterexample to commercial peace
- "When Does Liberal Peace Fail? Trade and Nationalism," *Review of International Political Economy* (2022)
- RAND: "Interdependence and Its Discontents" (2024)
- Defense Priorities: "Semiconductors Are Not a Reason to Defend Taiwan"
- ITIF: "How Innovative Is China in Semiconductors?" (2024)

### Related AI Transformation Works
- MacAskill & Moorhouse, "Preparing for the Intelligence Explosion" (Forethought Foundation, 2025) — "grand challenges" framework; relevant to Axiom 1
- Drago & Laine, "The Intelligence Curse" (2025) — resource curse analogy for AI; relevant counterpoint

---

## Key Facts Gathered

### ASML Monopoly
- 100% market share in EUV lithography — only technology for chips below 7nm
- 30+ years and $9B+ of iterative R&D
- China's EUV prototype estimated 10-15 years behind
- New advanced fab: 2-5 years, $10-165B+ cost
- US fabs cost 4-5x Taiwan's cost
- TSMC Arizona: announced 2020, 2nm production ~2029

### China Self-Sufficiency
- SMIC is 5-7 years behind TSMC on advanced chips
- Can produce 7nm using DUV workarounds but not at scale
- Big Fund 3.0 investing heavily but progress "patchy"
- Full AI autarky not achievable near-term
- DeepSeek showed significant capability with older chips + clever engineering

### Russia-Europe Energy (comparison data)
- Europe replaced Russian gas with LNG in ~18 months
- Germany built first LNG terminal in 9 months
- Russian gas dropped from 40%+ to ~14.4% of EU supply
- 32% increase in European LNG regasification capacity by 2023

---

## Essay Metadata

- **Author:** Liu He, Research Fellow, Hoover Institution, Stanford University
- **Target publication:** Foreign Affairs
- **Working title:** "The Intelligence Peace Thesis: Locking In Peace In A Post-AGI World"
- **Target length:** 4,000-5,000 words
- **Tone:** Authoritative, deductive, Bostrom-style axiomatic reasoning

---

## Pipeline Information

The repo contains a multi-agent research/writing pipeline. See `CLAUDE.md` for full spec. Key commands:
- `"run intake on <slug>"` — Stage 1
- `"run strategy on <slug>"` — Stage 2
- `"run research on <slug>"` — Stage 3 (multi-agent, 3-phase)
- `"run draft on <slug>"` — Stage 4 (multi-agent with adversarial review)
- `"run polish on <slug>"` — Stage 5

Each stage uses prompt templates from `prompts/` and is human-in-the-loop (user reviews before proceeding).

---

## Open Questions for the User (from Intake)

These were flagged in `01-intake.md` and not yet resolved. The strategy stage should work with these, and the user should weigh in:

1. How to differentiate IPT from existing liberal institutionalist arguments
2. Whether the "playbook" (especially Ukraine application) is realistic enough to include
3. How to resolve the integrate-everyone vs. democracies-only tension
4. What would falsify the thesis (empirical grip for FA editors)
5. How to treat AGI timeline uncertainty (the thesis depends on AGI arriving)
6. Whether to address AI weapons / existential risk objections in depth or briefly

---

## Notes on the Pipeline Itself

- The pipeline was built from scratch in this session
- All 22 prompt template files exist in `prompts/`
- 3 style guides exist in `style-guides/` (foreign-affairs.md, rationalist.md, substack.md)
- Voice samples directory exists but is empty (user hasn't added their writing samples yet)
- The pipeline is designed for Claude Code specifically — uses Task tool with parallel subagents for research and drafting
