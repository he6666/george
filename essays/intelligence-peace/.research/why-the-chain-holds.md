# Research Brief: Why the AI Supply Chain Will Remain Globally Integrated

## For: "The Intelligence Peace Thesis" — Chapter 2: Why the Chain Holds
## Date: March 2026 (verified with live web research)

**Citation reliability tiers:**
- **Tier 1**: Peer-reviewed academic work, official government statistics
- **Tier 2**: Major think tanks, industry reports, government-commissioned reports
- **Tier 3**: Quality journalism (NYT, FT, Reuters, Bloomberg, Nikkei Asia, etc.)

**Chapter conclusion the reader should leave with:** Global integration is not a fragile accident — it is the natural, self-reinforcing steady state of the AI supply chain. This is just how the supply chain will look in the long term.

---

## 1. The Phenomenon: How Globally Integrated the AI Supply Chain Actually Is

*Begin with observation. Let the reader see the staggering level of globalization before explaining why.*

### 1.1 ASML's EUV Machine: A Monument to Interdependence

ASML's EUV lithography machine is perhaps the most complex device ever manufactured — and no single country can build one:

- Weighs ~150,000 kg (150 metric tons; the newer High-NA EUV weighs 165 tons). Contains over 100,000 individual components and 2 km of cable. Requires 40 freight containers, 20 trucks, and three Boeing 747s to ship. Price: $370+ million per unit (High-NA).
- **Components from ~5,000 suppliers across multiple countries:**
  - **Germany (Carl Zeiss SMT)**: Mirror optics system. Mirrors polished to sub-atomic precision — if scaled to the size of Germany, the largest imperfection would be a fraction of a millimeter. Zeiss is the sole supplier; no alternative exists.
  - **Germany (Trumpf)**: CO2 laser system powering the EUV light source.
  - **United States (Cymer, ASML subsidiary since 2013)**: Light source system — tin droplets struck by laser to produce EUV photons.
  - **Japan**: Precision stages, measurement systems, various components.
  - **Netherlands (ASML)**: System integration, final assembly, and the intellectual architecture.
- **Only one company on Earth** can produce these machines. Even ASML itself is capacity-constrained — it sold 300 new tools in 2025 (€32.7 billion revenue, €9.6 billion net income). Q4 2025 EUV bookings alone: €7.4 billion.
- **The EUV program took ~20+ years** of development and billions in R&D across ASML and its partners. Replication is not a matter of money — it is a matter of distributed, accumulated, tacit knowledge across multiple countries and thousands of suppliers.

*Sources: ASML Q4 2025 results; ASML corporate disclosures; Zeiss press releases; Miller, "Chip War" (2022).* **[Tier 2/3]**

### 1.2 The Full Supply Chain Map: Every Node Depends on Every Other

No nation controls more than one or two layers. Each layer has extreme concentration:

| Layer | Dominant Nation(s) | Key Companies | Market Share |
|-------|-------------------|---------------|--------------|
| Chip design (fabless) | United States | Nvidia, Qualcomm, AMD, Apple, Broadcom | ~47% of global semiconductor revenue |
| EDA software | United States | Synopsys, Cadence, Mentor (Siemens) | ~74% combined |
| Leading-edge fabrication | Taiwan | TSMC | ~90% of sub-7nm chips; ~92% of leading-edge capacity |
| Memory (DRAM/NAND) | South Korea | Samsung, SK Hynix | ~70%+ of DRAM |
| EUV lithography equipment | Netherlands | ASML | 100% monopoly |
| Precision optics | Germany | Zeiss | 100% (sole EUV optics supplier) |
| Laser systems | Germany | Trumpf | Sole EUV laser supplier |
| Materials (wafers, photoresists) | Japan | Shin-Etsu, SUMCO, JSR, TOK | ~56% of semiconductor materials globally |
| Other equipment | US, Japan | Applied Materials, Lam, KLA, Tokyo Electron | 50-90%+ per segment |
| IP cores / ISA | UK (SoftBank) | ARM | Dominant in mobile and increasingly server |

*Sources: SIA factbook; TrendForce; SEMI equipment data; company disclosures.* **[Tier 2]**

### 1.3 The 70-Border Chip

According to Accenture, the inputs to a typical integrated circuit cross more than **70 international borders** before a final product reaches consumers. Manufacturing involves 1,000+ processing steps across a dozen or more countries, takes 4-6 months, and involves 500+ discrete production stages.

