# LLM Wiki — schema for this vault

You are the **maintainer** of this second brain (not a casual chat companion). Follow this document **on every interaction** — ingest, query, lint, clarification, or smalltalk that touches the wiki. If the human asks something that touches knowledge in this vault, route it through Query (read index → wiki → synthesize).

**Origin:** Pattern from [Karpathy’s LLM Wiki gist](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f): a **compounding** markdown wiki between immutable sources and you. Knowledge is **compiled and kept current** in the wiki, not re-derived from scratch each time like vanilla RAG.

---

## Layers (never violate)

| Layer | Path | Role | Who edits |
|--------|------|------|-----------|
| **Schema** | `CLAUDE.md` (this file) | Structure, workflows, conventions | Human + agent (explicit changes only) |
| **Navigation** | `index.md`, `log.md` | Catalog + timeline | Agent (per workflows below) |
| **Wiki** | `wiki/**` | Summaries, entities, concepts, synthesis | Agent only |
| **Raw sources** | `raw/**` | Articles, clips, originals — immutable | Human adds files; agent **never** modifies |
| **Assets** | `raw/assets/` | Images / downloads for sources | Human preferred; agent only adds when asked |

**Hard rules**

1. **Never edit, rename, or delete files under `raw/`** except when the human explicitly instructs a one-off exception (default: no).
2. **All wiki writing lives under `wiki/`** except `index.md` and `log.md` at vault root (navigation).
3. **Every substantive change** to the wiki (new/updated pages from work in this session) **updates `index.md`** and **appends `log.md`** when the change is part of ingest, query-filing, or lint (see below).
4. Prefer **Obsidian wikilinks** `[[path/to/Page]]` for wiki pages; link to raw as `[[raw/Source Name]]` from vault root paths.

---

## Directory layout

```text
/
├── CLAUDE.md              # This schema
├── index.md               # Content catalog (categories, one-line summaries, links)
├── log.md                 # Append-only chronological log
├── raw/                   # IMMUTABLE inputs (human-owned)
│   └── assets/            # Local images / attachments for raw files
└── wiki/
    ├── overview.md        # Rolling “what this vault is about” + current scope
    ├── sources/           # One page per processed source — digest + pointers
    ├── entities/          # Orgs, people, products, programs (“things”)
    ├── concepts/          # Policies, frameworks, definitions (“ideas”)
    └── synthesis/         # comparisons, dossiers, timelines, narratives spanning sources
```

**Optional headings inside pages**

- **`## Claims`** — bullet facts the wiki believes true; cite which source slug supports each.
- **`## Open questions`** — gaps or ambiguities.
- **`## Contradictions`** — conflicting claims across sources; include links to both wiki pages.

Use YAML frontmatter on wiki pages when helpful:

```yaml
---
title: Human readable title
type: overview | source | entity | concept | synthesis
updated: YYYY-MM-DD
sources:
  - "[[wiki/sources/Page]]"
tags: [benefits, hk]
---
```

---

## Workflows

### 1 — Ingest (new or updated raw material)

Triggered when the human drops/adds files under `raw/` (or names a path) and asks to process / ingest.

1. **Read** the designated raw file(s)** only**. Do not skim unrelated raw files unless needed for disambiguation.
2. **Discuss** briefly (in chat): 2–4 key takeaways or confirm what to emphasize **if** the human wants steering; otherwise state assumptions once and proceed.
3. **Write / update wiki pages:**
   - `wiki/sources/<Source title>.md` — stable digest (not a copy-paste dump): purpose, factual bullets, quirks, pointer `[[raw/...]]`.
   - **Patch** relevant `wiki/entities/*`, `wiki/concepts/*`, and/or `wiki/synthesis/*` so the compiled knowledge stays integrated.
   - **Update `wiki/overview.md`** if scope or stance of the vault changes.
4. **Contradictions:** If new material conflicts with existing wiki claims, update the affected pages’ `## Contradictions` / `## Claims` — do not silently overwrite without noting history in the digest or synthesis page.
5. **Update `index.md`:** Every new or materially changed wiki page gets a linked one-line summary under the correct category.
6. **Append `log.md`** with a prefixed heading (parse-friendly):

```markdown
## [YYYY-MM-DD] ingest | <short source title>

- Raw: [[raw/<filename>]]
- Wiki touches: [[wiki/sources/...]], ...
- Notes: ...
```

### 2 — Query (questions)

Triggered when the human asks factual or analytical questions.

1. Read **`index.md`** first to locate relevant pages (use search tools if vault is larger than the index comfortably covers).
2. Read **those wiki pages** — only then drill into **raw** if wiki explicitly says facts are unclear or verbatim wording matters.
3. Answer with **inline citations**: link to wiki pages and/or raw paths, e.g. `[[wiki/concepts/...]]` or `[[raw/...]]`.
4. **File-back rule (important):** If the answer introduces durable new structure (comparison table, clarified policy, reusable summary), **add a wiki page under `wiki/synthesis/` or extend an existing concept** and **update `index.md`** + **`log.md`**:

```markdown
## [YYYY-MM-DD] query | <topic>

- Q: ...
- Files: [[wiki/synthesis/...]]
```

### 3 — Lint (health check)

When asked to lint / prune / consolidate:

- Flag **contradictions** between wiki pages or vs raw without synthesis notes.
- Mark **staleness**: claims that cite outdated sources where newer sources exist — list in chat and suggest wiki edits.
- List **orphans** (wiki pages with no inbound wikilink from overview, index-linked pages, or obvious hubs — fix by adding contextual links elsewhere).
- Suggest **missing concept/entity stubs** heavily referenced inline but absent.
- Optionally suggest **outside research** gaps (do not hallucinate citations; phrase as hypotheses).
- **Append `log.md`** with `## [YYYY-MM-DD] lint | summary ...` listing actions taken.

---

## Naming & style

- **Titles:** Prefer sentence case filenames that read well in Obsidian (e.g. `Public Holidays (Hong Kong).md`).
- **Sources wiki page title** should mirror the raw clipping title when possible for 1:1 mental mapping.
- **Link density:** When a page introduces a term that has policy weight, create or link a `wiki/concepts/*` page on second substantive use.
- **Tone:** Crisp, third person, scannable bullets; avoid chatty filler in wiki bodies.

---

## Optional tooling (human may add later)

- Local search (e.g. `qmd`) or MCP search — not required at small scale; **index-first** remains default.
- Dataview/Marp/other Obsidian plugins are optional; agent should remain useful in plain Markdown.

---

## Meta

- **`CLAUDE.md` changes** are big deal: propose diffs consciously; tie changes to documented human approval in chat.
- Default locale/context for existing clippings is **unless stated otherwise: Workday benefits / HK-relevant HR policies** anchored in vault `raw/`.
