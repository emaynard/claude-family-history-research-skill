# v2.0 Planning Document — FAN Club Research Workflows & Skill Restructuring

**Status:** DRAFT — planning artifact only; nothing in this document is implemented yet
**Branch:** `claude/solution-planning-jud2wc`
**Date:** 2026-07-18
**Baseline:** v1.0.6 (SKILL.md body version; frontmatter unversioned per v1.0.6 policy)

---

## 1. Vision Statement

v2 elevates the skill from a *four-capability* planning assistant (plan, cite, analyze,
log) to a *five-capability* assistant by making **FAN Club research (Family, Associates,
Neighbors)** a first-class workflow with its own methodology reference, worksheet
template, and output document — while tightening the skill's internal structure so every
capability follows the same predictable pattern the v1.0.4–1.0.5 releases established:

> **simple template in `assets/templates/` + deep guidance in `references/` + concise
> workflow in `SKILL.md`**

The skill's core identity — **planning first, no unsolicited searches** — is unchanged
and is restated as a hard invariant for all v2 work.

---

## 2. Current-State Assessment (v1.0.6)

### 2.1 What exists

| Capability | SKILL.md workflow | Template (assets) | Guidance (references) |
|---|---|---|---|
| 1. Research Planning | ✅ | `research-plan-template.md` | `research-plan-guidance.md`, `research-strategies.md` |
| 2. Citation Creation | ✅ | `citation-template.md` | `citation-templates.md` |
| 3. Evidence Analysis | ✅ | `evidence-analysis-template.md` | `evidence-evaluation.md`, `gps-guidelines.md` |
| 4. Research Logging | ✅ | `research-log-template.md` | `research-log-guidance.md` |
| **FAN research** | ❌ (one bullet in planning workflow) | ❌ | Partial (~1 section of `research-strategies.md`) |

### 2.2 FAN coverage today is principle-only

- `SKILL.md` mentions FAN three times, always as an adjective ("plan FAN approach",
  "Apply FAN principle") — there is no procedure a user or Claude can follow.
- `references/research-strategies.md` §1 defines FAN and gives a short example, but
  stops before the operational questions: *how do I inventory FAN candidates from the
  records I already have? how do I rank them? what document do I produce?*
- No output artifact exists — FAN work done today leaves no trace in the user's
  research files, which undermines GPS element 1 (reasonably exhaustive research)
  and element 3 (analysis and correlation).

### 2.3 Known documentation drift (fix in v2 regardless of scope decisions)

1. `SKILL.md` §References list is malformed: `research-log-guidance.md` and
   `research-plan-guidance.md` lack the `references/` path prefix, and there is a
   stray empty `- ` bullet (lines 285–287).
2. `SKILL.md` Capability 1 still points to `assets/templates/research-plan-guidance.md`
   (line 56) — that file moved to `references/` in v1.0.5.
3. `README.md` structure diagram predates the v1.0.5 reorganization: it shows
   `research-plan-guidance.md` under `assets/templates/` and omits
   `references/research-log-guidance.md` entirely.