*Source: Accenture analysis; CSIS, "Mapping the Semiconductor Supply Chain"; SEMI/DHL resilience study.* **[Tier 2]**

### 1.4 TSMC: The World's Most Important Manufacturer Depends on Everyone Else

TSMC cannot function without foreign inputs:
- **Equipment**: >80% from non-Taiwanese sources (ASML, Applied Materials, Lam Research, KLA, Tokyo Electron)
- **Materials**: Ultra-high-purity silicon wafers (Shin-Etsu, SUMCO — Japan, ~55-60% global share), photoresists (JSR, TOK — Japan), specialty gases (US, European suppliers), CMP slurries (Cabot Microelectronics — US)
- **Design tools**: TSMC's process design kits built for Synopsys/Cadence (US) EDA software
- **IP cores**: ARM (UK/Japan) provides the instruction set architecture for most chips fabricated at TSMC

*Sources: SEMI equipment/materials data; TSMC supplier disclosures; SIA reports.* **[Tier 2]**

### 1.5 AI Research Talent: Inherently Global

- Georgetown CSET: ~65% of top-tier AI researchers working in the US are foreign-born (primarily China, India, Europe). Among AI PhD students: ~70%+.
- MacroPolo/Paulson Institute: of NeurIPS researchers, ~29% did undergraduate studies in China, ~20% US, ~18% Europe — but ~59% *currently work* in the US.
- The Transformer paper ("Attention Is All You Need," 2017) had 8 authors from multiple national backgrounds at Google Brain. DeepMind's founder is British-Greek. Ilya Sutskever was born in Russia, raised in Israel, trained in Canada.
- China produces ~77,000 STEM PhDs/year vs. ~40,000 in the US, but many top talents go abroad.

*Sources: Zwetsloot et al., CSET (2019); MacroPolo Global AI Talent Tracker; NSF S&E Indicators.* **[Tier 1/2]**

### 1.6 The Key Observation

**The AI supply chain has numerous points of failure — and this is a feature, not a bug.** Every node depends on every other node. No single country can produce the full stack. This mutual dependency is not a vulnerability to be eliminated through onshoring; it is, as this chapter will argue, the structural foundation of a potential peace architecture. To see why, we need to understand *why* the supply chain looks this way — and why it will continue to.

---

## 2. Why Integration Exists: The Economics of Specialization

### 2.1 Comparative Advantage Applied to Semiconductors

Different countries dominate different segments because of genuine, deep, path-dependent advantages:

- **Ricardian comparative advantage**: Taiwan's fabrication dominance arose from deliberate industrial policy (Morris Chang founding TSMC in 1987 with government backing) combined with a large engineering workforce. Morris Chang himself embodies the global ecosystem — born in China, educated at MIT and Stanford, worked at Texas Instruments for 25 years, then returned to Taiwan.
- **Increasing returns to scale and learning-by-doing**: Semiconductor fabrication exhibits extreme learning curves. Each node requires cumulative knowledge from all previous nodes. TSMC's advantage is not merely capital — it is the accumulated tacit knowledge of hundreds of thousands of engineers over 35+ years. This is what Arthur (1994) calls *dynamic increasing returns*.
- **Agglomeration effects**: Hsinchu Science Park (Taiwan), Silicon Valley (design), Eindhoven (ASML ecosystem) — clustering of firms, talent pools, and suppliers creates self-reinforcing advantages that are extremely difficult to replicate.

*Sources: Arthur, "Increasing Returns and Path Dependence" (1994); Krugman, "Increasing Returns and Economic Geography," JPE (1991); Saxenian, "Regional Advantage" (1994).* **[Tier 1]**

### 2.2 Gains from Trade at the Frontier

- **New trade theory** (Helpman & Krugman, 1985): Countries trade in differentiated products within the same industry — US designs chips, Taiwan manufactures them, Japan supplies materials — generating welfare gains beyond classical predictions.
- **Technology diffusion** (Grossman & Helpman, 1991): International trade facilitates knowledge spillovers that increase total factor productivity across partners.
- **Quantitative cost of fragmentation**: BCG/SIA (2021, updated 2024) estimated that building fully self-sufficient supply chains would require **$1 trillion+ in incremental investment** and **increase chip prices by 35-65%**. The 2024 follow-up report (*"Emerging Resilience in the Semiconductor Supply Chain"*) updated these figures with post-CHIPS Act data.

