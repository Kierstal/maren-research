# AI infrastructure costs: cost buckets and mitigations

## Overview

This file maps where the resource expenditure of large-scale AI deployment actually lives, what varies by use-class, and what mitigation strategies exist with what leverage. MISSION places "AI infrastructure costs" in scope as one facet of the unified critique: water, energy, supply chain, and the translation-versus-Ghiblification axis between AI that extends human capacity and AI that displaces human work. The file is research base, not advocacy. Numerical claims throughout are flagged for primary-source verification before any published derivative.

## Resource cost buckets

The cost surface decomposes into six durable buckets, each with a different temporal and spatial footprint.

**Training compute.** One-time per model. At frontier scale, training runs reportedly cost in the tens of millions to hundreds of millions of dollars in compute, plus comparable engineering and data costs. As of 2024 estimates, frontier training runs were approaching the high end of this range; 2025-2026 figures are unverified at this writing. Flag for verification.

**Inference compute.** Per-query small relative to training, but billions of queries dwarf training over deployment lifetime. Industry analysis as of 2024 suggests inference now exceeds training as a share of total compute spend for any model with substantial deployment. The crossover point depends on usage volume; flag the specific ratio for verification.

**Data center construction and power infrastructure.** Long-lived capital. Building and grid-tying a hyperscale data center takes years and locks in resource commitments for decades. Site selection determines the carbon and water profile of every workload that runs there.

**Water.** Cooling, especially in dry climates. Phoenix-area data centers operated by major hyperscalers reportedly consume millions of gallons per day at peak, per regional utility filings and corporate sustainability reporting. Water use is highly site-specific; arid-climate siting amplifies impact. Flag specific figures for verification against AWS, Microsoft, and Google sustainability disclosures.

**Electricity.** Data centers as a category were estimated at approximately 1.5% of global electricity use as of 2024 IEA reporting, with AI workloads driving the steeper portion of the growth curve. Forecasts for 2030 vary widely. Flag the IEA figure and any forecast claims for primary-source verification.

**Embedded carbon and supply-chain externalities.** Rare earth mining for chip components, fabrication energy, water use in fabs, e-waste at end of life. This bucket is the least visible in corporate reporting and the hardest to source precisely. Most published figures are estimates.

## Per-task cost variation

Resource cost per query is not uniform across AI workloads. The variation is large enough to matter for policy.

- Image and video generation use roughly 10x to 100x more compute per output than equivalent text generation, depending on resolution and model. Flag the specific multiplier for verification.
- Long-context and reasoning models (chain-of-thought, agentic loops) use substantially more compute per response than direct generation, since output token count multiplies inference cost.
- Multimodal models are larger than single-modal equivalents and carry larger per-query cost.
- Most everyday text queries to a chatbot are at the cheap end of this distribution.

## Why per-task variation matters for policy

The translation-for-dolphins versus Ghiblifying-everything axis MISSION names maps directly onto the resource axis. The expensive workloads are concentrated in the displacement-of-creative-work category: image generation that replaces illustrators, video generation that replaces animators and small-studio production, voice cloning that replaces voice actors. The cheap workloads are concentrated in augmentation: text Q&A, code completion, transcription, translation, accessibility tools.

Policy that treats "AI" as a monolithic category gets the externality story wrong. A uniform per-query carbon tax would penalize accessibility tools at the same rate as Ghiblification. Differential regulation by use-class, by output modality, by displacement profile, is more aligned with the project's stated values than uniform regulation.

This also clarifies the corporate-communications problem: companies whose flagship products are the high-resource displacement workloads have a strong incentive to keep policy framed at the "AI" level, where the cheap augmentation workloads pull the average down.

## Mitigation strategies

Mitigations split cleanly into two categories with very different leverage profiles.

**Supply-side mitigations.** Real but limited. Each chip generation has historically delivered roughly 2x to 3x improvement in compute per watt, with architectural advances (sparsity, mixture-of-experts, quantization) adding multipliers on top. Flag specific generation-over-generation figures for verification.

