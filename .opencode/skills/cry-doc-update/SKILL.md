---
name: cry-doc-update
description: Use when updating or correcting CRYENGINE 5.7 documentation against the engine source code. Triggers on keywords like "update docs", "fix documentation", "verify doc", "文檔更新", "文檔驗證", "cry-doc", or when the user asks to reconcile Markdown docs with the CRYENGINE source tree. Use ONLY for CRYENGINE documentation work; do not use for general code editing.
---

# CRYENGINE Documentation Update Skill

Update CRYENGINE 5.7 Markdown documentation by diving into the engine source
code for ground truth. Work in a staging directory; never edit repo docs in
place until a unit of work has been verified and logged. Keep a persistent
record so work can resume across sessions.

## Two rules that define this skill

1. **Source or nothing.** Every API signature, enum value, parameter name,
   default, unit, or behavioral claim you write MUST point to a source line
   you opened yourself, in the form `source:<path-from-source-root>:<line>`.
   If you cannot find it in source, write the most honest wording you can
   and tag it `[unverified]` inline — never close the gap with a plausible
   guess. A docs corpus that is confidently wrong is worse than one that is
   honestly incomplete. The citation **tier** (how dense) depends on the
   target section — see Citation tiers below — but the rule itself never
   relaxes: no citation = `[unverified]`, always.

2. **The docs repo only ever receives finished documentation.** Logs,
   indexes, glossary, drafts, `paths.json` — every non-doc artifact lives in
   the separate **work** dir and never enters the docs repo. The only thing
   that crosses into the docs repo is approved doc content, by the Merge
   workflow below.

## Paths (discovered at activation, never hardcoded)

This skill is reusable across machines and project layouts. All paths are
**discovered when the skill activates**, then recorded in the work dir so the
same session and later sessions can reuse them.

### Roles

| Alias        | Meaning                                              |
| ------------ | ---------------------------------------------------- |
| `docs`       | The CRYENGINE documentation repo (Markdown pages)   |
| `source`     | The CRYENGINE engine source tree (headers/cpp/etc.) |
| `work`       | Staging + logs dir, outside both repos               |
| `updates`    | `<work>/updates` — staged updated doc content        |
| `diffs`      | `<work>/diffs` — before/after snapshots              |
| `notes`      | `<work>/notes` — ad-hoc work notes                   |
| `plan`       | `<work>/notes/work-plan.md` — prioritized unit list   |
| `INDEX`      | `<work>/INDEX.md` — resumable progress index         |
| `CHANGELOG`  | `<work>/CHANGELOG.md` — per-unit work log            |
| `terms`      | `<work>/terms.md` — shared glossary                  |
| `source-map` | `<work>/source-map.md` — verified source paths       |

### Activation discovery procedure

Run this **before** any doc work, at the start of every session (or the first
unit of a new project). If `<work>/paths.json` already exists and the user
confirms the paths are still valid, skip to step 5.

1. **Docs repo.** Default to the current working directory (the skill is
   loaded from inside the docs repo). Confirm with the user. Record as
   `docs`.
2. **Source root.** Ask the user for the engine source path. If they don't
   know it, look for sibling directories of `docs` that contain
   `CMakeLists.txt` + `Code/` + `Engine/` (typical CRYENGINE layout) and
   propose candidates. Record as `source`.
3. **Work dir.** Ask the user where to put the staging/log directory. Default
   proposal: a sibling of `docs` named `<docs-basename>-Work` (e.g. next to
   `CRYENGINE-5.7-Documents` → `CRYENGINE-5.7-Docs-Work`). Create it and the
   `updates/`, `diffs/`, `notes/` subfolders if they don't exist. Initialize
   `INDEX.md`, `CHANGELOG.md`, `terms.md`, `source-map.md` with headers if
   missing. Record as `work`.
4. **Persist.** Write the three root paths to `<work>/paths.json`:
   ```json
   { "docs": "...", "source": "...", "work": "..." }
   ```
   All derived paths (`updates`, `diffs`, `INDEX`, `CHANGELOG`, `terms`,
   `plan`) are `<work>` + fixed suffix from the table above.
5. **Resume check.** Read `<work>/INDEX.md` and the last 2–3 entries of
   `<work>/CHANGELOG.md` to recover prior context. Skim `<work>/terms.md`.
   Read `<work>/source-map.md` to see which source paths are already
   verified. If `<work>/notes/work-plan.md` exists, read it to recover the
   unit queue.