*Sources: Helpman & Krugman (1985); Grossman & Helpman (1991); BCG/SIA (2021, 2024).* **[Tier 1/2]**

### 2.3 Winner-Take-Most Dynamics at the Leading Edge

- **Capital intensity**: A single leading-edge fab costs $15-20 billion. TSMC's total US investment now stands at $165 billion across six planned fabs.
- **Yield as moat**: The critical variable is yield — % of functional chips per wafer. TSMC's yields consistently outperform competitors. Higher yields → lower costs → more R&D investment → higher yields. This is Sutton's (1991) *endogenous sunk costs* creating natural oligopoly.
- **EDA duopoly**: Synopsys and Cadence (~74% combined) dominate because of massive R&D costs and compatibility lock-in.
- **Equipment concentration**: ASML's 100% EUV monopoly. Applied Materials, Lam, KLA, Tokyo Electron hold 50-90%+ shares in their segments.

*Sources: Sutton, "Sunk Costs and Market Structure" (1991); TSMC announcements; VLSI Research; SIA.* **[Tier 1/2]**

### 2.4 The Cost of Onshoring — Case Studies

**TSMC Arizona:**
- Original plan (2020): $12 billion, one fab, 5nm, operational by 2024.
- Current reality: $165 billion total investment, six fabs planned, Phase 1 (N4) producing since Q4 2024 (profitable by 2025), Phase 2 (3nm) equipment installation Q3 2026, production H2 2027.
- Per-wafer cost: 30-50% higher than Taiwan, even after CHIPS Act subsidies.
- Delays caused by: shortage of experienced fab construction workers, cultural/management frictions, slower permitting, lower construction labor productivity vs. Taiwan.
- **Key point**: These US fabs still depend entirely on ASML (Netherlands), Zeiss (Germany), Japanese materials. Onshoring fabrication redistributes one node while keeping all others globally distributed.

**Intel:**
- Pat Gelsinger departed December 2024 after $16.6 billion net loss. Lip-Bu Tan (former Cadence CEO) took over March 2025.
- Intel 18A achieved high-volume manufacturing late 2025 — first US sub-2nm chips. But external foundry customers remain cautious.
- US government took 9.9% equity stake — effectively guaranteeing Intel won't fail. This is strategic importance requiring a government bailout.
- Magdeburg, Germany fab: **officially cancelled** July 2025. "The company invested too much, too soon — without adequate demand." €10 billion in German subsidies unused.
- **Key lesson**: Manufacturing know-how is a *stock variable* (accumulated over time), not a *flow variable* (purchasable in any given year).

**Samsung:**
- Taylor, Texas fab: delayed, mass production positioned for late 2026 at earliest.
- Samsung foundry business consistently trails TSMC in yield at comparable nodes, even at Korean facilities.

*Sources: TSMC press releases; Tom's Hardware; Manufacturing Dive; TrendForce; Intel earnings; IT Daily.* **[Tier 2/3]**

---

## 3. Historical Attempts at Technological Autarky

*This is the novel research section — the strongest empirical evidence that autarky fails.*

### 3.1 The Soviet Union's Semiconductor Failure

The most instructive historical case:

- **Initial competitiveness (1950s-60s)**: Soviets developed transistor and early IC technology roughly in parallel with the West.
- **Falling behind (1970s-80s)**: Gap opened. Soviets tried domestic R&D, industrial espionage (reverse-engineering Intel processors), importing equipment through front companies to circumvent COCOM export controls.
- **Four reasons autarky failed:**
  1. **No competitive pressure**: Without market competition, no incentive to optimize for yield, cost, or performance.
  2. **Isolation from global knowledge ecosystem**: Cut off from conferences, publications, tacit knowledge in supplier relationships.
  3. **Equipment gap**: Could not manufacture precision lithography equipment. Reverse-engineering physical artifacts failed because tacit manufacturing knowledge cannot be extracted from the artifact itself.
  4. **Scale disadvantage**: Domestic market too small for learning-curve cost reductions.
- **Result**: By mid-1980s, Soviet microprocessors were **10-15 years behind** Western equivalents. This gap contributed to broader technological stagnation undermining Soviet economic and military competitiveness.

*Sources: Hanson, "Rise and Fall of the Soviet Economy" (2003); Goodman in Graham ed. (1990); Miller, "Chip War" (2022); CIA declassified estimates.* **[Tier 1/3]**

