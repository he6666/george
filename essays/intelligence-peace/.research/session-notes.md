# Research Session Notes: The Intelligence Peace Thesis

> These notes capture research and editorial decisions from a working session.
> They should be read by the strategy and research stages to maintain continuity.

## Current Status

- `00-hunch.md` — complete (the full essay sketch, all 5 parts)
- `01-intake.md` — complete (structured brief with 8 key claims, evidence needs, open questions)
- `02-strategy.md` — **next step**

## Key Editorial Decisions

### Method: Axiomatic, Not Empirical

The essay follows a **Bostrom-style axiomatic method** — like a physicist building a theory. State independently verifiable axioms, then show the conclusion follows as logical necessity.

**Axiom 1:** AI will become the substrate of economic and military power (observable trend, already happening).
**Axiom 2:** Frontier AI requires hardware producible only at a small number of irreplaceable locations (TSMC, ASML — verifiable).
**Axiom 3:** These locations cannot be quickly replicated (5-10 year fabs, 30+ years accumulated knowledge — verifiable).
**Axiom 4:** States that lose access lose their competitiveness (follows from A1).
**Axiom 5:** Destroying supply chain nodes harms everyone including the attacker (follows from A2-A4 + non-substitutability).

**Theorem:** If A1-A5 hold simultaneously, rational incentive is to protect, not attack, the supply chain and the nations hosting it. War against supplier nations becomes collectively irrational. The supply chain becomes a global commons with existential collective defense interest.

**Failure conditions = axiom breakdowns:**
- A1 weakens → AI less central than expected
- A2 weakens → supply chain diversifies, eliminating chokepoints (CHIPS Act trajectory, very slow)
- A5 has exception → actor accepts civilizational-level costs (irrational actor case)
- Transition risk → Copeland's point: theorem holds at equilibrium (everyone integrated) but breaks during transitions (when party expects to lose access)

This is the structure of a physics paper: axioms, derivation, boundary conditions. FA publishes essays with this deductive structure (Mearsheimer's "Back to the Future," Fukuyama's "The End of History").

### The Russia Problem: Reframed

**"What about Russia" is the wrong question.** The essay is a prediction about the **post-AGI world**, not an analysis of present-day geopolitics. Russia is NOT a counterexample to the IPT because the IPT's preconditions don't exist yet:

1. **AGI isn't here** — AI is not yet existentially important to Russia's economy or military
2. **Russia has supply from China** — not fully dependent on the Western AI supply chain
3. **Export controls aren't tight enough** — chokepoint not fully activated; Russia still gets chips via gray markets

**The real question Russia raises:** What happens when an **irrational actor who IS dependent on the supply chain** decides to attack anyway? This is a theoretical edge case, not a historical analogy.

**The answer:**
- In the post-AGI world, losing access to AI infrastructure isn't like losing gas — it's like losing electricity, internet, financial markets, healthcare, and military capability simultaneously
- The analogy isn't "Russia enduring sanctions" — it's "a country voluntarily returning to the pre-industrial era"
- The bar for "irrational enough to attack anyway" rises to near-suicidal levels
- Not absolute, but the strongest economic deterrent in human history

### Copeland's Trade Expectations Theory — MUST ADDRESS HEAD-ON

**Source:** Dale Copeland, *Economic Interdependence and War* (Princeton 2015). Winner of the 2017 ISA Best Book Award.

**Core insight:** What deters war isn't current dependency but *expectations about future access*. If an aggressor expects to be permanently locked out (via export controls, democracy-only policies), this creates *negative expectations about future trade* — which is precisely what triggers preventive war.

**Why this matters:** The essay's own policy recommendations could trigger the dynamic it wants to prevent. Copeland calls this the "trade security spiral."

**The essay's answer:** This is exactly why the supply chain must be *inclusive* rather than *exclusive*. The IPT doesn't work by locking adversaries out — it works by making everyone dependent. The counter-intuitive Bostrom-style conclusion: the path to eternal peace runs *through* interdependence with adversaries, not away from it.

This directly engages Farrell & Newman's weaponized interdependence framework: the US is currently using chokepoints offensively (export controls against China), generating exactly the negative trade expectations Copeland warns about. IPT says: stop doing that. Use chokepoints for *collective defense*, not unilateral coercion.

**Note the tension with the "democracy-only club" recommendation in the hunch.** The essay should acknowledge this tension explicitly and resolve it: perhaps the democracy preference applies to *new* supply chain entrants, while existing integrated parties (China) should be kept integrated rather than expelled.

### Open-Source AI

Open-source AI (DeepSeek, Llama, Mistral) still runs on the same hardware supply chain:
- Software is commoditizing; hardware is not
- DeepSeek showed compute-efficient training, but inference at scale still requires massive GPU clusters
- The chokepoint is in the physical layer (fabs, lithography, HBM), not the model layer
- As AI becomes more central, compute demand grows faster than efficiency gains (Jevons paradox for AI)
- Post-AGI question isn't "can you run a model?" — it's "can you run the AI infrastructure your economy depends on?"

### Scope

Keep the full sketch — all 5 parts from the hunch. This is a Bostrom-style essay that takes premises to logical conclusions, not a deep-dive on one narrow claim. The strategy should organize the full argument into a tight logical sequence within 4,000-5,000 words.

---

## Detailed Research Findings

### Why Russia-Europe Energy Interdependence Failed (5 reasons)

