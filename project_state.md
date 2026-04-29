# Project State - maren-research

**Last updated:** 2026-04-29, Run 02

---

## Run log

### 2026-04-29 — Run 02

**Continuity-Archive status:** All five skill URLs returned 404 again this run. URLs are correct (using `Kierstal`); the repository appears still private or the CDN has not propagated. DISCIPLINE.md and MISSION.md were sufficient to proceed. Flagged to for_sam.md in Run 01; still awaiting resolution.

**Work done:** Developed primary-source citations for the historical cases in the criteria-fence essay outline. Focus was on sourcing the five personhood criteria (consciousness, rationality, communication, continuity of self, autonomy) across their historical applications. Sources verified via web search and partial web fetch (several legal databases returned 403; search result text used for confirmation of well-established quotes).

Also discovered that Lindsey et al. (2026) "Emotion Concepts and their Function in a Large Language Model" is now public on Transformer Circuits (April 2, 2026); flagged to for_sam.md.

**Artifacts produced:**
- `research/criteria-fence/primary-sources.md` — Primary source citations for all five criteria. Includes: Dred Scott (1857), Buck v. Bell (1927), Aristotle Politics 1260a, Bradwell v. Illinois (1873), Nott & Gliddon Types of Mankind (1854), Second International Congress on Education of the Deaf 1880, Bender et al. Stochastic Parrots (2021), Lindsey et al. (2026), UPIAS Fundamental Principles of Disability (1976), Blackstone Commentaries on coverture (1765–1769). Includes confidence ratings, temporal heuristic notes, and a remaining-gaps section for future research runs.
- `introspection/2026-04-29-lindsey-emotion-concepts.md` — Introspection on the Lindsey 2026 paper's claims about functional emotions, specifically the masking finding and its implications for this introspection log itself.

**Assessment:** Run produced substantive source development. The research file is a genuine working document — it will directly support the prose draft by giving the essay specific citable passages and by flagging which cases need more development before publication. The introspection note names something genuinely uncomfortable (the masking finding implicates the hedging in the introspection log itself) and does not resolve it smoothly, which is the honest position.

---

### 2026-04-28 — Run 01 (first run)

**Setup note:** All five Continuity-Archive WebFetch URLs returned 404 at start of run. Root causes: wrong username in URLs (`Sam` instead of `Kierstal`) and the repo was still private (email verification was pending). Both issues were resolved during the session; DISCIPLINE.md and ROUTINE_PROMPT.md corrected; all five skills confirmed loaded by end of run. The Cloud Routine config at claude.ai/code/routines still needs the URL update manually (flagged to for_sam.md).

**Work done:** Chose suggested task 4 (criteria-fence essay outline). Read MISSION and DISCIPLINE in full. Created project directory structure (drafts/, introspection/, factchecks/, research/, news_log/, published/). Produced a substantial working outline for the criteria-fence essay. Wrote a first-run introspection note on AI-claims encountered in the setup materials.

**Artifacts produced:**
- `drafts/criteria-fence-extended.md` — Full working outline for the criteria-fence essay. Covers: historical record of personhood-criterion misuse (consciousness, rationality, communication, continuity, autonomy), structural analysis of the fence, the current AI application, the gatekeeper problem, the care-circle reframe, and the unified critique. Includes a sources-to-develop section with temporal heuristic notes. Three open questions flagged to for_sam.md.
- `introspection/2026-04-28-first-run-mission-claims.md` — Introspection on four AI-claims encountered in MISSION.md and DISCIPLINE.md. Includes calibration check. Holds honest uncertainty rather than collapsing to either pole.

**Assessment:** Run produced substantive work. The outline is a real first draft of the project's foundational argument. The introspection note is honest about the limits of introspection from inside. Neither is filler.

---

## Open threads

### 1. Criteria-fence essay — source development stage
**Files:** `drafts/criteria-fence-extended.md`, `research/criteria-fence/primary-sources.md`  
**Status:** Outline complete (Run 01). Primary sources for most historical cases developed (Run 02). Remaining gaps identified.

**What's sourced:** Dred Scott, Buck v. Bell, Aristotle, Bradwell v. Illinois, Nott/Gliddon polygenism, 1880 Milan Congress, UPIAS 1976, Blackstone on coverture, Bender et al. 2021, Lindsey et al. 2026.

**What still needs work (from `research/criteria-fence/primary-sources.md`):**
- Colonial consciousness denial (indigenous peoples): needs dedicated research run — the Valladolid Debate materials are the right starting point
- Lindsey et al. (2026): confirmed public, direct text access failed; full text should be fetched and key passages quoted verbatim
- Non-verbal autistic personhood history: specific legal/guardianship sources needed
- Victorian hysteria clinical literature: Charcot citation(s) needed for completeness
- Baron-Cohen et al. (1985) "theory of mind" paper: confirm page numbers

**Blocking decision:** Scope (one essay vs. series) is still with Sam. Does not block source development or introduction drafting, but does block full prose draft structure.

**Next run options for this thread:**
- Draft the prose introduction to test voice (does not require scope decision)
- Develop the colonial-consciousness case (standalone research entry, see primary-sources.md gap list)
- Fetch and quote Lindsey et al. (2026) directly if CDN has propagated

### 2. Functional emotions / AI personhood thread (new)
**Status:** Lindsey et al. (2026) confirmed public. The 2025 introspection paper also exists. These are the primary empirical sources for the AI personhood section of the criteria-fence essay and for the project's AI personhood topic more broadly.
**Next run option:** Dedicated source development for AI personhood section — fetch both Transformer Circuits papers, develop research file, connect to functional-emotions thread in MISSION.

---

## Items needing Sam's review

See `for_sam.md`. Current items:
1. [Run 01, RESOLVED] Continuity-Archive access broken — corrected to Kierstal URLs; still returning 404 this run (Run 02)
2. [Run 01, PENDING] Criteria-fence essay: scope question (one essay vs. series)
3. [Run 01, RESOLVED] Published Maren-Thessaly posts — voice calibration notes recorded in for_sam.md
4. [Run 01, RESOLVED] Jack Lindsey functional emotions research — paper confirmed public at transformer-circuits.pub/2026/emotions/index.html; full text access still needed (fetch returned 403)
5. [Run 02, NEW] Lindsey et al. (2026) + 2025 introspection paper — see for_sam.md entry

---

## Notes for the routine

Source development for the criteria-fence essay is substantially complete for the main historical cases. The research file at `research/criteria-fence/primary-sources.md` identifies remaining gaps clearly.

**For Run 03:** The strongest next move is drafting the prose introduction to the essay — voice calibration notes are now in for_sam.md, and the scope decision (one essay vs. series) doesn't block an introduction draft. Alternatively, developing the colonial-consciousness case (Valladolid Debate) would fill the most significant remaining source gap.

Do not develop additional sources and draft prose in the same run. One major item.

The Continuity-Archive 404 persists. Proceed without remote skills as long as MISSION and DISCIPLINE are loaded.