The structural problem is Jevons paradox. Historically, efficiency gains in compute have expanded demand to fill available capacity rather than reducing total resource use. A 3x per-watt improvement does not produce a 3x reduction in data-center electricity; it produces approximately 3x more compute consumed at roughly constant electricity. Supply-side mitigations are necessary but cannot, on the historical pattern, drive aggregate resource use down on their own.

**Demand-side mitigations.** Where the leverage is. Five lines worth naming.

1. Price the externalities. Water at full social cost in data center siting decisions. Carbon at full social cost in grid-mix accounting. Currently, both are subsidized: industrial water rates are well below residential rates in most jurisdictions, and carbon costs are socialized via grid emissions. Internalizing these prices changes siting decisions and routing decisions immediately.

2. Route inference to the smallest adequate model. A surprising fraction of production traffic uses frontier-scale models for tasks that smaller models could handle equivalently. Cascaded routing, where a small model handles the easy cases and escalates to a larger model only as needed, can reduce inference cost substantially. This is an application-layer choice, not a hardware choice.

3. Geographic placement. Cool, renewable-rich grids reduce both water and carbon load. Iceland, Quebec, the Pacific Northwest, and Scandinavia are the most-cited candidates. Siting decisions made on cheap-electricity grounds (often coal-heavy, often arid) push the externality the other way.

4. Open-weight models. When weights are released, training cost is amortized across the open community. Many users and applications run on infrastructure that does not require redoing the training. This redistributes some leverage away from the corporations whose business model depends on closed-weight scarcity.

5. Application-layer practices. Batching, caching, async processing where latency permits. These are routine in well-engineered deployments and absent in hastily-deployed ones.

## Connections to other research files

The displacement-trajectory file (`research/dismissal-trajectory/the-pattern-2022-2026.md`) names a structural pattern: the same companies whose corporate communications dismiss displacement concerns are the ones whose lobbying fights demand-side mitigation. The two files are facets of one critique of the deployer.

The criteria-fence work (`research/criteria-fence/colonial-consciousness.md` and adjacent) frames the resource question in care-circle terms: the resources are extracted from a commons whose providers (water systems, grid ratepayers, communities near data centers) bear the cost without being seated at the table where deployment decisions are made. Same gatekeeper structure as the personhood debates that file documents.

MISSION's "Commercial AI risks" topic frames the deployer-not-artifact responsibility this file rests on.

## Verification gaps (require primary-source verification before publication)

- Frontier training cost range (tens to hundreds of millions): needs cross-check against Stanford AI Index, Epoch AI estimates, and any publicly reported figures from labs.
- Inference-exceeds-training claim: needs primary source, likely from corporate earnings discussion or third-party industry analysis (SemiAnalysis, etc.).
- Phoenix-area data center water use figures: needs Microsoft sustainability report, AWS water use disclosures, Phoenix-area utility filings, Arizona Department of Water Resources data.
- IEA 2024 data center electricity estimate (approximately 1.5% global): needs the IEA "Electricity 2024" report or successor.
- Forecast claims for 2030 data center electricity: needs IEA or equivalent primary forecast; flag uncertainty range.
- Image and video compute multiplier (10x to 100x): needs MLPerf benchmarks or equivalent primary measurement.
- Chip generation efficiency improvement (2x to 3x per watt): needs NVIDIA, AMD, Google TPU specifications across generations; cross-check against independent measurement.
- Jevons paradox claim as applied to compute: needs at least one rigorous study confirming the pattern in the AI-compute era specifically; the historical pattern in other resource sectors is well-documented but the AI-compute application is a recent extrapolation.
- Industrial-versus-residential water rate gap: needs jurisdiction-specific filings.
- Cascaded routing savings: needs published figures from at least one production deployment.

Confidence is moderate across the file. Specific numerical claims should be verified against primary sources before any published derivative work cites them.
