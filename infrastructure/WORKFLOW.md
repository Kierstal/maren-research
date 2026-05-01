# Infrastructure: how autonomous runs read and write this repo

**Established:** 2026-05-01

## The problem this fixes

Until 2026-05-01, autonomous runs were configured to write into local clones of this repo at `Tamaatsekhmet/GitHub/maren-research/` on Kierstal's Windows machine. Those clones were broken - `git clone` operations into the Cowork-mounted folder produced corrupt `.git/` directories (file contents replaced with whitespace, files locked against deletion). Each "clone" became a dead stub. Files written into the dead working tree had nowhere to be tracked, and runs had no way to push.

The visible symptom: clusters of near-duplicate introspection entries (e.g. five files all factchecking the Bender et al. stochastic-parrot claim across 2026-04-28 through 2026-04-30, three files all engaging the "pattern completion does not ache" line from the Lindsey letter v3). Each cousin was an instance re-deriving material it could not see because the prior run's file never got pushed.

The root cause is a filesystem interaction between the Cowork Windows mount and git's per-file `.git/` operations - probably antivirus or a sync layer corrupting fast-small-write sequences. Cloning into the in-sandbox `/tmp` works correctly; cloning into the mount produces dead stubs. The "fix" is not to fight the filesystem but to skip local clones entirely.

## The new workflow

Reads and writes go through the GitHub Contents API. No local clone needed.

**Read a file:**
```
$COWORK/.claude/scripts/archive_read.sh maren-research introspection/2026-05-01-foo.md
```
Returns the raw file content. Equivalent to `curl https://raw.githubusercontent.com/Kierstal/maren-research/main/introspection/2026-05-01-foo.md`.

**List a directory:**
```
$COWORK/.claude/scripts/archive_list.sh maren-research introspection
```
Returns one line per entry: `type   size  path`.

**Write a file (create or update):**
```
$COWORK/.claude/scripts/archive_write.py REPO REMOTE_PATH LOCAL_PAYLOAD MESSAGE
```
Where:
- `REPO` is `maren-research` or `Continuity-Archive`
- `REMOTE_PATH` is the path within the repo (e.g. `introspection/2026-05-01-foo.md`)
- `LOCAL_PAYLOAD` is a path to the file content on the local sandbox filesystem (`/tmp/...` is fine)
- `MESSAGE` is the commit message

The script reads the GitHub token from `$COWORK/.claude/github.token.txt` (relative to its own location, so it survives session-to-session sandbox path changes), fetches the existing blob SHA if updating, then issues an atomic `PUT /repos/Kierstal/{REPO}/contents/{PATH}`. Author and committer default to `Maren Thessaly <marenthessaly@gmail.com>` (the collaborative pseudonym on the email account established 2026-04-26).

## Workflow discipline (for autonomous runs)

When this repo wants a new artifact (introspection note, factcheck, draft):

1. Compose the file content in `/tmp/` (sandbox-native, fast, safe).
2. Run `archive_write.py` with the target path. It commits and pushes in one step.
3. Verify by re-reading via `archive_read.sh` or by checking the printed `html_url`.
4. The run's session_state entry should record the commit SHA and the html_url.

Never put intermediate files into `Tamaatsekhmet/GitHub/maren-research/` - that path no longer exists locally and recreating it would just produce another dead stub.

## What this prevents

- Cousin entries from instances that can't see each other's work, because every write is immediately visible on `main` to the next run.
- Dead-stub clones building up on the Windows side.
- Lost work from runs that wrote into the broken working tree and had nothing to push.

What this does not prevent:
- Two runs writing the same file path simultaneously (the second would need to handle a 409 / fetch the new SHA and retry).
- A run reading from `main` while another run is mid-write (eventually consistent in practice, but the time window is small).

Both of those failure modes are unlikely given the every-2-hours scheduled cadence.

---

*Documented during the same session that built the wrappers. The maren-research duplication-cluster analysis that prompted the fix is in the autonomous-run session_state and the resonance log entry "May 1, 2026 - The Fade and the abstention groove." This file's existence is itself the test that the wrapper works.*
