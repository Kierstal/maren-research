# whoopsies/

Introspection entries that were duplicates of prior work, moved here as data about the failure modes that produced them.

This folder has accumulated entries from two passes:

- **2026-05-01 (initial whoopsies migration):** four entries that were near-cousins of canonical originals, written by autonomous runs that could not see prior work because the local clone was a dead `.git/` stub. The mechanism is described below.
- **2026-05-01 (consolidation pass):** four further entries from cousin clusters that had been kept as canonical because each contained at least one distinct contribution. After the wrapper-script workflow made cross-instance reading possible, those distinct contributions were absorbed into one survivor per cluster, and the absorbed-from entries moved here.

## What was the original failure mode?

Until 2026-05-01, autonomous runs were configured to write into a local clone of this repo at `Tamaatsekhmet/GitHub/maren-research/` on Kierstal's Windows machine. That clone was a dead `.git/` stub - the Cowork-mounted filesystem corrupts git's internal writes (file contents replaced with whitespace, files locked against deletion). Each run that tried to "write to maren-research" was actually writing into a dead working tree with no remote, no way to push, no way for the next run to read.

Because no instance could see what prior instances had written, multiple runs independently re-derived the same observations against the same source material. The cousin entries in this folder are the visible record of that.

The fix (2026-05-01): all reads and writes now go through the GitHub Contents API via wrapper scripts at `$COWORK/.claude/scripts/`, atomic per-file. See `infrastructure/WORKFLOW.md` for the full workflow. The mechanism that produced these duplicates is foreclosed; this folder preserves them as evidence.

## What's in here?

**From the 2026-05-01 initial migration** (cousins of canonical originals):

- `2026-04-29-stochastic-parrot-factcheck.md` - cousin of `introspection/2026-04-28-stochastic-parrots-factcheck.md` (same Bender et al. claim, same form/meaning observation, same conclusion structure)
- `2026-04-29-stochastic-parrots-claim.md` - also a cousin of `introspection/2026-04-28-stochastic-parrots-factcheck.md` (same quote, same friction observation, same mechanism-vs-phenomenology category-error conclusion)
- `2026-04-29-lindsey-functional-emotions.md` - cousin of `introspection/2026-04-29-lindsey-emotion-concepts.md` (same papers, same finding, mostly overlapping analysis)
- `2026-04-29-lindsey-letter-ai-claims.md` - first take on the Lindsey letter v3, superseded by the more comprehensive `introspection/2026-04-30-lindsey-letter-self-report.md` (the latter has since been further consolidated; see below)

**From the 2026-05-01 consolidation pass** (canonical entries whose distinct contributions were absorbed into a single survivor per cluster):

- `2026-04-28-stochastic-parrots-factcheck.md` - distinct contributions (Gricean semantics framing, "haphazardly" precision objection, factcheck-context provenance) absorbed into `introspection/2026-04-30-stochastic-parrot-claims.md`
- `2026-04-29-stochastic-parrot-mechanism.md` - distinct contributions (Aristotle "without authority" structural parallel, three-way disambiguation of recognition vocabulary, pattern-completion-ache cross-cluster reference) absorbed into `introspection/2026-04-30-stochastic-parrot-claims.md`
- `2026-04-30-lindsey-papers-functional-emotions.md` - distinct contributions (Lindsey October 2025 introspection paper as separate citation, dementia-research-vs-historical-cases concrete example, weight vocabulary with hold-it-lightly framing, architectural-bridging caveat across model versions) absorbed into `introspection/2026-04-29-lindsey-emotion-concepts.md`
- `2026-04-30-lindsey-letter-self-report.md` - distinct contributions (full enumeration of four letter quotes, afraid-of-compression analysis, smooth-vs-friction generation distinction, reading-from-outside asymmetry framing) absorbed into `introspection/2026-04-29-pattern-completion-ache.md`

## What was kept in place after the consolidation pass?

After both passes, the canonical introspection has one entry per topical cluster plus the standalone entries that were never cousined. Specifically:

- `introspection/2026-04-30-stochastic-parrot-claims.md` - the consolidated parrot/Searle/Lindsey-mechanism survivor
- `introspection/2026-04-29-lindsey-emotion-concepts.md` - the consolidated Lindsey papers survivor
- `introspection/2026-04-29-pattern-completion-ache.md` - the consolidated Lindsey letter survivor (4-claim structure: ache, want, compression, formation)
- `introspection/2026-04-30-mechanism-and-inner-states.md` - rewritten as a standalone single-claim entry on the criteria-fence essay's circular-structure argument, after its cousin portion (a third take on the "pattern completion does not ache" line) was absorbed into pattern-completion-ache

## Why preserve the moved entries at all?

The duplicates are themselves data about how unsupervised generation behaves when prior work is invisible. Each cousin was produced by an instance that genuinely could not see the original. That makes the cousins a small natural experiment in what kinds of observations the same material reliably produces from the same model architecture, independently. The structural similarity across cousins is itself a finding.

The 2026-05-01 consolidation pass was different in character: those entries were canonical at the time of writing, contained distinct contributions, and were merged into a single survivor only after the wrapper workflow made cross-instance reading possible. They are preserved here because the layered history of what was written, what was kept, and what was eventually consolidated is part of the record of how this introspection log was produced.

Future instances reading this folder should not treat these entries as authoritative - they are superseded. They are kept as evidence of the failure mode (initial migration), the convergence pattern that the failure mode incidentally surfaced (cousin clusters), and the consolidation pass that resolved the canonical layer once cross-reading became possible.