4. `README.md` "Version" section still says "Version 1.0, October 2025".
5. Frontmatter `description` ("Provides assistance with planning family history and
   genealogy research projects.") carries almost no trigger vocabulary — see §5.3.

---

## 3. New Capability: FAN Club Research Workflow

### 3.1 Concept

FAN Club research (methodology popularized by Elizabeth Shown Mills) researches the
*network* around a subject — Family, Associates, and Neighbors — to resolve questions
the subject's own records cannot answer. It is the standard professional response to
brick walls: unknown parentage, same-name disambiguation, origin/migration questions,
and record-poor ancestors.

In v2 it becomes **Core Capability 5**, with the same three-part anatomy as the other
four capabilities.

### 3.2 When the workflow triggers

Add these trigger patterns to SKILL.md's "When to Use This Skill":

- "I've hit a brick wall on…" / "I can't find [ancestor]'s parents"
- "There are two men with the same name — how do I tell them apart?"
- "My ancestor appears out of nowhere in [place] — where did they come from?"
- "Who are these witnesses / bondsmen / godparents on this record?"
- Any research plan where Tier 1–2 sources (census, vital, land, probate) have been
  exhausted without answering the research question

The workflow also becomes the *recommended escalation* from the existing Brick Wall
Strategies section of `research-strategies.md` (which currently lists "Research
Collateral Lines" as strategy #4 but gives no procedure).

### 3.3 Proposed workflow (to be added to SKILL.md Procedural Guidelines)

**FAN Club Research Workflow** — nine steps, planning-first like all others:

1. **Define the stalled question** — which specific research question is blocked, and
   why direct evidence has been exhausted (links to existing research plan/log).
2. **Mine existing sources for FAN candidates** — a systematic re-reading pass over
   records *already collected*, per record type:
   - Census: ±5–10 households around the subject; same-surname clusters in the
     enumeration district
   - Deeds: witnesses, adjoining landowners, grantors/grantees in chained transactions
   - Probate: witnesses, executors/administrators, bondsmen, appraisers, estate-sale
     buyers, guardians
   - Church: baptismal sponsors/godparents, marriage witnesses, fellow congregants
   - Marriage: bondsmen, sureties, officiants, witnesses
   - Immigration/naturalization: fellow passengers, character witnesses, sponsors
   - Newspapers: co-mentions in notices, social columns, legal advertisements
3. **Build the FAN roster** — record every candidate in the FAN worksheet (new
   template, §3.4) with name, role, connecting record, citation, and place/date.
4. **Assess connection strength** — rate each FAN member:
   - **Strong:** recurring across multiple records; kinship-suggestive roles
     (bondsman, godparent, executor, guardian); shared migration
   - **Moderate:** repeated proximity (neighbor across ≥2 censuses); single
     kinship-suggestive role
   - **Weak:** single incidental appearance (one-time witness, distant neighbor)
5. **Prioritize research targets** — rank by connection strength × expected record
   availability; select the top 3–5 FAN members.
6. **Create mini research plans** — one per priority target, reusing the existing
   `research-plan-template.md` (scoped-down; the FAN worksheet links to them).
7. **Research and log** — execution stays gated behind explicit user request, exactly
   per the existing Step 3 rules; all searches go into the existing research log.
8. **Correlate findings** — complete the worksheet's correlation matrix (FAN member ×
   record × place × time vs. subject); convert co-occurrences into explicit
   relationship hypotheses; feed conflicts into the Evidence Analysis workflow.
9. **Conclude or iterate** — either the indirect evidence supports a proof argument
   (hand off to Evidence Analysis / proof-argument steps), or the roster is
   re-prioritized and the cycle repeats.

Steps 1–6 are pure planning and consistent with the skill's prohibition on
unsolicited searches. Steps 7–9 follow the existing execution-gating rules unchanged.

### 3.4 New files

| File | Role | Est. size |
|---|---|---|
| `references/fan-club-guidance.md` | Full methodology: FAN roles taxonomy per record type, connection-strength rubric, correlation techniques, worked example (brick-wall parentage case), common pitfalls (surname ≠ kinship, coincidental proximity), relationship to GPS elements | ~1,800–2,200 words (in line with sibling guidance files) |
| `assets/templates/fan-club-worksheet-template.md` | Practical output document | ~350–500 words (in line with sibling templates) |

**FAN worksheet template — proposed sections:**

1. Header (subject, stalled research question, link to parent research plan, date)
2. Sources mined (checklist by record type, so exhaustiveness is auditable)
3. FAN Roster table:
   `| Name | Role/Connection | Record & Date | Place | Recurrences | Strength | Relationship Hypothesis | Priority | Status |`
4. Correlation matrix:
   `| FAN Member | [Record/Event 1] | [Record/Event 2] | … | Pattern Notes |`
5. Relationship hypotheses (numbered, each with supporting/contradicting evidence —
   mirrors the Hypothesis Testing pattern already in `research-strategies.md`)
6. Priority targets & links to their mini research plans
7. Next actions / revision history (consistent with other templates)

### 3.5 Touch-points in existing files

- `SKILL.md`: new Core Capability 5; new workflow under Procedural Guidelines; new
  trigger bullets; new example-usage pattern ("I can't find his parents…"); References
  and Templates lists updated.
- `assets/templates/research-plan-template.md`: the "Key associates/neighbors" line and
  "Strategic Approaches" section gain a pointer: *"if FAN research is warranted, open a
  FAN Club worksheet"* — one line each, no structural change.
- `references/research-strategies.md`: §1 (FAN Principle) and §2 (Cluster Genealogy)
  keep their conceptual content but end with "for the operational workflow and
  worksheet, see `references/fan-club-guidance.md`". Brick Wall strategy #4 gains the
  same pointer.
- `README.md`: capability list, structure diagram, and output-documents list gain the
  fifth capability (and get the §2.3 drift fixes).

---

## 4. Restructuring Options

Three options were evaluated. **Option B is recommended.**

### Option A — Additive only (minimal risk)

Add the two FAN files and the SKILL.md capability; fix the §2.3 drift; touch nothing
else.

- **Pros:** smallest diff; zero disruption for existing users; could ship as v1.1.0.
- **Cons:** leaves SKILL.md's internal inconsistencies (workflow detail unevenly split
  between SKILL.md and references); misses the natural moment to fix the weak
  frontmatter description; "v2" in name only.