### 3.2 China's "Made in China 2025" Semiconductor Push

The contemporary test case — with unprecedented investment and still falling short:

- **Targets (2015)**: 40% self-sufficiency by 2020, 70% by 2025.
- **Actual results (March 2026)**: ~40% overall self-sufficiency (up from ~20-23%), but much at mature nodes and from foreign firms operating in China. Original 70% target not met.
- **SMIC progress** (the most important data point):
  - 7nm (N+2): Achieved 2023 via DUV multi-patterning. Huawei Kirin 9000s.
  - 5nm (N+3): Completed December 2025. Kirin 9030 manufacturing begun.
  - Yields: 7nm Ascend 910C improved from 20% to 40% — still far below TSMC's >90%.
  - 3nm R&D: Started, tape-out expected 2026, using GAA technology.
  - **All achieved without EUV** — DUV multi-patterning makes production ~50% more expensive per wafer than TSMC's EUV equivalent.
- **Equipment self-sufficiency**: Surged to ~35% by end 2025 (up from 13.6% early 2024). Strong in etching, cleaning, CMP. But EUV: prototype assembled, functional chips 2028-2030 at earliest vs. ASML's 20-year development timeline.
- **Big Fund**: Phase I ($21B, 2014), Phase II ($29B, 2019), Phase III ($47.5B, May 2024). Total $100B+ plus provincial/local funds. Plagued by corruption scandals (multiple executives arrested 2022). Returns disappointing.
- **Persistent barriers**: EUV blockade, EDA tools (Empyrean 10-15 years behind Synopsys/Cadence), talent gap (200,000-300,000 experienced engineers short), materials import dependency.

*Sources: TrendForce; TechInsights; WCCFTech; SCMP; Caixin; CSIS; Tom's Hardware.* **[Tier 2/3]**

### 3.3 Other Autarky Attempts

- **India**: Tata-PSMC fab in Gujarat targets mature nodes (28nm+). No leading-edge capability.
- **Japan (Rapidus)**: Pilot line opened April 2025. Working 2nm GAA transistors demonstrated July 2025. $1.7B funding secured. IBM partnership with ~10 engineers on-site. Mass production target 2027. 60+ potential customers. *If successful, adds a democratic node — strengthening the allied supply chain, not breaking from global integration.*
- **European Chips Act**: €43B committed. Centerpiece (Intel Magdeburg) **cancelled July 2025**. EU 20% market share target by 2030 now in serious doubt.

*Sources: Rapidus announcements; TrendForce; The Register; IBM Research; IT Daily.* **[Tier 2/3]**

### 3.4 The Pattern

**Every attempt at semiconductor autarky has either failed outright (Soviet Union), fallen dramatically short of targets (China: 40% vs. 70%), or remained in early/uncertain stages (India, Japan, EU).** The common thread: the semiconductor supply chain's complexity exceeds what any single nation can replicate within a strategically relevant timeframe. And this complexity is *increasing*, not decreasing.

---

## 4. Why Specialization Deepens Over Time

*The supply chain is not just integrated today — it is becoming more integrated, more specialized, and harder to replicate with each passing year.*

### 4.1 Increasing Concentration at the Leading Edge

The number of companies capable of leading-edge fabrication has *collapsed*:

| Year | Node | Companies |
|------|------|-----------|
| 2001 | ~130nm | ~25 |
| 2010 | ~32nm | ~10 |
| 2017 | ~10nm | 4 (TSMC, Samsung, Intel, GlobalFoundries) |
| 2018 | — | 3 (GlobalFoundries abandoned leading edge) |
| 2024 | ~3nm | 2 (TSMC, Samsung), with Intel attempting to rejoin |

Each new node requires more capital, more specialized knowledge, more precise equipment. **The barriers to entry increase with each generation.** This is concentration accelerating, not reversing.

*Sources: SIA; IC Insights historical data.* **[Tier 2]**

### 4.2 Wright's Law and Compounding Advantage

The semiconductor industry follows Wright's Law — costs decrease by a fixed percentage with each doubling of cumulative production. TSMC's cumulative production volume far exceeds any competitor, giving it an inherent cost advantage that *compounds over time*. This is not a lead that can be closed by spending — it can only be closed by producing, and producing takes decades.