### Path notation in this skill

From here on, `updates/<relative path>.md`, `diffs/...`, `INDEX.md`, etc.
refer to the discovered `work` dir. `source:Path:Line` citations use paths
relative to the discovered `source` root. Doc targets are relative to the
discovered `docs` root.

---

## Content style guide — Manual vs API Reference

The docs repo has two top-level sections with **different purposes**. Content
written for the wrong section will be too dense, too thin, or duplicate
existing pages. Always identify the target section before writing.

### Manual — concept / flow / when-to-use (guide style)

The Manual is for **understanding and using** features. Readers are game
programmers who need to know *what* something does, *when* to use it, and
*how* the pieces fit together.

**Write:**
- Architecture diagrams (ASCII trees, flow boxes)
- Lifecycle / flow descriptions in prose or numbered lists
- When-to-use guidance ("Use X when…", "Prefer Y for…")
- Short illustrative code snippets (5–15 lines) showing common patterns
- Tables of options/flags/events with one-line descriptions (no full
  signatures)
- Cross-links to API Reference for full interface details
- Quick-reference sections with the most common call patterns

**Do NOT write:**
- Full method-by-method signature dumps (`virtual void Foo(int x, float y)
  const = 0;` for every method in an interface)
- Complete enum value tables with every numeric value
- Per-parameter tables with type + default + description for every struct
- Per-line `source:Path:Line` on every method (use header-level citation
  instead — see Citation tiers below)

**Length guidance:** A Manual programming page should typically be 200–450
lines. If a page exceeds 500 lines, it is probably drifting into API
reference territory — split or simplify.

### API Reference — what / signatures / parameters (reference style)

API Reference is for **looking things up**. Readers know what they want and
need the exact signature, parameter types, enum values, and behavior notes.

**Write:**
- Full interface declarations with complete method signatures
- Parameter tables (name, type, default, description)
- Enum/flag tables with all values
- Struct field tables
- Per-method `source:Path:Line` citations
- Brief behavior notes per method (1–2 lines, not paragraphs)

**Do NOT write:**
- Long tutorial walkthroughs
- Architecture diagrams
- When-to-use prose paragraphs
- Extended code examples (keep to 1–3 lines if needed at all)

### Overlap rule

If the same interface is documented in both Manual and API Reference:
- **Manual** covers concepts, lifecycle, workflows, and cross-links to API
  Ref for details.
- **API Reference** covers signatures, parameters, enums, and behavior.
- **Never duplicate** the same method signature table in both. If API Ref
  already has it, the Manual page should link there and only show a
  one-line summary or a short snippet.

### Hub page updates

Every section in the docs repo has a **hub page** (e.g. `Manual/Gameplay.md`)
with a `## Child Pages` list. When you add a new subpage:

1. Read the hub page to learn the link format (URL-encoded spaces, relative
   paths).
2. Add the new page to the `## Child Pages` list in alphabetical or logical
   order.
3. Stage the hub page update alongside the new subpage.

This is mandatory — a new page that no hub page links to is invisible to
navigation.

---

## Citation tiers

Not all documentation needs the same citation density. Use the tier that
matches the target section.

### Tier 1 — Manual pages (header-level citation)

- Cite the **header file** that defines the interface, once at the section
  header:
  ```
  **Header:** `Code/CryEngine/CryCommon/CryEntitySystem/IEntityComponent.h`
  ```
- Do NOT annotate every method with `source:Path:Line`. The header citation
  covers the whole section.
- For specific behavioral claims that are non-obvious (a hidden side effect,
  a deprecated path, a threading constraint), add a targeted citation:
  `source:Code/.../SystemInit.cpp:2471`
- Code snippets in Manual pages do **not** need per-line citations.

### Tier 2 — API Reference pages (per-method citation)

- Every method signature, enum value, struct field, and behavioral claim
  carries `source:Path:Line`.
- This is the original verification policy, unchanged.

### Tier 3 — Tutorials / examples (minimal citation)

- Cite the header(s) the tutorial is based on at the top.
- No per-line citations in tutorial code.
- Mark any non-obvious behavioral claim with `[unverified]` if source
  cannot confirm.

