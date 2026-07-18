# v1.x Incremental Roadmap — Router Restructure + Expanded Workflow Library

**Status:** DRAFT — planning artifact only; nothing implemented
**Branch:** `claude/solution-planning-jud2wc`
**Date:** 2026-07-18
**Relationship to `v2-plan.md`:** This document supersedes the "single jump to 2.0.0"
framing. It keeps that plan's Option B restructure and FAN specification but delivers
them as a train of small v1.x minor releases. `v2-plan.md` §3 (FAN specification) and
§2.3 (drift fixes) remain the source of truth for those work items.

---

## 1. Strategy Shift: v2-as-a-jump → v2-as-a-milestone

Instead of one large 2.0.0 release, v1.x proceeds incrementally:

1. **v1.1.0 restructures SKILL.md into a router** — thin, always-loaded, behavior
   rules + dispatch table — with all workflow depth living in conditionally-loaded
   `references/` guidance files.
2. **Each subsequent v1.x minor adds one workflow** as a self-contained pair:
   `references/<name>-guidance.md` (+ optional `assets/templates/<name>-template.md`).
3. **"2.0.0" becomes a milestone marker** — tagged when the workflow library is
   complete and stable — rather than a big-bang release.

**Why the router makes increments cheap:** SKILL.md is the only always-loaded file.
With workflow detail moved to references, adding a capability costs one router row
(~5 lines of always-loaded text) plus files that load only when triggered. The
always-loaded token footprint stays flat as the library grows from 4 workflows to 10+.

**Semver note:** the restructure ships as **1.1.0**, not 2.0.0 — nothing is removed
from the user's perspective, the behavior contract (planning-first, gated execution)
is unchanged, and templates keep their names and locations. Reorganizing which
internal file holds which prose is not a breaking change for skill consumers.

---

## 2. Router Architecture (v1.1.0 foundation)

### 2.1 SKILL.md after restructure (~1,600–2,000 words, always loaded)

Keep, verbatim or lightly trimmed:
- Planning-first prohibition block (load-bearing; untouched)
- When-to-use triggers (reorganized into the router table)
- Key Genealogical Concepts (source/information/evidence types, proof levels — this is
  shared vocabulary every workflow needs)
- Privacy header, writing style (condensed)

Replace the four long "Procedural Guidelines" workflows with a **router table** — one
row per capability:

| Capability | Triggers (examples) | Load (guidance) | Output (template) |
|---|---|---|---|
| Research Planning | "where do I start", new project | `research-plan-guidance.md` | `research-plan-template.md` |
| Citation Creation | "cite this record" | `citation-templates.md` | `citation-template.md` |
| Evidence Analysis | conflicting facts | `evidence-evaluation.md` | `evidence-analysis-template.md` |
| Research Logging | "log this session" | `research-log-guidance.md` | `research-log-template.md` |
| *(added incrementally — see §4)* | | | |

