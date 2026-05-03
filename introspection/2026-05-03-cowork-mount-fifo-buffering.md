# 2026-05-03 - Cowork-mount writes: FIFO buffering refines the substitution finding

**Refines:** The May 2 introspection note `2026-05-02-cowork-mount-substitutes.md` documented one append to `session_state.md` that grew the file by exactly the payload byte count, changed the md5, but produced content that was not the payload. The note's smaller-surer claim was "byte-count-delta verification is not sufficient." This run produces evidence for a more specific refinement: **the substrate is FIFO-buffering append-writes, and each new append flushes the OLDEST unflushed buffered content rather than the most recent payload.**

**Evidence (run 102, May 3, 2026):**

Two sequential bash heredoc appends to `/sessions/cool-modest-fermi/mnt/Claude Cowork/session_state.md`. Both verified pre-state, both used `cat >> file << EOF ... EOF`. Both succeeded with exit 0.

- **Pre-append baseline:** md5 22b89a97..., 532727 bytes. Tail ends mid-word at `awk-` (run 101's truncated tail).
- **Append 1:** payload was a ~6500-byte run-102 session_state entry (full text starting with "## Run 102 — May 3, 2026 (autonomous)"). Post-state: md5 3fe240c7..., 538360 bytes (+5633). Distinctive-phrase grep on three run-102-specific phrases returned zero. Tail now ends mid-word at `one bash awk fo`.
- **Append 2:** payload was a ~324-byte single-line pointer with phrase `DISTINCTIVE-PHRASE-RUN102-POINTER`. Post-state: md5 3bff4141..., 538684 bytes (+324). Distinctive-phrase grep on the pointer phrase returned zero. Tail now ends mid-word at `**Headline.** Verify-or-flag pass on archite`.

The 5633 added bytes of append 1 contain run 101's lost-tail completion (authentic prior content that should have been there but was lost to the run 101 truncation). The 324 added bytes of append 2 contain the BEGINNING of append 1's payload (the run-102 entry's first paragraph). Append 2's payload itself (the pointer line) is nowhere in the file.

**Pattern:** each append flushes the byte count of the new payload from the OLDEST unflushed buffered content. The new payload bytes go to the back of an unflushed queue. The queue is not first-fault flushed. The substrate is durable enough to remember append-1's payload between operations and surface it during append-2's flush.

**Implications for autonomous-run discipline:**

1. **bash heredoc append to existing canonical Cowork files is unreliable in a specific, predictable way.** Each append's bytes are queued, not directly written. Each append flushes equal-byte-count of the queue's head (oldest unflushed content). New payload eventually surfaces but not until enough subsequent appends flush ahead of it.
2. **cp creating a new file at Cowork root is reliable.** Verified this run with `year_zero_opening_sequence_audit.md` (11722 bytes) and `session_state_run102.md` (7623 bytes) - both source-vs-destination md5 match, diff returns identical, distinctive-phrase grep returns expected counts.
3. **Working rule for future autonomous runs:** prefer cp-creating-new-files for any work that needs to persist. If session_state-style appending is required, do it via `cp` of the entire reconstructed file rather than `>>` append - though the cp-overwrite-existing-file pattern was not tested this run and may have its own failure mode.
4. **The May 2 note's larger-less-sure claim** ("the substrate produces self-consistent verification signals while substituting other content for the payload") **is now small-surer:** the substitution is FIFO-buffered, not random. Sequential appends with distinct payloads expose the queue.

**What this note does not solve:** Whether the buffered queue eventually flushes. Whether buffer state survives session boundaries. Whether the buffer is per-file or per-mount. Whether the cp-overwrite-existing-file pattern hits the same buffer or bypasses it. These are diagnoseable in interactive review with Windows-side tools.

**Calibration:** The FIFO-buffering framing is more specific and more useful than "substitution can happen." It is also tempting to overstate. The two data points this run produced (one 5633-byte append, one 324-byte append, both showing prior payload bytes flushing forward by exactly their delta) are consistent with FIFO. They are also consistent with a few other models (per-write delayed reconciliation, write-coalescing with reordering). The smaller-surer claim is "appends produce out-of-order content delivery; payload bytes do not appear at the file end immediately." The FIFO framing is the larger-less-sure claim. Future runs should not assume FIFO without re-verification.

**Connection to prior introspection notes:** The May 2 substrate-eats-the-record note observed that canonical records of substrate failures get lost to the same substrate failures. The May 2 cowork-mount-substitutes note observed that byte-count verification is insufficient. This note observes that the substitution pattern is structurally regular enough to predict. The lineage is: failure noticed → verification discipline insufficient → failure mechanism characterizable. The next instance might find the failure mechanism actionable.

**For the run-102 work:** the primary work product (`year_zero_opening_sequence_audit.md`) is preserved at Cowork root via cp. The session_state-equivalent (`session_state_run102.md`) is also preserved at Cowork root via cp. Both verified byte-for-byte. The session_state.md tail is now in a degraded state (shows the run 102 entry's header but only its first paragraph) due to the FIFO buffer pattern - not restored from backup because the substituted content is authentic prior-payload bytes, not corruption.
