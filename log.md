# Wiki log

Append-only timeline of ingest, filed queries, and lint passes.

Log entry convention (parse-friendly):

```text
## [YYYY-MM-DD] <ingest | query | lint> | <short title>
```

---

## [2026-05-13] init | Vault LLM Wiki bootstrap

- Created `CLAUDE.md` schema, `wiki/` taxonomy, vault-root `index.md` + `log.md`.
- Added `raw/assets/` place for clipped images.
- First ingest queued: [[raw/Public Holidays]].

## [2026-05-13] ingest | Public Holidays

- Raw: [[raw/Public Holidays]]
- Wiki touches: [[wiki/sources/Public Holidays]], [[wiki/concepts/Public holidays (Hong Kong)]], [[wiki/entities/Workday Benefits]], [[wiki/overview]]
- Notes: Established baseline for HK public holidays 2026; flagged dependency on official Hong Kong announcements for calendar changes.

## [2026-05-13] ingest | batch — remaining `raw/*.md` Workday HK clips

- Raws: all markdown clippings in `raw/` **except** the already-ingested [[raw/Public Holidays]] (20 files in this pass: Bright Days Off; Business Travel Medical and Security; Compassionate Leave; Enhanced Bonding Leave; Flexi Benefit; Financial Investments; Financial Wellbeing Support; For When Life Happens; Health Insurance 1; Here to Support Your Health; House Rent Reimbursement; Leave Entitlement; Life Insurance; Mind Matters (EAP); Personal and Extended Leave of Absence; Taking Time Off; Taking Time Off 1; Taking Time Off 2; Time Off in Lieu; Women's Health and Family Support).
- Wiki touches: matching `wiki/sources/*` digests; new concepts under `wiki/concepts/*` (leave map, PLOA, compassionate, bonding, TOIL, travel assistance, flex, AIA medical, Maven, Mind Matters, financial programmes); refreshed [[wiki/entities/Workday Benefits]], [[wiki/overview]], [[index]].
- Notes: Documented **Leave Entitlement table vs PLOA detail** tension; Maven Wallet vs AIA fertility bullets need broker alignment; several raw pages are FAQ stubs only.

## [2026-05-13] ingest | Business Travel Accident & Business Travel Medical (PDF)

- Raw: [[raw/Business Travel Accident & Business Travel Medical.pdf]]
- Wiki touches: [[wiki/sources/Business Travel Accident & Business Travel Medical]], [[wiki/sources/Business Travel Medical and Security]], [[wiki/concepts/Business travel assistance (ISOS and Chubb)]], [[wiki/entities/Workday Benefits]], [[wiki/overview]], [[index]]
- Notes: Chubb **Schedule of Benefits** for policy ADD N18767041 (effective 2026-01-01); linked as authoritative caps alongside portal digest; **Israel** sub-limits and exclusion of security evacuation / travel inconvenience captured.

## [2026-05-13] ingest | batch — remaining PDFs in `raw/`

- Raws: [[raw/AIA Health Insurance Coverage.pdf]], [[raw/CHUBB Business Travel Program.pdf]], [[raw/CHUBB Claim Kit.pdf]], [[raw/LGBT TRAVELERS IN THE AMERICAS.pdf]], [[raw/TribeGO_App_User_Guide_Workday_Hong_Kong_2026_copy.pdf.pdf]] (already ingested earlier same day: [[raw/Business Travel Accident & Business Travel Medical.pdf]]).
- Wiki touches: new [[wiki/sources/AIA Health Insurance Coverage]], [[wiki/sources/CHUBB Business Travel Program]], [[wiki/sources/CHUBB Claim Kit]], [[wiki/sources/LGBT TRAVELERS IN THE AMERICAS]], [[wiki/sources/TribeGO App User Guide (Workday Hong Kong)]]; patched [[wiki/sources/Health Insurance 1]], [[wiki/sources/Flexi Benefit]], [[wiki/sources/Business Travel Medical and Security]], [[wiki/sources/Business Travel Accident & Business Travel Medical]]; concepts [[wiki/concepts/Group medical insurance (AIA Hong Kong)]], [[wiki/concepts/Flexible benefits (Hong Kong)]], [[wiki/concepts/Business travel assistance (ISOS and Chubb)]]; [[wiki/entities/Workday Benefits]], [[index]].
- Notes: AIA summary **Plan 001** HKD figures **2026-02-01–2027-01-31**; Chubb kit lists **Hong Kong** under North American claims cohort; LGBT PDF filename says Americas but body covers **five regions**; TribeGO raw filename has duplicate `.pdf` extension.

## [2026-05-13] query | index Raw quick map

- Q: Clarify that `raw/` inputs include **`.md`** and **`.pdf`** alongside Sources rows.
- Files: [[index]]
- Notes: **Raw quick map** sentence tightened; examples added.

## [2026-05-14] ingest | Paid Time Off (PTO) Policy

- Raw: [[raw/Paid Time Off (PTO) Policy]] (content aligned with prior `Clippings/Paid Time Off (PTO) Policy.md` clipping from the same portal URL)
- Wiki touches: [[wiki/sources/Paid Time Off (PTO) Policy]], [[wiki/concepts/Paid time off policy (Workday)]], [[wiki/sources/Leave Entitlement]], [[wiki/concepts/Leave entitlement overview (Hong Kong)]], [[wiki/entities/Workday Benefits]], [[wiki/overview]], [[index]]
- Notes: Regional **EMEA/APAC/Japan** mechanics; pair with [[wiki/sources/Leave Entitlement]] for HK accrual ladder; **People Leaders** responsibilities section blank in clip.

## [2026-05-14] ingest | Corporate Travel & Expense Card (FAQ + User Agreement)

- Raw: [[raw/Everything You Need to Know About The Corporate Travel Credit Card]], [[raw/Workday Corporate Travel and Expense Card User Agreement]]
- Wiki touches: [[wiki/sources/Everything You Need to Know About The Corporate Travel Credit Card]], [[wiki/sources/Workday Corporate Travel and Expense Card User Agreement]], [[wiki/concepts/Corporate travel and expense card (Workday)]], [[wiki/concepts/Business travel assistance (ISOS and Chubb)]], [[wiki/entities/Workday Benefits]], [[wiki/overview]], [[index]]
- Notes: **Bank of America** programme; pairs operational FAQ (`bofaml.com/globalcardaccess`, fraud/dispute flows) with **User Agreement** (30-day reporting + liability carve-outs, HR card recovery duties, US-only Amazon caveat). Threshold **USD 3k annual travel→mandatory card** cites live **Travel & Expense Policy** link not clipped in vault.

## [2026-05-14] ingest | Sick leave enquiry (HK — HR ticket)

- Raw: [[raw/Sick leave enquiry]]
- Wiki touches: [[wiki/sources/Sick leave enquiry]], [[wiki/concepts/Leave entitlement overview (Hong Kong)]], [[wiki/entities/Workday Benefits]], [[wiki/overview]], [[index]]
- Notes: ServiceNow HR case excerpt (2024-10); People & Purpose lines: **no sick certificate for 1 day** HK paid sick; certificate when leave **greater than two days**. Flagged as **informal precedent** pending alignment with Compass / entitlement articles.

## [2026-05-14] ingest | FY27 General Terms + PlanDocument (sales compensation)

- Raws: [[raw/FY27 General Terms.pdf]], [[raw/PlanDocument.pdf]]
- Wiki touches: [[wiki/sources/FY27 General Terms]], [[wiki/sources/FY2027 Individual Goal Sheet (PlanDocument)]], [[wiki/concepts/Sales compensation plan FY2027 (Workday)]], [[wiki/entities/Workday Benefits]], [[wiki/overview]], [[index]]
- Notes: General Terms = global FY2027 Sales Comp framework (Plan Period **2026-02-01–2027-01-31**); PlanDocument = Individual Goal Sheet instance — wiki digests avoid pasting participant compensation tables (see raw for numbers).

## [2026-06-12] lint | full vault health check

### Staleness fixed
- **[[wiki/overview.md]]** — struck out stale open gap on Maven Wallet/AIA fertility reconciliation; annotated as resolved 2026-06-12 per [[wiki/concepts/Maven family and reproductive benefits]].
- **[[wiki/sources/Women's Health and Family Support]]** — Summary section now flags Maven Wallet as US-only from 2026-02-01 (was only in Contradictions).

### Contradictions (existing, already documented)
- **PLOA eligibility table vs detail page** — [[wiki/sources/Leave Entitlement]] row understates day-one PLOA; resolution pointer in place across concept and source pages. No change needed.
- **Sick leave cert threshold** — [[wiki/sources/Sick leave enquiry]] informal ticket; flagged as pending formal policy reconciliation. No change needed.

### Orphans
- No true orphans: all source pages are linked from [[wiki/entities/Workday Benefits]] hub and/or at least one concept page.
- **Near-orphan:** [[wiki/sources/LGBT TRAVELERS IN THE AMERICAS]] is listed in the entity hub but has no inbound concept page — low priority unless travel policy questions arise.

### Missing concept stubs (created)
- **[[wiki/concepts/Caregiving leave (Workday)]]** — new page; 12 wks / 50% base; layering table vs compassionate + PLOA.
- **[[wiki/concepts/Life insurance (AIA Hong Kong)]]** — new page; AIA group life/AD&D/TPD/CI/LTD stack; linked from [[wiki/sources/Life Insurance]].
- **[[wiki/concepts/Employee Relief Fund (E4E)]]** — stub only; no raw source ingested; flags open questions for P&P.
- **[[index]]** updated with all three new concept entries.

## [2026-06-12] query | Maven Wallet HK ineligibility (effective 2026-02-01)

- Q: Maven Wallet is now US-only; HK employees ineligible since 2026-02-01.
- Files touched: [[wiki/concepts/Maven family and reproductive benefits]], [[wiki/sources/Women's Health and Family Support]], [[wiki/sources/Health Insurance 1]], [[wiki/sources/AIA Health Insurance Coverage]]
- Notes: Added HK-ineligibility callout to Maven concept page; updated Contradictions sections on Women's Health and Health Insurance 1 source digests to mark Wallet bullets as US-only; resolved prior "reconcile with broker" open question on AIA HKD 50k fertility — that is now the complete HK fertility insurance picture. Maven core virtual care (non-Wallet) scope unconfirmed — flagged for P&P check.