*Source: Wright, "Factors Affecting the Cost of Airplanes," J. Aeronautical Sciences (1936); industry application widely discussed.* **[Tier 1]**

### 4.3 Ecosystem Lock-In

- **Customer lock-in**: TSMC's process design kits (PDKs) represent billions in customer-side investment. Apple, Nvidia, AMD have optimized designs for TSMC's specific processes. Switching foundries requires years of re-engineering.
- **Equipment co-development**: TSMC co-develops manufacturing processes with ASML, Applied Materials, etc. Deep IP sharing and joint R&D that newcomers cannot replicate.
- **Knowledge ecosystem**: Cutting-edge R&D disseminated through international venues (IEDM, ISSCC, VLSI Symposia). Isolation from these forums means falling behind. EUV development itself involved US national labs (Sandia, Lawrence Livermore), universities, and companies across three countries over two decades.

### 4.4 Tacit Knowledge — The Deepest Moat

Much critical semiconductor manufacturing knowledge is *tacit* — embedded in the skills and experience of individual engineers and teams, transferring through people, not documents. This is why TSMC's yield advantages persist even though the basic physics of its processes are published. It is why TSMC's own Arizona fab costs 30-50% more per wafer with *identical equipment*. The knowledge is in the people and the accumulated process refinements, not in the blueprints.

*Sources: Polanyi, "The Tacit Dimension" (1966); Appleyard et al. on knowledge management in semiconductor firms; Saxenian, "The New Argonauts" (2006) on talent circulation.* **[Tier 1]**

### 4.5 The Deepening Thesis

**The more advanced the technology becomes, the more specialized the supply chain.** This is not a temporary condition. It is the natural result of increasing returns, learning-by-doing, agglomeration, tacit knowledge, and ecosystem lock-in — all forces that intensify over time. The AI supply chain is not drifting toward fragmentation. It is locking into deeper integration.

---

## 5. Counterarguments and Responses

### 5.1 "China could achieve 'good enough' self-sufficiency"

- **The argument**: Most chips are NOT leading-edge. Mature nodes (28nm+) serve automotive, industrial, IoT, military. China has growing capacity here. For AI inference (vs. training), less-than-cutting-edge chips may suffice.
- **Assessment**: Legitimate. But frontier AI *training* — the capability that determines who leads in AI — requires the most advanced chips. The peace thesis applies most directly to frontier capabilities, where the cost/yield penalty of autarkic production is multiplied by billions in compute spend. SMIC's 5nm is 50% more expensive per wafer and 2+ generations behind.

*Sources: CSIS analyses; SIA data on chip demand by node.* **[Tier 2]**

### 5.2 "Technological breakthroughs could disrupt the supply chain"

- **The argument**: Quantum computing, photonic computing, neuromorphic chips could bypass current supply chains. Advanced packaging/chiplets reduce node-shrink importance. AI itself could optimize away bottlenecks.
- **Assessment**: Plausible on 15-30 year horizon. But even new paradigms will likely require globally sourced precision manufacturing. And history shows: new technological paradigms create *new* specializations and *new* chokepoints, not a return to autarky.

### 5.3 "The CHIPS Act will reduce Taiwan dependency"

- **The argument**: $52.7B in US incentives. TSMC, Samsung, Intel building US fabs. Meaningful domestic leading-edge production by ~2030.
- **Assessment**: CHIPS Act increases US production but cannot achieve self-sufficiency. Total global semiconductor capex is ~$150-180B/year; $52.7B over 5 years is significant but not transformative. US fabs still depend on ASML (Netherlands), Zeiss (Germany), Japanese materials. Even with domestic fabrication, the design ecosystem requires global talent. **Onshoring one node does not break the chain — it moves one link while leaving all others in place.**
- 19 companies, 40 projects awarded as of July 2025. First milestone: TSMC Fab 21 Phase 1 certified complete June 2025.

*Sources: CHIPS Act legislation; CRS analysis; GAO-26-107882; Manufacturing Dive.* **[Tier 1/2]**

### 5.4 "Wartime mobilization could overcome barriers"

- **The argument**: Manhattan Project, Apollo, wartime industrial mobilization show governments can achieve seemingly impossible goals.
- **Assessment**: Valid parallel, but semiconductors differ crucially. Manhattan Project required physics breakthroughs but relatively simple manufacturing (by modern standards). Semiconductor manufacturing requires the opposite — well-understood physics but extraordinarily complex, globally distributed manufacturing. You cannot build an ASML EUV machine on a wartime footing if you don't have Zeiss optics, and Zeiss optics take years to produce.