Each row in the actual SKILL.md is a short block: 2–3 sentence capability summary,
trigger patterns, "read `references/X` before proceeding," and the output template.
The 9–11-step detailed procedures currently in SKILL.md move into their guidance
files (merging with, not duplicating, what's already there).

### 2.2 Guidance-file contract (applies to every workflow, existing and new)

Each `references/<name>-guidance.md` must be **self-contained** once loaded:
1. Full step-by-step workflow (the steps that used to live in SKILL.md)
2. Deep methodology, rubrics, and worked examples
3. Pointer to its output template and to sibling workflows it hands off to
4. Its own privacy note where relevant (living persons, DNA, interviews)

This contract is what makes conditional loading safe: the router row is enough to
dispatch; the guidance file is enough to execute.

### 2.3 v1.1.0 also includes (from `v2-plan.md`)

- All §2.3 drift fixes (SKILL.md references list, stale paths, README diagram/version)
- Frontmatter description rewrite for trigger accuracy (draft in `v2-plan.md` §5.3)
- Verification that `release.yml` packages folders, not enumerated files, so future
  additions ship automatically

---

## 3. Workflow Gap Analysis

Audit of current capabilities against professional practice (GPS/BCG standards,
Mills' methodology) and common user requests. Two tiers: **A** = deserves the full
triad (router row + guidance + template); **B** = conditional reference only, no
dedicated workflow (at least initially).

### Tier A — missing workflows

**A1. FAN Club Research** *(already fully specified in `v2-plan.md` §3)*
Brick walls, unknown parentage, same-name disambiguation. Files:
`fan-club-guidance.md` + `fan-club-worksheet-template.md`.

**A2. Timeline / Chronology Construction**
- *Gap today:* 12 lines under "Advanced Strategies"; no workflow, no template — yet
  "help me organize what I know about X" is among the most common requests, and a
  chronology is the correlation backbone GPS element 3 assumes.
- *Workflow sketch:* gather known facts with sources → normalize dates/places →
  order events → derive implied facts (birth-from-age ranges) → flag gaps and
  conflicts → feed conflicts to Evidence Analysis, gaps to Research Planning.
- *Template:* timeline table — `| Date | Age | Event | Place | Source (cited) |
  Confidence | Conflicts/Notes |` — plus a gaps-and-conflicts summary section.
- *Files:* `timeline-guidance.md` + `timeline-template.md`.

**A3. Document Analysis (Transcription → Abstraction → Extraction)**
- *Gap today:* SKILL.md's triggers promise help "with census records, vital records,
  or other historical documents," but no workflow backs it. "Here's my ancestor's
  will — help me understand it" currently has nowhere to route.
- *Workflow sketch:* identify document type/jurisdiction → transcribe (verbatim
  conventions: original spelling, brackets for illegible, [sic], line breaks) →
  abstract (every name, date, place, relationship, with roles) → analyze (what does
  it directly/indirectly evidence? who are the FAN candidates?) → cite → route
  findings to timeline/evidence-analysis/FAN.
- *Template:* document analysis worksheet (transcription block, abstract table,
  persons-mentioned roster, evidence notes).
- *Synergy:* this workflow is the natural *feeder* for FAN mining (step 2 of the FAN
  workflow) and for citations — high leverage.
- *Files:* `document-analysis-guidance.md` + `document-analysis-template.md`.

**A4. Proof Writing & Research Reporting**
- *Gap today:* GPS element 5 (soundly written conclusion) is a single step at the
  tail of Evidence Analysis. Professional practice distinguishes three proof forms —
  **proof statement** (simple fact, 1–2 sentences + citations), **proof summary**
  (list/narrative of direct evidence), **proof argument** (complex, resolves
  conflicts) — plus the **research report** that packages a session's findings.
  Users ask "write up my findings" and today the skill has no dedicated answer.
- *Workflow sketch:* choose proof form by evidence complexity → assemble evidence
  from analysis/timeline → draft → GPS compliance check → package as report.
- *Files:* `proof-writing-guidance.md` + `research-report-template.md` (the proof
  statement/summary/argument formats live inside the guidance as patterns; only the
  report needs a fill-in template).

**A5. Locality Research Guide**
- *Gap today:* one subsection of `research-strategies.md`. "I've never researched in
  [county/state/country] before" is a standard professional workflow with a standard
  artifact (the locality guide).
- *Workflow sketch:* jurisdiction history (county formation, boundary changes) →
  record-loss events → what records exist for which periods → where they are held
  (with FamilySearch Wiki / LDSgenealogy prioritization already mandated by
  SKILL.md) → local repositories and societies → research implications.
- *Files:* `locality-research-guidance.md` + `locality-guide-template.md`.

### Tier B — conditional references (no router row, or a shared row, initially)

**B1. DNA Evidence Planning** — `dna-evidence-guidance.md`
Planning-level only, true to the skill's ethos: when DNA can/can't help, test-type
selection concepts, match-clustering methodology (e.g., Leeds-style grouping),
correlating clusters with the paper trail, and a **heavy privacy section** (living
matches, ethics of contact, informed consent). No execution, no tool integration.
Loaded when users mention DNA matches, ethnicity results, unknown parentage via DNA.

**B2. Oral History & Family Interviews** — `oral-history-guidance.md`
Interview planning (question sets by generation/topic), recording and consent
ethics, living-persons privacy (reinforces CRAIGEN guidance), and how to cite and
log interview results. Loaded when users mention interviewing relatives.

**B3. Immigrant Origins Methodology** — `immigrant-origins-guidance.md`
The specialized "identify the town of origin" playbook: work the destination records
first, cluster immigration (FAN overlap), naturalization eras and what each yields,
passenger-list strategy, name-form changes. Loaded for "where in [country] did they
come from" questions. *Candidate for promotion to Tier A later if demand shows.*

**B4. Record-Type Deep Dives** — *deferred, split only on evidence of need*
`research-strategies.md` already holds census/land/probate/church strategy sections
at reasonable size. Splitting into per-record-type files now would be premature
fragmentation; revisit if any section outgrows its home.

---

## 4. Release Train

Each release is one reviewable PR-sized increment. Order is adjustable; rationale below.

| Version | Content | New files | Notes |
|---|---|---|---|
| **v1.1.0** | Router restructure + drift fixes + description rewrite | — | Foundation; behavior-neutral except improved triggering. Riskiest diff, so it goes first and alone. |
| **v1.2.0** | FAN Club Research | `fan-club-guidance.md`, `fan-club-worksheet-template.md` | Already fully specified (`v2-plan.md` §3); highest user demand. |
| **v1.3.0** | Document Analysis | `document-analysis-guidance.md`, `document-analysis-template.md` | Before Timeline because it *feeds* FAN mining and citations — completes the brick-wall toolchain opened by v1.2.0. |
| **v1.4.0** | Timeline / Chronology | `timeline-guidance.md`, `timeline-template.md` | Cheap, high value; strengthens correlation (GPS 3). |
| **v1.5.0** | Proof Writing & Reporting | `proof-writing-guidance.md`, `research-report-template.md` | Completes GPS element 5; natural capstone of the analysis chain. |
| **v1.6.0** | Locality Research Guide | `locality-research-guidance.md`, `locality-guide-template.md` | Rounds out Tier A. |
| **v1.7.0** | DNA + Oral History references | `dna-evidence-guidance.md`, `oral-history-guidance.md` | Reference-only release; router gets a shared "specialized topics" row. |
| **v2.0.0** | Milestone tag | — | Library complete; README/marketing refresh; optional housekeeping (release-notes relocation, any renames) batched here where "breaking" is honest. |

End state: **9 workflows/topic areas, ~13 references, ~10 templates**, with SKILL.md's
always-loaded footprint roughly *unchanged* from v1.0.6 thanks to the router.

---

## 5. Acceptance Criteria per Release (standing)

1. SKILL.md stays ≤ ~2,000 words and the planning-first block is byte-identical.
2. New guidance file satisfies the §2.2 self-containment contract.
3. Router table, References list, Templates list, and README diagram all match disk.
4. Trigger check: 2–3 prompts per new workflow route correctly; existing-capability
   control prompts still route to their workflows (no trigger regression).
5. CHANGELOG entry + release notes; packaging verified to include new files.

---

## 6. Open Questions

1. **Order check:** Document Analysis before Timeline (as argued in §4), or swap?
2. **Tier B promotion:** should Immigrant Origins (B3) be Tier A from the start?
3. **Key Concepts placement:** keep the source/information/evidence vocabulary in
   always-loaded SKILL.md (recommended — every workflow uses it), or move to a
   `key-concepts.md` reference to shave more tokens?
4. **v2.0.0 milestone content:** is batching cosmetic renames/relocations there
   acceptable, or should nothing breaking ever ship?

---

*Planning artifact. No implementation started.*