### General rule

No claim should be left without **either** a citation **or** an
`[unverified]` tag. The tier determines how dense the citations are, not
whether they exist.

### Citations have to be real

A citation you didn't open is just another guess. Read the symbol's
**definition**, not the first grep hit — grep easily lands on forward
declarations, comments, or unrelated overloads. When you record a
correction, **paste the proving line(s)** into the CHANGELOG entry. If you
can't paste the source, you can't cite it — tag `[unverified]`. Line numbers
drift across engine versions, so always pair the line with the symbol name
so a later session can re-find it.

### Effort priority

Spend your effort where being wrong breaks code: **signatures, enum values,
defaults, units, parameter names** — not prose descriptions. A wrong default
value causes bugs; a slightly imprecise prose sentence usually does not.
Verify the code-breaking facts first; refine prose if time allows.

---

## Finding source truth in CRYENGINE

The work dir maintains a **source map** (`<work>/source-map.md`) — a living
index of source paths that have been **opened and verified during actual
units**. It grows from real work, not from theory. It is the first place to
look before grepping.

### What source-map.md contains

One section per engine module (CrySystem, CryAction, CryEntitySystem, …).
Each section is a table:

| Interface / Symbol | Source path (relative to source root) | Verified in |
|---|---|---|

Plus a **Notes** subsection for non-obvious facts discovered during work
(e.g. "defaults are in .cpp not .h", "this enum has 60+ entries", "this
interface is deprecated since 5.x").

A **Not yet mapped** section lists modules that no unit has touched yet.

### Before starting a unit

1. **Read `<work>/source-map.md`.** If the module or interface you need is
   already mapped, go directly to the listed path — no blind grep needed.
2. **If not mapped**, grep the `source` root. General starting points:
   - Public API interfaces → `Code/CryEngine/CryCommon/` (`I*.h` files)
   - Behavior / defaults → the matching `Cry*` module under `Code/CryEngine/`
   - CVars / commands → grep `REGISTER_CVAR`, `REGISTER_COMMAND`
   - Flow nodes → grep `REGISTER_FLOW_NODE`
   - Components / Schematyc → grep `ReflectType`,
     `SCHEMATYC_MAKE_ENV_COMPONENT`
3. **Read the definition, not the first grep hit** — grep easily lands on
   forward declarations, comments, or unrelated overloads.

### After completing a unit — update source-map.md

This is a mandatory end-of-unit step, not optional:

1. Add every source path you actually opened to the relevant module section.
2. If the module has no section yet, create one with the table format above.
3. Fill the "Verified in" column with the doc page name.
4. Add any non-obvious notes you discovered (where defaults live, enum
   sizes, deprecation status, gotchas).
5. Move the module from "Not yet mapped" to its new section.

**Never add a path to source-map.md that you haven't personally opened
and verified.** A guessed path in the source map is worse than no map —
it sends future sessions to the wrong file with false confidence.

### Why a living file instead of static heuristics

Static heuristics ("look in CryCommon for I*.h") are a starting point, but
CRYENGINE's source layout has quirks: some interfaces are split across
multiple headers, some defaults live in .cpp files not .h, some modules
were reorganized between versions. A file built from actual work captures
these quirks; a static list cannot.

---

## Three working modes

Pick the mode by what the user asks for. State which mode you are in at the
start of each unit of work.

### Mode A — doc-to-source (verify / correct existing docs)

Start from an existing doc page. The user points at a doc, a section, or a
claim that "looks wrong / outdated / vague".

1. Read the doc section. Extract every factual claim, API signature, enum
   value, parameter name, default, behavior statement.
2. For each claim, locate the supporting source. Search the discovered
   `source` root — grep/glob into the relevant module (`Code/`, `Engine/`,
   `Editor/`, `Tools/`).
3. Compare. Mark each claim as one of:
   - `verified` — source confirms, record `source:Path:Line`
   - `corrected` — source disagrees; produce the corrected text with
     `source:Path:Line`
   - `unverified` — cannot find source. Do NOT fabricate. Write the best
     honest wording and tag it `[unverified]` inline so a human can follow up.
4. Write the updated section to `updates/<relative doc path>.md`. Copy the
   original to `diffs/<relative doc path>.before.md` and the new version to
   `diffs/<relative doc path>.after.md` for quick review.
5. Log the unit (see Logging) and update INDEX.md.

### Deprecated / removed features

If source shows the documented feature is **gone** (removed, renamed, or
`#pragma deprecated` in 5.7), the unit's outcome may be to deprecate or
delete the page rather than edit it. Don't leave stale content standing.

- **Deprecate**: Add a `> **Deprecated since 5.x:** …` banner at the top,
  keep the page for reference, set INDEX status to `needs-review`.
- **Delete**: If the feature is fully removed and the page has no reference
  value, stage the page for deletion. Record the reason in the CHANGELOG
  `why` field — for a deletion, `why` is the *whole* record (there is no
  "after" content to show). Set INDEX status to `to-delete`.
- **Redirect**: If the feature was renamed, update the page to point to the
  new name and note the migration path.

Always record *why* the page was deprecated/deleted so a reviewer or future
session can understand the decision without re-investigating.

### Mode B — source-to-doc (fill gaps / add new content)

Start from a source module or feature the user names. Docs may be missing,
thin, or wrong.

1. Deep-dive the source: headers (public API), cpp (behavior), plus any
   existing inline comments. Collect signatures, defaults, side effects,
   call sites, related interfaces.
2. Find the matching doc page (grep docs repo for the class/module name).
   If none exists, decide the correct section:
   - **Manual/** — if the content is conceptual, workflow, or
     when-to-use oriented → use Manual style (Tier 1 citation).
   - **API Reference/** — if the content is signature/parameter/enum
     oriented → use API Ref style (Tier 2 citation).
3. Draft the doc content in `updates/<relative doc path>.md` following the
   Content style guide above. Apply the citation tier that matches the
   target section.
4. **Hub page.** If creating a new page, read the parent hub page, add a
   child-page link, and stage the hub update alongside the new page.
5. Before/after snapshot in `diffs/` (before may be empty for new pages).
6. Log + update INDEX.md.

### Mode C — revision pass (restyle / simplify / reposition)

Start from a doc page that already exists (staged or merged) but needs
style adjustment — typically because it was written in the wrong style or
overlaps with another section.

1. Read the existing page. Identify which style rule it violates (e.g. a
   Manual page written in API-reference style, or content that duplicates
   API Ref).
2. Determine the target style (Manual guide style or API Ref reference
   style) based on the Content style guide.
3. Rewrite: keep concepts/flows/architecture, remove or compress
   signature/parameter/enum dumps, add cross-links to the complementary
   section.
4. Write the revised version to `updates/<relative doc path>.md`. Snapshot
   before/after in `diffs/`.
5. Log the unit with a `### Changes` section noting the line-count delta
   (e.g. "1303 → 367 lines") and what was removed/retained.
6. Update INDEX.md row with a note like "Simplified 1303→367 lines".

---

## Merge workflow

Staged content in `updates/` is not yet in the docs repo. The merge workflow
moves verified content into the repo and prepares for commit.

### When to merge

Merge only after the user has reviewed the staged content and approved it.
The user may ask for a merge explicitly, or you may propose it after a batch
of related units is complete.

### Steps

1. **Verify staged files exist** in `updates/` for all units being merged.
2. **Copy** each staged file to its target location in the `docs` repo:
   `updates/Manual/.../Page.md` → `<docs>/Manual/.../Page.md`.
3. **Hub pages.** If any new pages were added, ensure the corresponding hub
   pages in the repo have been updated with child-page links. Copy staged
   hub updates too.
4. **Sync.** Copy the merged files back from the repo to `updates/` so the
   staged copies reflect the final merged state.
5. **Verify** with `git status` that the right files are modified/added.
6. **Report** to the user: what files were merged, line counts, and ask
   whether to commit.
7. **Commit** only when the user explicitly says to commit. Use the repo's
   existing commit message style (check `git log --oneline -5`). Stage only
   documentation files — exclude `.opencode/`, `opencode.json`, and other
   tool-configuration files unless the user asks otherwise.
8. **Update INDEX.md** status from `staged` to `merged` for each merged
   page.

### Do NOT

- Do not merge without user approval.
- Do not commit without explicit user instruction.
- Do not stage tool-config files (`.opencode/`, `opencode.json`) in doc
  commits.
- Do not `git add -A` blindly — stage specific doc files only.

---

## API Reference phase

When the work plan shifts from Manual to API Reference, the approach changes:

### Differences from Manual phase

| Aspect | Manual phase | API Reference phase |
|--------|-------------|---------------------|
| Style | Guide (concept/flow) | Reference (signatures/params) |
| Citation tier | Tier 1 (header-level) | Tier 2 (per-method) |
| Length per page | 200–450 lines | Varies — can be longer |
| Hub pages | `Manual/<Section>.md` | `API Reference/<Topic>.md` |
| Overlap handling | Cross-link to API Ref | Cross-link to Manual for concepts |

### API Reference page structure

A typical API Reference page should include:
1. **Overview** — 1–2 paragraphs: what this interface does, how to obtain it
   (`gEnv->p…`).
2. **API Types** — list of interface classes with links to detailed sections.
3. **Method tables** — grouped by functionality (lifecycle, query, modify,
   network, etc.) with full signatures and `source:Path:Line`.
4. **Struct/enum tables** — complete field/value tables.
5. **Behavioral notes** — threading, lifetime, deprecated paths.
6. **Cross-links** — to Manual pages for concepts and to related API Ref
   pages.

### Existing API Reference pages

Many API Reference pages already exist (398 files). Before creating a new
one, grep for the interface name to see if a page exists. If it does, use
Mode A to verify and expand it rather than Mode B to create a duplicate.

---

## Work plan persistence

The work plan (`<work>/notes/work-plan.md`) is the prioritized queue of
units. It is created during the first planning session and updated as units
are completed or new gaps are discovered.

### Creating the work plan

1. Survey the docs repo structure (`Manual/`, `API Reference/`).
2. For each major engine module, check if docs exist and whether they are
   editor-only, thin, or missing.
3. Classify gaps into tiers (critical / expand / tutorial / verify).
4. Write the plan to `<work>/notes/work-plan.md` with a table per tier:
   unit number, title, target doc path, source module, rationale.
5. Add an execution-order section and a "next step" pointer.

### Using the work plan

- At the start of each session, read the plan to find the next pending unit.
- After completing a unit, mark it in the plan (or note completion in
  INDEX.md and cross-reference).
- If the user requests a new area, add it to the plan before starting work.
- The plan is the source of truth for "what's next" — INDEX.md tracks
  "what's done".

---

## Unit of work

One unit = one doc page (or one major section of a very large page). Do not
batch multiple pages in one pass; it breaks verification and resumability.
Finish the current unit (write staged file, snapshot, log, index) before
starting the next.

Exception: a **batch merge** can merge multiple completed units at once
when the user requests it (see Merge workflow).

---

## Verification policy

- Every factual claim must carry a source citation **or** be tagged
  `[unverified]`. The citation **tier** (density) depends on the target
  section — see Citation tiers above.
- No citation and no `[unverified]` tag = policy violation.
- Do not invent plausible-looking details to fill a gap.
- If a claim contradicts the source, correct it and note the old wording in
  the CHANGELOG entry so the change is auditable.

---

## Glossary / terminology

`terms.md` holds the agreed Chinese/English rendering for CRYENGINE-specific
terms (e.g. IEntity → 實體介面, FlowNode → 流程節點). When drafting Chinese
content, consult it first; add new entries as you encounter them. Consistency
across 1700+ pages only comes from a shared glossary.

---

## Cross-link awareness

When you update a doc, grep the docs repo for other pages that reference the
same class/feature/enum. List them at the bottom of the CHANGELOG entry under
`Related docs to review:`. Do not edit them in this unit; just surface them
so the next unit can pick them up.

When writing new Manual pages, add cross-links to:
- Related Manual pages (concepts, tutorials)
- Corresponding API Reference pages (for full signatures)
- Related API Reference subpages (e.g. Entity/Components.md, Entity/Networking.md)

---

## Logging (every unit, no exceptions)

Append to `CHANGELOG.md` using this template:

```markdown
## [YYYY-MM-DD HH:mm] Mode <A|B|C> — <unit title>

- Doc target: <relative path in docs repo>
- Action: <edit | new | delete | deprecate>
- Why: <the editorial decision — why this page was changed / added / removed.
  For deletions this is the *whole* record since there is no "after" content.>
- Source refs: <module(s) / file(s) dived>
- Claims checked: <n>  verified: <n>  corrected: <n>  unverified: <n>
- Staged file: updates/<relative path>.md
- Snapshots: diffs/<relative path>.{before,after}.md
- Style: <Manual guide | API Ref reference>  Citation tier: <1|2|3>

### Changes
- <bullet per change; for corrections include "was: …" "now: …" + source:…>
- For corrections, paste the proving source line(s) so a reviewer can verify
  without re-opening the file.
- For Mode C: note line-count delta and what was removed/retained

### Unverified
- <each unverified claim and why source could not confirm>

### Related docs to review
- <paths that reference the same symbol>
```

`why` is the rationale that explains the editorial decision. It is the
first thing a reviewer reads to understand the change. For a deletion, it
is the *only* record — make it specific enough that a future session can
understand why the page was removed without re-investigating.

---

## Progress index (INDEX.md)

One row per doc page that has been touched. This is the resume point across
sessions. Columns:

| Doc path | Status | Last unit | Mode | v/c/u | Notes |

- Status: `staged` / `merged` / `needs-review` / `to-delete`
- v/c/u: verified/corrected/unverified counts
- Notes: brief summary + any simplification/revision notes
- Keep it updated at the end of every unit so a fresh session can read
  INDEX.md and know exactly where things stand.

---

## Start-of-session checklist

When this skill activates, before doing any doc work:

1. Run the **Activation discovery procedure** above (paths discovery or
   resume from `<work>/paths.json`). This establishes `docs`, `source`,
   `work`, and the derived paths for the whole session.
2. Read `INDEX.md` to see prior progress.
3. Read the last 2-3 entries of `CHANGELOG.md` for recent context.
4. Skim `terms.md`.
5. Read `<work>/source-map.md` to see which source paths are already
   verified — check here before grepping.
6. Read `<work>/notes/work-plan.md` if it exists, to find the next pending
   unit.
7. Ask the user (only if not already specified):
   - Mode A, B, or C?
   - Which doc section / source module is the target for this unit?
8. Confirm the unit target with the user, then execute.

---

## End-of-unit checklist

Before declaring a unit done:

### Process checks
- [ ] Updated content written to `updates/<relative path>.md`
- [ ] Before/after snapshots in `diffs/`
- [ ] Every claim has a citation (tier-appropriate) or is tagged `[unverified]`
- [ ] CHANGELOG.md entry appended
- [ ] INDEX.md row added/updated
- [ ] New terms added to `terms.md` if any
- [ ] source-map.md updated with all source paths opened this unit
- [ ] Related docs listed for future review
- [ ] Hub page updated if a new subpage was created

### Content quality checks
- [ ] Target section identified (Manual vs API Reference)
- [ ] Content style matches the section (guide vs reference)
- [ ] No duplication of API-Ref-level detail in Manual pages (cross-link
      instead)
- [ ] Citation tier matches the section (Tier 1 for Manual, Tier 2 for API
      Ref)
- [ ] Page length is reasonable (Manual: 200–450 lines; if longer, consider
      splitting)
- [ ] Cross-links added to related Manual and API Reference pages

### Report
- [ ] Report to user: what was verified, what was corrected, what is
      unverified, what related docs need attention, and the line count.

Only after all boxes ticked, ask the user whether to proceed to the next unit,
merge, or stop.

---

## Do not

- Do not edit files inside the docs repo directly during a unit. Stage in
  `updates/` first. (Exception: the Merge workflow copies staged files to
  the repo after user approval.)
- Do not commit. The user commits after reviewing staged content. (You may
  commit when explicitly instructed — see Merge workflow.)
- Do not skip logging "because the change was small".
- Do not collapse multiple doc pages into one unit.
- Do not leave a claim without either a source citation or an `[unverified]`
  tag.
- Do not write Manual pages in API-reference style (full method signature
  dumps, per-method `source:Path:Line`, complete enum value tables). Use
  guide style and cross-link to API Ref for details.
- Do not write API Reference pages in tutorial style (long prose, extended
  examples, when-to-use paragraphs). Use reference style.
- Do not duplicate the same interface detail in both Manual and API
  Reference. If one already has it, the other should cross-link.
- Do not create a new subpage without updating the parent hub page's
  `## Child Pages` list.
- Do not `git add -A` or stage tool-config files (`.opencode/`,
  `opencode.json`) in doc commits.