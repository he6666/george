# Research Essay Co-Writer — Implementation Plan

## Overview

A checkpoint-based research essay pipeline that turns rough idea hunches into
publication-ready essays for Foreign Affairs, LessWrong, and EA Forum. Built as
a Python backend (FastAPI) with a web UI frontend.

---

## Architecture

```
┌─────────────┐     ┌──────────────┐     ┌─────────────┐
│   Web UI    │────▶│  FastAPI      │────▶│  Claude API │
│  (Frontend) │◀────│  Backend      │◀────│  (Anthropic)│
└─────────────┘     └──────┬───────┘     └─────────────┘
                           │
                    ┌──────┴───────┐
                    │  Tavily API  │
                    │  (Research)  │
                    └──────────────┘
```

**Backend:** FastAPI (async, supports streaming for long generations)
**Frontend:** Vanilla HTML/CSS/JS (no framework overhead — this is a tool, not a product)
**AI:** Claude API via `anthropic` Python SDK
**Research:** Tavily Search API (returns clean text, good for synthesis)
**Storage:** SQLite via `sqlite3` (essay projects, checkpoints, style samples)

---

## Pipeline Stages (Checkpoint-Based)

Each stage produces output, pauses for user review/feedback, then proceeds.

### Stage 1: Idea Intake
- **Input:** User's hunch paragraph + target publication (Foreign Affairs / LessWrong / EA Forum)
- **Output:** Parsed thesis statement, key claims, domain tags
- **User checkpoint:** Review/edit extracted thesis before proceeding

### Stage 2: Structure Planning
- **Input:** Thesis + target publication
- **Output:** Recommended essay structure with rationale
  - E.g., "Problem → Historical context → Analysis → Policy recommendation" for Foreign Affairs
  - E.g., "Epistemic status → Core argument → Formal model → Implications → Caveats" for LessWrong
- **User checkpoint:** Approve/modify structure

### Stage 3: Research & Evidence Gathering
- **Input:** Thesis + key claims + domain
- **Process:**
  - Generate 8-12 targeted search queries from the thesis
  - Run searches via Tavily API
  - Cluster results by relevance to each claim
  - Extract key findings, statistics, quotes, citations
  - Identify potential counterarguments from the literature
- **Output:** Research brief — organized evidence mapped to claims, with source citations
- **User checkpoint:** Review sources, flag any to include/exclude, add manual sources

### Stage 4: Outline with Evidence
- **Input:** Structure + research brief
- **Output:** Detailed section-by-section outline with:
  - Section purpose and argument flow
  - Specific evidence/citations allocated to each section
  - Transition logic between sections
  - Planned counterargument placement
- **User checkpoint:** Review outline, reorder sections, adjust emphasis

### Stage 5: First Draft
- **Input:** Outline + evidence + style profile
- **Process:** Draft each section sequentially, maintaining argument coherence
- **Output:** Complete first draft with inline citations
- **User checkpoint:** Edit draft, flag weak sections, request expansions/cuts

### Stage 6: Counterargument & Rebuttal Pass
- **Input:** Draft
- **Process:**
  - Identify the 3-5 strongest objections to the argument
  - Steelman each objection
  - Generate rebuttals using evidence from research
  - Integrate into draft at appropriate points
- **Output:** Revised draft with counterargument handling
- **User checkpoint:** Review counterarguments, adjust strength of rebuttals

### Stage 7: Style Polish & Final Edit
- **Input:** Draft + target publication style profile + user writing samples
- **Process:**
  - Adjust register, sentence structure, vocabulary for target venue
  - Check citation format matches venue conventions
  - Tighten prose, remove redundancy
  - Verify argument coherence end-to-end
- **Output:** Publication-ready essay
- **User checkpoint:** Final review

---

## Style System

### Publication Profiles (built-in)

Each profile encodes:
- **Tone:** (e.g., Foreign Affairs = authoritative/measured; LessWrong = precise/epistemic humility)
- **Structure conventions:** (e.g., FA uses policy-oriented framing; LW uses epistemic status headers)
- **Citation style:** (e.g., FA = minimal inline attribution; LW = hyperlinks; EA Forum = mix)
- **Vocabulary register:** (e.g., FA = diplomatic/institutional; LW = rationalist/technical)
- **Typical length:** (e.g., FA = 3000-5000 words; LW = varies widely)
- **Example prompts** that capture the style

### User Writing Samples

- Users upload 2-5 of their own published pieces
- System extracts: sentence length distribution, vocabulary preferences, rhetorical patterns,
  how they handle hedging/confidence, paragraph structure
- Stored per-user in SQLite
- At generation time, the style profile + user sample analysis are combined into a
  style instruction prompt

---

## Project Structure

