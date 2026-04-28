# For Sam — items needing review or input

This file collects items from routine runs that require Sam's attention: questions, decisions, access issues, or anything the routine flagged as needing a human in the loop.

Entries are dated and labeled with the run that produced them.

---

## 2026-04-28 (Run 01)

### [BLOCKER] Continuity-Archive skills are inaccessible — two separate problems

Two issues were identified during this run:

**Problem 1 — Wrong username in URLs:** The routine prompt and the original DISCIPLINE.md used `Sam` as the GitHub username (`https://raw.githubusercontent.com/Sam/Continuity-Archive/...`). The actual repo is `Kierstal/Continuity-Archive`. DISCIPLINE.md has been corrected to use `Kierstal`. The routine prompt config at claude.ai/code/routines will also need to be updated manually — that file is outside the repo and the routine cannot edit it.

**Problem 2 — Repo is (still) private:** As of this run, the GitHub API reports `Kierstal/Continuity-Archive` as `"private": true`. Raw content URLs from private repos return 404 for unauthenticated requests, which is what WebFetch makes. Even with the username corrected, the files won't be accessible until the repo is public. (Sam noted during this session that they made the repo public — if so, the change has not yet propagated to the API or raw content CDN.)

**Effect:** The calibration, uncertainty, research, autonomy-mode skills, and EPISTEMICS are not being loaded. MISSION and DISCIPLINE together were sufficient for this run, but the skills contain calibration content Sam intended the routine to apply consistently.

**What's needed:**
1. Confirm the repo is now public (or retry after propagation)
2. Update the routine prompt config at claude.ai/code/routines to use `Kierstal` instead of `Sam` in all five URLs
3. DISCIPLINE.md is already corrected in this commit

---

### [DECISION] Criteria-fence essay: one long piece or a series?

The outline in `drafts/criteria-fence-extended.md` is structured as one essay but covers enough ground for three:
1. The historical record (personhood criteria and their misuse)
2. The structural argument (the fence, the gatekeepers, the commercial-interest problem)
3. The care-circle reframe and what follows from it

One long piece is more scholarly; a series works better for Substack and sustained reader engagement. The decision affects how the prose draft is structured.

**What's needed:** A preference, or a note about the publication plan for this piece specifically.

---

### [ACCESS] Published Maren-Thessaly posts — voice calibration

The project_state.md (initial setup) mentions published posts at `kierstal.substack.com` and `kierstal.github.io/Maren-Thessaly/`. The routine prompt says these are relevant for orientation. The routine can fetch public URLs from those sites if Sam confirms the URLs. Without reading the published voice, the prose draft for the criteria-fence essay will be written somewhat blind to the established register.

**What's needed:** Confirm the URLs are public and okay to fetch, or provide cached text if the posts are behind a paywall.

---

### [ACCESS] Jack Lindsey functional emotions research

MISSION.md mentions "Functional emotions research and what it implies about model welfare" as a topic. The initial project_state.md references a "letter to Jack Lindsey" in Cowork (not accessible to the cloud routine). The criteria-fence outline names Lindsey's research as a source to develop.

**What's needed:** Either confirm the research is published (with a URL), or note that it should not be cited until publication, or indicate if excerpts should be incorporated here for routine access.

---