1. **Putin planned a fait accompli** — 72-hour war, done before sanctions could bite. Western intelligence predicted Kyiv falls in 48-72 hours. Russian soldiers carried only 2-3 days of food/fuel. Warehouses of parade uniforms found. Putin calculated "the third party would choose to preserve economic gain over punishing the aggressor" if short enough.
2. **Russia was the supplier, not the consumer** — held offensive leverage (threaten gas cutoff). Gazprom reduced flows in 2021, drove down storage, pushed prices up — *preparing the battlefield economically*.
3. **Energy is fungible and substitutable** — Europe replaced Russian gas with LNG in ~18 months. Germany built first LNG terminal in 9 months. 32% increase in European LNG regasification capacity by 2023. Russian gas dropped from 40%+ to ~14.4% of EU supply.
4. **Bilateral, not multilateral dependency** — only Europe directly depended on Russian gas. Weak collective action incentive for third parties.
5. **Authoritarian echo chamber** — Putin's advisors told him what he wanted to hear about Western resolve and Ukrainian resistance. Deterrence only works if the decision-maker accurately perceives costs.

### Structural Comparison: Energy vs. AI/Semiconductors

| Dimension | Energy (Russia-Europe) | AI/Semiconductors (Post-AGI) |
|---|---|---|
| Substitutability | High. Energy is fungible. Europe switched to LNG in months. | Near-zero. ASML sole EUV maker (100% share). TSMC 90%+ advanced chips. No alternative exists. 5-10 years to replicate. |
| Retaliation speed | Slow. Sanctions require political will, coordination, months to bite. | Automatic. Invading Taiwan destroys fabs instantly. No political decision needed. Fait accompli strategy fails. |
| Dependency breadth | Bilateral (Russia ↔ Europe). Third parties weakly affected. | Global. Every technologically integrated economy depends on same nodes. |
| Who holds leverage | Supplier (Russia) held offensive leverage. | Consumer (potential aggressor) is the dependent party. Aggressor hurts itself. |
| Stockpilability | Strategic petroleum reserves hold years of supply. | Chips: ~1 month, heterogeneous, rapidly obsolete. No Strategic Chip Reserve feasible. |
| Cost magnitude | High but survivable (Europe survived 2022-23 crisis). | Civilizational regression. Loss of AI = loss of everything built on it. |

### Key Academic Sources to Read in Full (for research stage)

**Critical — must deep-read:**
- Dale Copeland, *Economic Interdependence and War* (Princeton 2015) — trade expectations theory
- Henry Farrell & Abraham Newman, "Weaponized Interdependence," *International Security* 44:1 (2019) — chokepoint power framework
- Farrell & Newman, "The Weaponized World Economy," *Foreign Affairs* (Dec 2025) — updated argument
- Chris Miller, *Chip War* (2022) — semiconductor supply chain structure

**Important — should read:**
- "The War in Ukraine: The Deterrent Effect of Weaponized Interdependence," *Nationalities Papers* (Cambridge, 2024)
- "Inside Putin's Hall of Mirrors," *Nationalities Papers* (Cambridge)
- European Politics and Society (2024) — academic assessment of the Silicon Shield argument
- OECD, "Vulnerabilities in the Semiconductor Supply Chain" (2023)
- CFR: "Will China's Reliance on Taiwanese Chips Prevent a War?"
- The Diplomat: "Silicon Shield 2.0: A Taiwan Perspective" (2024)
- Stimson Center: "Taiwan Fears America First Risks Eroding Its Silicon Shield" (2025)

**Context — good to skim:**
- Gartzke & Lupu on why WWI is not a counterexample to commercial peace
- "When Does Liberal Peace Fail? Trade and Nationalism," *Review of International Political Economy* (2022)
- RAND: "Interdependence and Its Discontents" (2024)
- Defense Priorities: "Semiconductors Are Not a Reason to Defend Taiwan"
- ITIF: "How Innovative Is China in Semiconductors?" (2024)

**Related work on intelligence explosion / AI transformation:**
- MacAskill & Moorhouse, "Preparing for the Intelligence Explosion" (Forethought Foundation, 2025) — "grand challenges" framework; argues century of progress could happen in a decade; directly relevant to Axiom 1
- Drago & Laine, "The Intelligence Curse" (2025) — resource curse analogy for AI; labor-replacing AI shifts incentive structures; relevant counterpoint on how AI changes political economy

### ASML Monopoly (key facts for the essay)

- ASML has **100% market share** in EUV lithography — the only technology that can produce chips below 7nm
- Represents 30+ years and $9 billion+ of iterative R&D
- China's EUV prototype (2025) estimated 10-15 years behind, realistic mass production ~2030
- A new advanced fab takes 2-5 years to build, costs $10-165+ billion
- Building in the US costs 4-5x what it costs in Taiwan
- TSMC Arizona announced 2020, won't reach 2nm production until ~2029

### China Self-Sufficiency Status

- SMIC is 5-7 years behind TSMC on advanced chips
- Can produce at 7nm using DUV multi-patterning workarounds but not at scale
- Big Fund 3.0 investing massively but progress is "patchy"
- Full AI autarky is not achievable on any near-term timeline
- But DeepSeek showed that significant AI capability is possible with older chips and clever engineering

### Farrell & Newman's Framework — Double-Edged Sword

**Validates IPT:** Network chokepoints confer real, exercisable power. SWIFT case, Huawei sanctions, ASML export controls all prove states controlling hubs can impose devastating costs.

**Undermines IPT:** Chokepoint power is inherently *offensive*, not just defensive. The US already weaponizes chip supply chains. From China's perspective, this makes the supply chain a *threat*. Their 2025 FA piece argues the US should "turn away from unilateralism, toward detente and arms control."

**Nuclear deterrence analog:** Like nuclear deterrence, supply chain deterrence carries risk of catastrophic miscalculation. Credibility of the threat matters. Brinkmanship can trigger the very conflicts it's meant to prevent.