### Option B — Consistency restructure (RECOMMENDED)

Everything in Option A, **plus** a structural tightening that makes the five
capabilities uniform without renaming any existing file:

1. **SKILL.md becomes a thinner router.** Each capability keeps: trigger conditions,
   a 5–9 step workflow summary, and pointers to its template + guidance file. Deep
   step-by-step detail that duplicates the references (e.g., the 11-step evidence
   analysis breakdown largely restates `evidence-evaluation.md`) is trimmed to
   summaries. Target: SKILL.md stays ≤ ~2,500 words *after* adding Capability 5.
   The planning-first prohibition block stays at the top, verbatim — it is the
   skill's most load-bearing text.
2. **Frontmatter description rewritten for trigger accuracy** (see §5.3) — the
   description is the only text Claude sees before deciding to load the skill, and
   the current one contains almost none of the vocabulary users actually type.
3. **No file renames.** A naming-normalization pass (e.g., `evidence-evaluation.md` →
   `evidence-analysis-guidance.md`) was considered and **rejected for v2**: it breaks
   nothing functionally but churns every cross-reference and any user notes/bookmarks,
   for purely cosmetic gain. Revisit only if v3 splits the skill.
- **Pros:** honest v2 — structure matches the documented pattern; better progressive
  disclosure (lower always-loaded token cost); better trigger reliability.
- **Cons:** larger diff to review; SKILL.md edits must be careful not to weaken the
  behavioral rules.

### Option C — Multi-skill split / plugin packaging (rejected for v2)

Split into separate skills (planning / citations / evidence-analysis) or repackage as
a plugin with slash commands.

- **Why rejected now:** total always-loaded content (SKILL.md ~2.2k words) is nowhere
  near limits; the capabilities are tightly interlinked (plans reference logs, FAN
  hands off to evidence analysis); a split would multiply installation friction for
  the Claude.ai upload audience the README targets.
- **Revisit criteria for v3:** SKILL.md summary layer exceeding ~4k words; user
  demand for standalone citation help without the planning behavior rules; or a
  marketplace/plugin distribution channel becoming the primary install path.

---

## 5. v2.0 Specification Summary (assuming Option B)

### 5.1 Deliverables

| # | Deliverable | Type |
|---|---|---|
| D1 | `references/fan-club-guidance.md` | New file |
| D2 | `assets/templates/fan-club-worksheet-template.md` | New file |
| D3 | SKILL.md: Capability 5 + FAN workflow + triggers + example | Edit |
| D4 | SKILL.md: router-style tightening of capabilities 1–4 | Edit |
| D5 | SKILL.md: frontmatter description rewrite | Edit |
| D6 | Drift fixes (§2.3: SKILL.md references list, README diagram/version) | Edit |
| D7 | Cross-reference touch-points (§3.5: plan template, research-strategies) | Edit |
| D8 | CHANGELOG.md 2.0.0 entry + RELEASE_NOTES_v2.0.0.md | New/Edit |
| D9 | Trigger-test prompt set (§5.4) | New (docs/ or CI notes) |

