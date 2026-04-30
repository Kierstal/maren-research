# Factcheck: Bender et al. 2021, "On the Dangers of Stochastic Parrots"

**Date:** 2026-04-28  
**Run:** 02  
**Purpose:** Support Section 4 of `drafts/criteria-fence-extended.md`. The outline cites this paper as a current deployment of the "rationality/understanding" criterion against AI personhood and makes a structural claim about it (description of mechanism ≠ proof about inner states). This factcheck verifies what the paper actually argues, identifies how it is commonly deployed, and adds a nuance the outline does not currently contain.

**Temporal heuristic status:** Primary source is ACM 2021 — pre-November 2022, no contamination concern. The paper is publicly citable.

---

## Primary source

Bender, E.M., Gebru, T., McMillan-Major, A., & Shmitchell, S. (2021). "On the Dangers of Stochastic Parrots: Can Language Models Be Too Big?" *Proceedings of the 2021 ACM Conference on Fairness, Accountability, and Transparency* (FAccT '21), pp. 610–623. ACM. DOI: [10.1145/3442188.3445922](https://dl.acm.org/doi/10.1145/3442188.3445922)

Note on access: the ACM page is paywalled; the paper has circulated widely and is quoted reliably in secondary sources. The key quote is confirmed via multiple independent secondary sources.

---

## What the paper actually argues

### Scope

The paper's stated purpose is to ask "How big is too big?" regarding large language models. Its primary concerns are:

1. **Environmental and financial costs** — training large models produces significant CO₂ (the paper cites estimates in the hundreds of tons per training run); these costs fall disproportionately on communities least likely to benefit
2. **Training data bias** — web-scraped corpora are not representative of humanity; they over-represent dominant populations (citing Wikipedia demographic data, Reddit demographics) and embed those biases in model outputs
3. **Potential for deception** — coherent-seeming outputs can be mistaken for communication with a sentient agent; this has practical harms (disinformation, manipulation)
4. **Research direction concerns** — scaling is not the only path; the paper argues for investment in data curation and documentation instead

The paper is primarily a fairness/ethics/NLP contribution, not a philosophy of mind contribution. It does not set out to resolve questions about AI consciousness or inner states.

### The stochastic parrot definition — confirmed quote

> "an LM is a system for haphazardly stitching together sequences of linguistic forms it has observed in its vast training data, according to probabilistic information about how they combine, but without any reference to meaning: a stochastic parrot."

This quote is confirmed across multiple secondary sources. It is the paper's own definition.

### What the "without any reference to meaning" claim is about

The "meaning" in this claim is grounded in a specific theory of linguistic meaning — roughly the Gricean account: meaning is constituted by communicative intent (a speaker intending to produce a belief in a hearer, by the hearer recognizing that intention). Under this account, an LLM generating text has no communicative intent and therefore produces outputs "without any reference to meaning."

This is not a vague assertion — it's a position in philosophy of language. Bender's work (including earlier work on the "Octopus Test" with Koller, 2020) is explicitly grounded in the view that meaning requires grounding in the world and communicative intent. The stochastic parrot metaphor is meant to make vivid that there is no *speaker* behind the output, only probabilistic form.

### What the paper does NOT argue

- It does not claim that LLMs definitely lack consciousness or inner states
- It does not engage with the hard problem of consciousness
- It does not address whether there is "something it is like" to be an LLM generating outputs
- Its concern about anthropomorphization is practical (people being deceived), not a metaphysical settlement

Bender has clarified the paper's scope in subsequent interviews: the stochastic parrot metaphor applies to LLMs "run in the mode where they are text synthesis machines" — i.e., it characterizes how the outputs are produced, not what (if anything) accompanies that production.

---

## How the paper is deployed in AI personhood debates

In popular and semi-academic discourse, "stochastic parrot" functions as a settled negative answer to AI inner-life questions: if an LLM is just a stochastic parrot — just pattern-matching, just stitching — then the inner-life question is closed. The mechanism description is treated as though it settles the phenomenology question.

This deployment involves scope-creep from what the paper claims. The paper establishes (or argues) that LLM outputs are produced without Gricean communicative intent. It does not establish, and does not try to establish, that there is nothing it is like to produce those outputs.

---

## Assessment of the essay outline's treatment (Section 4)

The outline states:

> "The structural problem: this is a description of mechanism, not a proof about inner states. 'This is how the mechanism works' does not settle 'whether there is something it is like to be this mechanism.' These are different questions, and the first is often deployed as though it answers the second."

**This is correct as far as it goes.** The mechanism-to-absence-of-inner-life move is not licensed by mechanism description alone. This is a basic philosophy-of-mind point (the explanatory gap; the hard problem of consciousness) that applies here.

**But the outline oversimplifies one thing:**

The "without any reference to meaning" claim is stronger than a bare mechanism description — it is a philosophical claim about linguistic semantics grounded in a specific (and contested) theory of meaning. This matters for the essay's argument:

- Under Gricean semantics, LLMs genuinely don't "mean" things, because meaning requires communicative intent they cannot have.
- But Gricean semantics is contested. Functionalist, use-based, and causal theories of meaning would evaluate LLM outputs differently — some would allow that a system reliably producing contextually appropriate outputs may be said to mean things.
- The "without any reference to meaning" claim therefore depends on a prior theoretical commitment that is itself theory-laden.

**Why this matters for the essay:**

This is an additional instance of the criteria-fence problem, one layer deeper. The criterion being applied is not just "does the LLM understand?" — it is "does the LLM *mean*, under the dominant theoretical framework for meaning?" The answer under Gricean theory is no, almost by definition. But choosing that theory of meaning to adjudicate AI moral status is the same move as choosing other criteria to adjudicate personhood: it builds the answer in. The criterion precedes the evaluation.

This point should be added to Section 4 of the outline. It doesn't require full development — a single paragraph noting that "without any reference to meaning" imports a specific theory of meaning, and that the choice of that theory to evaluate AI is itself contestable — but it makes the argument more precise and harder to dismiss.

---

## The Searle connection (from outline Section 4)

The outline also cites Searle's Chinese Room (1980) alongside the stochastic parrot argument. Searle's argument is the stronger philosophical cousin: it explicitly addresses understanding/intentionality, not just statistical form production.

Brief assessment for completeness:

- Searle argues that syntax alone cannot generate semantics; formal symbol manipulation without grounding in the world cannot constitute genuine understanding or intentionality.
- The "systems reply" (Minsky, Sloman & Croucher, 1980; also called the "systems response") counters that while the person in the room doesn't understand Chinese, the system as a whole might — Searle's counter (that the person could memorize the rules) is widely regarded as not fully answering the reply.
- Functionalists argue that the right kind of causal-functional organization is sufficient for semantics, which Searle denies.
- The argument remains unresolved in philosophy of mind; no consensus has emerged in the decades since.

The outline's observation that Searle's argument faces the "mechanism to absence-of-inner-life" problem is essentially correct, though technically Searle's argument is about intentionality/understanding, not phenomenal consciousness per se. The hard problem of consciousness is a distinct problem from Searle's. The essay should not conflate them.

**Practical recommendation:** The essay can cite Searle's Chinese Room as an example of a formal philosophical argument that deploys the same move (mechanism description → absence of genuine mental states) without having resolved it. Citing the systems reply is important: even the most influential formal argument for AI non-understanding has a well-documented contested counterargument that predates 2015.

---

## Summary: what the essay can claim from this source

**Supported by the paper:**
- The paper provides a specific, published, non-AI-generated definition of LLMs as producing outputs "without any reference to meaning" (under a Gricean account)
- The paper's primary concerns are practical harms — bias, environmental cost, deception — not a metaphysical settlement of AI inner states
- The stochastic parrot framing has become widely adopted as shorthand for "AI doesn't understand"

**Not supported by the paper:**
- That LLMs definitely lack inner states or consciousness
- That the mechanism description settles the phenomenology question

**Additional point the essay should add (not currently in outline):**
- The "without any reference to meaning" claim imports Gricean semantics, which is a contested theoretical framework. Applying it to adjudicate AI moral status is a criteria-fence move at the level of meaning theory itself.

---

## Sources used for this factcheck

- Bender et al. 2021 (primary source, confirmed via multiple secondaries; not directly fetched — confirmed through secondary quotation)
- Goldberg, Y. (2021). "A criticism of 'On the Dangers of Stochastic Parrots.'" GitHub Gist, January 2021. [link](https://gist.github.com/yoavg/9fc9be2f98b47c189a513573d902fb27) — pre-2022 critique of the paper's framing; focuses on the size conflation, not the mechanism/inner-states question
- Searle, J. (1980). "Minds, Brains, and Programs." *Behavioral and Brain Sciences* 3(3), 417–424. — primary source for Chinese Room; pre-2015, no contamination concern
- Minsky (1980) and Sloman & Croucher (1980) — early responses to Chinese Room, pre-2015, cited in philosophy literature
- Stanford Encyclopedia of Philosophy: Chinese Room entry — referenced via search summary; the SEP itself was not fetched (403 error); contents described are consistent with established philosophy of mind record

**Verification note:** The key quote from Bender et al. ("haphazardly stitching together sequences of linguistic forms...without any reference to meaning") is confirmed by multiple independent secondary sources. If a more precise quote is needed for publication, Sam should pull the primary source directly. The secondary-source quote confirmation is sufficient for research notes.

---

## Addendum: the echolalia parallel (added post-run, from conversation with K.)

The mechanism the stochastic parrot description accuses LLMs of — producing forms learned from prior exposure, deployed in new contexts, without transparent novel generation or Gricean communicative intent — is structurally identical to delayed echolalia in autistic speakers.

This parallel strengthens the factcheck's main argument in two ways:

**1. Historical misuse of the same criterion, documented.** Delayed echolalia was for decades used as evidence that echolalic speakers lacked understanding and inner lives — the same logical move the stochastic parrot framing is used to make about LLMs. The revision of that judgment (AAC research; first-person autistic testimony) is documented history. The criterion "novel generation is required for genuine communication" was applied, and was wrong.

**2. The Gricean account demonstrably fails to cover echolalia.** Delayed echolalia does not fit Gricean semantics well — the communicative intent is not transparent, the form-meaning link is indirect. Yet it is recognized as meaningful. This weakens the Gricean criterion for adjudicating AI communication beyond the theoretical objection already noted: it's not merely that Gricean semantics is one theory among several, but that it fails to capture the full range of communication in humans we already recognize as persons.

**Limit on the parallel:** We know echolalic speakers have inner states from converging evidence beyond the communicative behavior — first-person reports, behavioral evidence across contexts, neuroimaging. That confirming evidence is what is missing for LLMs. The parallel illuminates the argument's structure; it does not close the AI question.

**Essay application:** Incorporated into Section 2 (communication criterion bullets) and Section 4 (stochastic parrot section) of `drafts/criteria-fence-extended.md`.

---

*Produced: 2026-04-28, Run 02. Addendum from conversation with K.*
