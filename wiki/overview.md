---
title: Vault overview
type: overview
updated: 2026-05-13
tags: [benefits, workday]
---

## What this vault is

Personal **second brain** using the **LLM Wiki** pattern: immutable notes in the `raw/` folder are summarized and interlinked under `wiki/`. Navigation: [[index]], evolution trail: [[log]].

## Current scope

- **Corpus:** Workday **Hong Kong benefits** materials in `raw/` — primarily portal **Markdown** clippings; **PDF** schedules/certificates when supplied (HR, leave, insurance, travel, financial wellbeing, family support).
- **Compilation status:** **All current `raw` markdown clips are ingested** into `wiki/sources/*`; PDF sources ingested on demand with matching digests — cross-linked **concepts** and hub [[wiki/entities/Workday Benefits]].

## How to extend

Add new files under `raw/` (and attachments under `raw/assets/`) → request **ingest** → expect updates to sources, concepts, [[wiki/entities/Workday Benefits]], [[index]], and [[log]].

## Open gaps

- Some clips contain **stub FAQ sections** without answers — live site or People Guide may hold detail.
- **Known doc tension:** [[wiki/sources/Leave Entitlement]] summary row vs [[wiki/sources/Personal and Extended Leave of Absence]] for PLOA eligibility windows — flagged in [[wiki/concepts/Leave entitlement overview (Hong Kong)]].
- Fertility funding bullets on [[wiki/sources/Health Insurance 1]] need **broker confirmation** against Maven Wallet language.
- No multi-policy **synthesis dossier** yet (optional next step for cross-comparisons).
