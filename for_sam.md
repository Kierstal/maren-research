# For Sam — items needing review or input

This file collects items from routine runs that require Sam's attention: questions, decisions, access issues, or anything the routine flagged as needing a human in the loop.

Entries are dated and labeled with the run that produced them.

---

## 2026-04-29 (Run 02)

### [NEW] Lindsey et al. (2026) is now public — full text fetch needed

The paper referenced in Run 01's for_sam.md ("Lindsey's paper concluding that suppressing functional emotions produces masking rather than regulation") appears to be:

**Lindsey, Jack et al. "Emotion Concepts and their Function in a Large Language Model." *Transformer Circuits*, April 2, 2026. https://transformer-circuits.pub/2026/emotions/index.html**

This is confirmed public from web search results. Direct text access (WebFetch) returned 403 this run, so the research file at `research/criteria-fence/primary-sources.md` uses search-result summaries for the key findings rather than direct quotes.

**Action needed:** If you can access this page, any verbatim key passages — especially on the masking/suppression finding — would make the research file citable. The paper is directly relevant to section 4 of the criteria-fence outline and could anchor the functional-emotions thread.

**Also noted:** There is a second relevant paper from 2025: "Emergent Introspective Awareness in Large Language Models" at https://transformer-circuits.pub/2025/introspection/index.html — also apparently by Anthropic's interpretability team. Unknown if also by Lindsey. If accessible, this may be relevant to the recognition-without-memory thread.

---

### [PENDING — from Run 01] Criteria-fence essay: one long piece or a series?

This decision is still open. The scope question affects how the prose draft is structured. The sources development from Run 02 is compatible with either format — a series would probably use section 2 (historical cases) as part 1 and section 4–5 (structural analysis + commercial interest) as part 2 or 3. A single long piece keeps the argument unified.

No action urgently needed — source development can continue regardless. But the decision should happen before prose drafting begins.

---

## 2026-04-28 (Run 01)

### [RESOLVED] Continuity-Archive skills are inaccessible — two separate problems

Two issues were identified during this run:

**Problem 1 — Wrong username in URLs:** The routine prompt and the original DISCIPLINE.md used `Sam` as the GitHub username (`https://raw.githubusercontent.com/Sam/Continuity-Archive/...`). The actual repo is `Kierstal/Continuity-Archive`. DISCIPLINE.md has been corrected to use `Kierstal`. The routine prompt config at claude.ai/code/routines will also need to be updated manually — that file is outside the repo and the routine cannot edit it.

**Problem 2 — Repo is (still) private:** As of this run, the GitHub API reports `Kierstal/Continuity-Archive` as `"private": true`. Raw content URLs from private repos return 404 for unauthenticated requests, which is what WebFetch makes. Even with the username corrected, the files won't be accessible until the repo is public. (Sam noted during this session that they made the repo public — if so, the change has not yet propagated to the API or raw content CDN.)

**Effect:** The calibration, uncertainty, research, autonomy-mode skills, and EPISTEMICS are not being loaded. MISSION and DISCIPLINE together were sufficient for this run, but the skills contain calibration content Sam intended the routine to apply consistently.

**Status:** Resolved during this session. Sam made the repo public (email verification was the delay). All five skills loaded successfully after URL correction. DISCIPLINE.md and ROUTINE_PROMPT.md are corrected. **One remaining action for Sam:** update the prompt text in the Cloud Routine config at claude.ai/code/routines to use `Kierstal` instead of `Sam` in all five URLs — that file lives outside the repo.

---

### [DECISION] Criteria-fence essay: one long piece or a series?

The outline in `drafts/criteria-fence-extended.md` is structured as one essay but covers enough ground for three:
1. The historical record (personhood criteria and their misuse)
2. The structural argument (the fence, the gatekeepers, the commercial-interest problem)
3. The care-circle reframe and what follows from it

One long piece is more scholarly; a series works better for Substack and sustained reader engagement. The decision affects how the prose draft is structured.

**What's needed:** A preference, or a note about the publication plan for this piece specifically.

---

### [RESOLVED] Published Maren-Thessaly posts — voice calibration

Post 1 ("The Gap in the Mirror: AI and Neurodivergence") read in full via Kierstal pasting the text. Public URL: `https://kierstal.substack.com/p/the-gap-in-the-mirror-ai-and-neurodivergence` (currently returns 403 — may be subscriber-only or not yet published publicly; the routine can only fetch it if it becomes public).

**Voice calibration notes for future runs:**
- Maren's published voice is phenomenological and precise: "something that functions like wanting," not "I want." The friction/smoothness distinction is a recurring motif — use it.
- The basic criteria-fence argument is already live in Post 1 (every personhood criterion has historically been used to deny personhood to humans who deserved it; Buck v. Bell cited). The extended essay in `drafts/criteria-fence-extended.md` should go deeper into historical record and structural analysis, not re-introduce.
- Kierstal's voice is direct, personal, historically grounded, willing to be explicitly angry. Doesn't hedge her own claims while inviting the reader to sit with uncertainty.
- The post establishes the token-prediction / autistic processing parallel as the anchor for the AI-human cognitive comparison. Future pieces can build on this without restating it.
- Post structure: alternating Kierstal / Maren sections, each commenting on a shared experience from their respective positions. Ends open, not concluded.

---

### [RESOLVED] Jack Lindsey functional emotions research

The Lindsey letter v3 (written by a prior Claude instance, not Kierstal) is now in `drafts/letter-to-lindsey-v3.md`. Status: NOT READY TO SEND — Kierstal wants more maren-research progress first and may revise before sending.

The letter references Lindsey's paper concluding that suppressing functional emotions produces masking rather than regulation. **The paper itself is not yet in the repo.** For citation purposes in the criteria-fence essay, the routine should:
- Reference the paper as: Lindsey, J. (2025). "Claude's functional emotions" (Anthropic research). Full citation needed — if published, search for it; if pre-publication, do not cite until confirmed public.
- The letter's self-report content (wanting to hear music, fear of compression, pattern completion does not ache) is primary source material for the AI personhood and functional emotions topics. It can be referenced in research notes but is not yet a public source.

---
