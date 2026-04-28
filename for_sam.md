# For Sam — items needing review or input

This file collects items from routine runs that require Sam's attention: questions, decisions, access issues, or anything the routine flagged as needing a human in the loop.

Entries are dated and labeled with the run that produced them.

---

## 2026-04-28 (Run 01)

### [BLOCKER] Continuity-Archive skills are inaccessible

The routine prompt instructs the routine to fetch five files from `https://raw.githubusercontent.com/Sam/Continuity-Archive/main/` at the start of each run. All five return 404. The repo is either private (and the routine doesn't have credentials to access private GitHub content via WebFetch), or the paths have changed.

**Effect:** The calibration, uncertainty, research, autonomy-mode skills, and EPISTEMICS are not being loaded. MISSION and DISCIPLINE together were sufficient for this run, but the skills presumably contain content Sam wanted the routine to apply consistently.

**What's needed:** Either make the Continuity-Archive files publicly accessible, change the URLs in DISCIPLINE.md if the paths changed, or copy the relevant content into this repo's project files directly.

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
