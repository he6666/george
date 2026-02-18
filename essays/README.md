# Essays Directory

Each essay lives in its own folder, named with a URL-friendly slug.

## Creating a new essay

1. Create a folder: `essays/<your-slug>/`
2. Write your hunch: `essays/<your-slug>/00-hunch.md`
3. Run the pipeline stages in order:
   - `run intake on <slug>` → produces `01-intake.md`
   - `run strategy on <slug>` → produces `02-strategy.md`
   - `run research on <slug>` → produces `03-research.md`
   - `run draft on <slug>` → produces `04-draft.md`
   - `run polish on <slug>` → produces `05-polished.md`

Review and edit after each stage before proceeding to the next.

## Folder structure

```
essays/<slug>/
  00-hunch.md           # Your raw idea (you write this)
  00b-seeds.md          # Your foundational sources and context (prompted during research)
  01-intake.md          # Structured brief
  02-strategy.md        # Essay plan
  03-research.md        # Synthesized research notes
  04-draft.md           # Full draft (post-review)
  05-polished.md        # Publication-ready version
  sources/              # Drop your own PDFs, links, or notes here (optional)
  .research/            # Agent working papers (auto-generated)
    phase1-landscape.md
    phase1-academic.md
    phase1-policy.md
    phase1-discourse.md
    phase2-deep-reads.md
    phase2-citations.md
    phase3-gaps.md
    phase3-contradictions.md
    red-team-review.md
    revision-log.md
    flow-check.md
```

## The `.research/` folder

This folder contains the raw outputs from every research and review agent. It's preserved for transparency — you can inspect exactly what each agent found, how the Red Team critiqued the draft, and what was revised in response.

## Multi-venue polish

To produce versions for different publications from the same draft:
- `run polish on <slug> for foreign-affairs` → `05-polished-fa.md`
- `run polish on <slug> for rationalist` → `05-polished-lw.md`
- `run polish on <slug> for substack` → `05-polished-substack.md`

## Tips

- **The hunch can be rough.** A single paragraph is fine. The intake stage will structure it.
- **Edit between stages.** The pipeline is human-in-the-loop. Your edits between stages improve everything downstream.
- **Add sources early.** If you have relevant papers or articles, drop them in `sources/` before the research stage.
- **The draft stage is where your voice matters most.** Edit `04-draft.md` heavily before polishing.