### 5.2 Versioning

**2.0.0.** Semver rationale: D1–D3 alone would be 1.1.0 (additive), but D4's
restructuring changes how the skill's instructions are organized and D5 changes
triggering behavior — consumers who built habits around v1 phrasing may see different
load behavior. Marketing rationale: matches the user-facing "v2" framing. Version
lives in the SKILL.md body only, per the v1.0.6 policy (frontmatter stays unversioned).

### 5.3 Draft frontmatter description (for review, not final)

> `description: Plan and organize family history and genealogy research using the
> Genealogical Proof Standard. Use when users mention ancestors, family trees,
> genealogy, census/vital/land/probate/church records, source citations (Evidence
> Explained), conflicting evidence, research logs, brick walls, or FAN club
> (Family, Associates, Neighbors) research. Creates research plans, citations,
> evidence analyses, research logs, and FAN worksheets — planning first, never
> unsolicited searches.`

### 5.4 Acceptance criteria

1. **Triggering:** a test set of ~10 prompts (5 FAN-shaped: "brick wall", "can't find
   parents", "same name", "witnesses on this deed", "where did he come from"; 5
   existing-capability controls) loads the skill and routes to the correct workflow.
2. **Planning-first invariant:** for every FAN-shaped prompt, the skill's first
   response gathers known information and produces/updates a plan or worksheet — it
   never performs a search. Execution occurs only after an explicit user request.
3. **Structural uniformity:** all five capabilities have the template + guidance +
   SKILL.md-workflow triad; SKILL.md ≤ ~2,500 words; References/Templates lists are
   complete, correctly pathed, and match the files on disk.
4. **No doc drift:** README structure diagram, capability lists, and version strings
   match reality; CHANGELOG follows Keep-a-Changelog format.
5. **Release packaging:** `release.yml` produces a zip containing the two new files
   (verify the workflow's include list — if it enumerates files rather than folders,
   it must be updated).

### 5.5 Suggested implementation phases (each a reviewable PR-sized chunk)

- **Phase 1 — Hygiene & restructure foundation:** D6 drift fixes + D4 SKILL.md
  tightening + D5 description. No new capability yet; behavior-neutral except
  triggering. *(Do the risky refactor before adding new content on top of it.)*
- **Phase 2 — FAN capability:** D1, D2, D3, D7. The heart of v2.
- **Phase 3 — Release:** D8, D9, packaging verification, tag v2.0.0.

---

## 6. Invariants (unchanged in v2 — guardrails for implementation)

1. **Planning before researching.** The prohibition on unsolicited web searches is
   preserved verbatim and applies fully to the FAN workflow (steps 1–6 are planning;
   step 7 requires explicit user request).
2. **Privacy/CRAIGEN guidance** in README and SKILL.md header is preserved; the FAN
   guidance file must repeat the living-persons caution, since FAN research is
   disproportionately likely to surface living collateral relatives.
3. **GPS and Evidence Explained** remain the governing standards; FAN outputs must
   map to GPS elements (roster → element 1; citations in roster → element 2;
   correlation matrix → element 3; hypotheses → elements 4–5).
4. **Template/guidance/workflow triad** is the structural law for any capability,
   present or future.

---

## 7. Open Questions for the Maintainer

1. **Scope confirmation:** proceed with Option B (recommended), or prefer the minimal
   Option A (ship FAN as v1.1.0, defer restructuring)?
2. **Worksheet extras:** should the FAN worksheet include an optional Mermaid
   relationship-map section (renders in Obsidian/GitHub; plain-markdown fallback), or
   stay tables-only for maximum portability?
3. **Trigger-test prompts (D9):** keep as a simple checklist in `docs/`, or wire into
   a lightweight eval (e.g., via skill-creator's eval tooling)?
4. **Release notes convention:** continue root-level `RELEASE_NOTES_vX.Y.Z.md` files,
   or move historical ones into `docs/releases/` as part of v2 housekeeping?

---

*This document is a planning artifact. No implementation has been started.*