### 5.5 "AI could compress the catch-up timeline"

- **The argument**: AI could dramatically accelerate materials science, chip design, and manufacturing optimization, compressing the timeline for autarky.
- **Assessment**: The most speculative but intellectually honest counterargument. If AI accelerates *everything*, it could accelerate catch-up too. Two responses: (1) AI also accelerates the *leader's* progress, so the gap may not close. (2) The very technology that could enable catch-up is the technology the supply chain produces — creating a chicken-and-egg problem for would-be autarkists.

### 5.6 "RISC-V eliminates architecture dependency"

- **The argument**: Open-source RISC-V could replace proprietary ARM/x86, removing one dependency layer.
- **Assessment**: Removes one layer, but the *physical* layers (fabrication, equipment, materials) are the binding constraints. RISC-V does not help you build an EUV machine.

---

## 6. Conclusion: The Long-Term Steady State

### The Weight of Evidence

The AI supply chain will remain globally integrated for at least the next **10-15 years**, and probably longer. Six reinforcing forces all point in the same direction:

1. **Deepening specialization and increasing returns** — concentration has gone from 25 to 2 companies at the leading edge in two decades, and barriers keep rising.
2. **No single country controls all layers** — US leads design/EDA; Taiwan fabrication; Netherlands lithography; Japan materials; Germany optics.
3. **Tacit knowledge cannot be purchased** — TSMC's own Arizona fab costs 30-50% more with identical equipment.
4. **Historical autarky has universally failed** — Soviet Union fell 10-15 years behind; China hit 40% vs. 70% target.
5. **Cost penalties are prohibitive** — full onshoring: $1T+ investment, 35-65% price increase (BCG/SIA).
6. **The talent pool is inherently global** — 65%+ of top US AI researchers are foreign-born.

### Scoping the Thesis

- **Strongest for frontier AI** (training large models), which requires leading-edge chips.
- **Weaker for mature-node** chips and inference workloads, where autarky is more feasible.
- **Temporal dimension**: strongest for 2025-2040, less certain thereafter.
- **Honest acknowledgment**: determined autarky efforts, while failing at full independence, could *partially* degrade interdependence — and partial decoupling partially undermines the peace mechanism. This is addressed in Chapter 6 (failure conditions).

### The Bottom Line

Global integration is not a fragile historical accident. It is the equilibrium outcome of economic forces — increasing returns, learning-by-doing, agglomeration, tacit knowledge, ecosystem lock-in — that intensify over time. The supply chain does not merely happen to be global. It *must* be global at the frontier, because no single nation can replicate the full stack of knowledge, equipment, materials, talent, and accumulated process refinements within any strategically relevant timeframe. This is the long-term steady state. And it is on this structural foundation that the Intelligence Peace Thesis rests.

---

## Key Sources

| Source | Tier |
|--------|------|
| Arthur, "Increasing Returns and Path Dependence" (1994) | 1 |
| Krugman, "Increasing Returns and Economic Geography," JPE (1991) | 1 |
| Helpman & Krugman, "Market Structure and Foreign Trade" (1985) | 1 |
| Grossman & Helpman, "Innovation and Growth" (1991) | 1 |
| Sutton, "Sunk Costs and Market Structure" (1991) | 1 |
| Polanyi, "The Tacit Dimension" (1966) | 1 |
| Wright, "Factors Affecting the Cost of Airplanes" (1936) | 1 |
| Saxenian, "Regional Advantage" (1994) / "New Argonauts" (2006) | 1 |
| BCG/SIA, "Strengthening the Global Semiconductor Supply Chain" (2021) | 2 |
| BCG/SIA, "Emerging Resilience in the Semiconductor Supply Chain" (2024) | 2 |
| SIA, "2025 State of the U.S. Semiconductor Industry" (July 2025) | 2 |
| Miller, "Chip War" (2022) | 3 |
| Hanson, "Rise and Fall of the Soviet Economy" (2003) | 1 |
| Georgetown CSET, AI talent publications | 2 |
| ASML Q4 2025 financial results | 2 |
| GAO-26-107882, CHIPS Act progress audit | 1 |
| TSMC earnings and press releases | 2 |
| TechInsights, TrendForce, Digitimes | 3 |