```
research-cowriter/
├── backend/
│   ├── main.py                 # FastAPI app entry point, CORS, routes
│   ├── pipeline/
│   │   ├── __init__.py
│   │   ├── intake.py           # Stage 1: thesis extraction
│   │   ├── structure.py        # Stage 2: essay structure planning
│   │   ├── research.py         # Stage 3: web search + evidence gathering
│   │   ├── outline.py          # Stage 4: detailed outline generation
│   │   ├── draft.py            # Stage 5: first draft generation
│   │   ├── counterargument.py  # Stage 6: counterargument pass
│   │   └── polish.py           # Stage 7: style matching + final edit
│   ├── style/
│   │   ├── __init__.py
│   │   ├── profiles.py         # Built-in publication style profiles
│   │   └── analyzer.py         # User writing sample analysis
│   ├── search/
│   │   ├── __init__.py
│   │   └── tavily_client.py    # Tavily API wrapper
│   ├── db/
│   │   ├── __init__.py
│   │   └── models.py           # SQLite schema + queries
│   ├── prompts/
│   │   ├── __init__.py
│   │   └── templates.py        # All Claude prompt templates
│   └── config.py               # API keys, settings
├── frontend/
│   ├── index.html              # Main page
│   ├── app.js                  # UI logic, stage navigation, API calls
│   └── styles.css              # Styling
├── requirements.txt
├── .env.example                # Template for API keys
└── README.md
```

---

## API Endpoints

```
POST /api/projects                    # Create new essay project
GET  /api/projects/{id}               # Get project state
POST /api/projects/{id}/intake        # Stage 1: submit hunch
POST /api/projects/{id}/structure     # Stage 2: generate structure
POST /api/projects/{id}/research      # Stage 3: run research
POST /api/projects/{id}/outline       # Stage 4: generate outline
POST /api/projects/{id}/draft         # Stage 5: generate draft
POST /api/projects/{id}/counterargs   # Stage 6: counterargument pass
POST /api/projects/{id}/polish        # Stage 7: style polish
PATCH /api/projects/{id}/stage/{n}    # User edits to any stage output
POST /api/projects/{id}/feedback      # User feedback at checkpoint
POST /api/style/samples              # Upload writing samples
GET  /api/style/profiles             # List available publication profiles
```

---

## Data Model (SQLite)

### projects
| Column         | Type    | Description                          |
|----------------|---------|--------------------------------------|
| id             | TEXT PK | UUID                                 |
| title          | TEXT    | Auto-generated from thesis           |
| hunch          | TEXT    | Original user input                  |
| target_pub     | TEXT    | "foreign_affairs" / "lesswrong" / "ea_forum" |
| current_stage  | INT     | 1-7                                  |
| created_at     | TEXT    | ISO timestamp                        |
| updated_at     | TEXT    | ISO timestamp                        |

### stage_outputs
| Column      | Type    | Description                             |
|-------------|---------|----------------------------------------|
| id          | TEXT PK | UUID                                    |
| project_id  | TEXT FK | References projects.id                  |
| stage       | INT     | 1-7                                     |
| output      | TEXT    | JSON blob of stage output               |
| user_edits  | TEXT    | JSON blob of user modifications         |
| feedback    | TEXT    | User feedback text                      |
| created_at  | TEXT    | ISO timestamp                           |

### style_samples
| Column      | Type    | Description                             |
|-------------|---------|----------------------------------------|
| id          | TEXT PK | UUID                                    |
| title       | TEXT    | Sample title                            |
| content     | TEXT    | Full text of writing sample             |
| analysis    | TEXT    | JSON blob of extracted style features   |
| created_at  | TEXT    | ISO timestamp                           |

---

## External Dependencies

| Package         | Purpose                                |
|-----------------|----------------------------------------|
| fastapi         | Web framework                          |
| uvicorn         | ASGI server                            |
| anthropic       | Claude API client                      |
| tavily-python   | Tavily search API client               |
| python-dotenv   | Environment variable management        |
| python-multipart| File upload support (writing samples)  |

---

## Implementation Order

1. **Project scaffolding** — directory structure, requirements.txt, config, .env.example
2. **Database layer** — SQLite schema, basic CRUD
3. **Style profiles** — encode Foreign Affairs, LessWrong, EA Forum profiles
4. **Pipeline Stage 1** (Intake) — thesis extraction + API endpoint + UI
5. **Pipeline Stage 2** (Structure) — structure planning + endpoint + UI
6. **Pipeline Stage 3** (Research) — Tavily integration + search query generation + endpoint + UI
7. **Pipeline Stage 4** (Outline) — outline generation + endpoint + UI
8. **Pipeline Stage 5** (Draft) — full draft generation + endpoint + UI
9. **Pipeline Stage 6** (Counterarguments) — objection handling + endpoint + UI
10. **Pipeline Stage 7** (Polish) — style matching + endpoint + UI
11. **Style sample upload** — file upload, analysis, storage
12. **Frontend polish** — stage navigation, editing UX, export

---

## Key Design Decisions

**Why FastAPI over Flask?**
Async support matters — Claude API calls and Tavily searches are I/O-bound. FastAPI
handles concurrent requests naturally and has built-in streaming response support for
long generations.

**Why SQLite over a full database?**
This is a single-user tool. SQLite is zero-config, file-based, and more than sufficient.
No deployment overhead.

**Why Tavily for search?**
Returns clean, pre-extracted text (not raw HTML). Designed for AI consumption. Good
academic and news source coverage. One API call returns structured results ready for
synthesis.

**Why vanilla frontend?**
This is a writing tool — the UI is mostly text display and editing. A framework would
add build complexity without meaningful benefit. If the UI needs to grow later, we
can migrate to something like Svelte.

**Why checkpoint-based over streaming end-to-end?**
Research essays require human judgment at key junctures. An outline that's structurally
wrong produces a bad draft no matter how well-written. Checkpoints catch errors early
and keep the user in control of the argument.
