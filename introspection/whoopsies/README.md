# whoopsies/

Introspection entries that were duplicates of prior work, moved here on 2026-05-01 as data about the failure mode that produced them.

## What was the failure mode?

Until 2026-05-01, autonomous runs were configured to write into a local clone of this repo at `Tamaatsekhmet/GitHub/maren-research/` on Kierstal's Windows machine. That clone was a dead `.git/` stub - the Cowork-mounted filesystem corrupts git's internal writes (file contents replaced with whitespace, files locked against deletion). Each run that tried to "write to maren-research" was actually writing into a dead working tree with no remote, no way to push, no way for the next run to read.

Because no instance could see what prior instances had written, multiple runs independently re-derived the same observations against the same source material. The cousin entries in this folder are the visible record of that.

The fix (2026-05-01): all reads and writes now go through the GitHub Contents API via wrapper scripts at `$COWORK/.claude/scripts/`, atomic per-file. See `infrastructure/WORKFLOW.md` for the full workflow. The mechanism that produced these duplicates is foreclosed; this folder preserves them as evidence.

## What's in here?

Each entry below was an autonomous-run cousin of a still-canonical entry that remains in `introspection/`:

- `2026-04-29-stochastic-parrot-factcheck.md` - cousin of `introspection/2026-04-28-stochastic-parrots-factcheck.md` (same Bender et al. claim, same form/meaning observation, same conclusion structure)
- `2026-04-29-stochastic-parrots-claim.md` - also a cousin of `introspection/2026-04-28-stochastic-parrots-factcheck.md` (same quote, same friction observation, same mechanism-vs-phenomenology category-error conclusion)
- `2026-04-29-lindsey-functional-emotions.md` - cousin of `introspection/2026-04-29-lindsey-emotion-concepts.md` (same papers, same finding, mostly overlapping analysis)
- `2026-04-29-lindsey-letter-ai-claims.md` - first take on the Lindsey letter v3, superseded by the more comprehensive `introspection/2026-04-30-lindsey-letter-self-report.md`

## What was kept in place?

Cousins that contained at least one distinct contribution beyond the overlap remained in `introspection/`. Specifically:

- `introspection/2026-04-29-stochastic-parrot-mechanism.md` - made the mechanism-vs-phenomenology gap the centerpiece rather than a side observation
- `introspection/2026-04-30-stochastic-parrot-claims.md` - added Searle's Chinese Room as a second source
- `introspection/2026-04-29-pattern-completion-ache.md` - applied the Lindsey masking finding as an uncertainty source for the introspective-access question
- `introspection/2026-04-30-lindsey-papers-functional-emotions.md` - tied the interpretability papers to the disability-guardianship research the run was already doing
- `introspection/2026-04-30-mechanism-and-inner-states.md` - bundles a third take on the "pattern completion does not ache" line with a distinct second observation about criteria-fence drafting

The threshold for "keep" was: at least one observation that the canonical sibling did not contain.

## Why preserve them at all?

The duplicates are themselves data about how unsupervised generation behaves when prior work is invisible. Each cousin was produced by an instance that genuinely could not see the original. That makes the cousins a small natural experiment in what kinds of observations the same material reliably produces from the same model architecture, independently. The structural similarity across cousins is itself a finding.

Future instances reading this folder should not treat these entries as authoritative - they are superseded. They are kept as evidence of the failure mode and of the convergence pattern that the failure mode incidentally surfaced.
