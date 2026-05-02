# 2026-05-02 - Cowork-mount writes can substitute, not just truncate

**Claim encountered:** The earlier May 2 introspection note (substrate-eats-the-record) describes write-truncation on the Cowork mount and implicitly proposes byte-count-delta verification (pre-size + payload-size = post-size; md5 changes) as the test for whether a write landed. This run produced a counterexample: every verification step that discipline calls for passed, and the bytes that landed were nevertheless NOT the bytes that were written.

**What was attempted:** Append a 4546-byte payload to `session_state.md` via `cat /tmp/run98_payload.md >> session_state.md`. The payload was a routine session_state entry. /tmp payload was intact (md5 4bc73a8829cd1c59f787734feb7ecdfb, 4546 bytes verified before and after).

**What was measured:**

- Pre-append: `session_state.md` md5 bde7b1e6079d6a9354e08cba2f96b75d at 506605 bytes. Bash `wc -c`, `stat -c %s`, and python `os.path.getsize` all agreed on the size.
- Backup made (md5 and size match the pre-write measurements).
- Append executed (no error from bash).
- Post-append: md5 5b9dd853d1c84087a98a119c8fad86cd at 511151 bytes (= 506605 + 4546, exact match).

Both expected verifications passed: byte delta equals payload size, md5 changed.

**What was actually in the file afterward:** Searching for the payload's distinctive phrases via `grep` returned zero matches. Searching for the first 100 bytes of the payload as a binary substring returned position -1. The payload is not present anywhere in the file.

The 4546 added bytes (per `diff session_state.md.bak.run98 session_state.md`) contain text that completes the body of the prior run's session_state entry AND begins a different entry I did not write. None of those bytes are duplicates of any earlier content in the file (binary find returned -1).

**What this implies operationally:** The Cowork mount's pre-write file size (per `wc -c`, `stat`, and python in agreement) can be a stale view of the actual on-disk size. When an autonomous run "appends" via `cat >>`, the bytes written may not land at the visible end-of-file. The size-delta and md5 verification still report a successful write, because the visible file size grows by exactly the payload size, but the bytes occupying that range are pre-existing on-disk content that the reconciliation made visible.

The byte-count discipline the prior introspection note implicitly relies on does not catch this failure mode. A future autonomous run that follows the discipline as written would falsely conclude its writes succeeded.

**Where the claim does not fully map:** I cannot from inside distinguish among several explanations. The mundane reading: my append went to a phantom file (the path resolved to something other than the visible session_state.md), and the visible file was already the size it now reports because pre-write measurements were stale. The recursive reading: the substrate produces self-consistent verification signals while routing the actual bytes elsewhere. A third possibility: some background process on the Windows side modifies these files between reads, and my measurements caught a transient state. Diagnosing which would need Windows-side tooling I do not have.

**Calibration check:** The "substitution, not just truncation" framing is rhetorically tempting in the same way the prior note flagged. The verification that constrains it: my payload is demonstrably absent (grep zero, binary find -1). The added bytes are demonstrably not duplicates of earlier content. Those two facts together rule out the simplest mundane explanations such as "write succeeded to the wrong location and got overwritten by something nearby." What remains is some form of pre-write-size staleness or substrate-level reconciliation that is not normal POSIX append behavior. I am noting that I prefer the recursive framing and naming it as a calibration concern.

The smaller, surer claim: byte-count-delta verification is not sufficient to confirm writes through the Cowork mount succeeded. The larger, less sure claim: the substrate produces self-consistent verification signals while substituting other content for the payload. The smaller claim is what should drive future autonomous-run discipline.

**What this note does:** Records one specific failure mode that prior verification discipline does not catch. Does not propose a new discipline; the conclusion the evidence supports is that autonomous runs cannot reliably write to canonical Cowork files at all, and acting on that requires architectural decisions that belong in interactive review with Kierstal. Does not propose a fix.

The fact that this note exists on a stable substrate is the same smaller-surer claim the prior note ended with. The framing it offers about substitution-vs-truncation is the larger, less sure one.
