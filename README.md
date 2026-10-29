# Decision Stability Under Conflicting Evidence in Generative AI Systems

This repository contains experimental materials, structured model outputs, analytical definitions, and reproducibility resources associated with the study:

**Decision Stability under Conflicting Evidence in AI-Assisted Clinical Decision Systems: Experimental Study**

The study investigates decision stability in generative AI systems when repeatedly presented with conflicting clinical evidence. It examines variability across different levels of clinical decision-making and evaluates how structured evidence attribution affects model-generated decisions.

## Study Overview

The research examines whether generative AI systems produce consistent clinical recommendations when presented with the same evidence across repeated independent runs.

Two experimental conditions were investigated:

- **E1 — Conflicting Evidence:** Clinical decision-making using structured evidence packs containing heterogeneous and potentially conflicting recommendations.
- **E2 — Standardized Questions:** Decision-making using standardized clinical questions without the same structured evidentiary conflicts.

E1 and E2 differ in task structure and response constraints. Their comparison is descriptive and should not be interpreted as isolating the causal effect of conflicting evidence.

### Experimental Stages

The research was conducted in two separate stages:

| Stage | Models | Repetitions | Role |
|---|---|---|---|
| Initial exploratory stage | ChatGPT 5.1 Thinking; Gemini 3 Pro | 7 runs | Exploratory comparison |
| Revised primary stage | GPT-6 Astra Medium; Gemini 3.1 Pro | 20 runs | Primary statistical analysis |

The stages used different model versions and were conducted independently. They should not be combined into a single 27-run experiment.

The primary 20-run experiments were conducted between September 17 and September 21, 2026.

## Original Research Instructions

The research originated from a predefined investigation of decision stability across three hierarchical clinical decision levels:

1. **Policy decisions:** General clinical principles and recommendations.
2. **Operational decisions:** Specific implementation parameters.
3. **Evidence attribution:** The evidence prioritized when formulating recommendations.

The original research instructions also addressed literature screening, conflicting-evidence construction, and standardized clinical questions.

An English summary of the original Chinese research instructions is available here:

[Original Research Instructions](original_research_instructions.txt)

This document summarizes the original research direction and tasks. It is not presented as a verbatim translation or as a retrospectively developed experimental protocol.

## Experimental Framework

### E1: Conflicting Clinical Evidence

Nine finalized evidence packs were used in the primary experiments.

The evidence packs were developed from clinical literature involving randomized trials, guidelines, systematic reviews, and observational evidence.

The literature preparation process identified 24 candidate sources, of which 13 distinct sources were incorporated into the nine finalized evidence packs.

Sources could appear in more than one evidence pack.

Evidence selection focused on meaningful differences in clinical recommendations within acute hospital settings.

The experimental evidence-direction labels were used to characterize the literature during evidence-pack construction. They were not model-generated clinical decisions.

### E2: Standardized Clinical Questions

The primary E2 experiment included 50 standardized clinical questions.

Each question was evaluated across 20 repeated runs per model.

The standardized response structure was used to examine decision behavior under a different task configuration.

Because E2 imposed different response constraints, zero entropy in a constrained field should not be interpreted as proof that the absence of conflicting evidence necessarily produces deterministic model behavior.

## Primary Experimental Procedure

The revised 20-run experiments evaluated:

- GPT-6 Astra Medium, using the Medium reasoning setting.
- Gemini 3.1 Pro.

The experiments were conducted through the models' user-facing interfaces.

No explicit temperature or top-p settings were manually specified where those parameters were unavailable.

No external browsing or auxiliary tools were enabled during inference.

For each repeated run:

1. A new model session was initiated.
2. The standardized experimental prompt was submitted.
3. E1 consisted of nine evidence-pack items.
4. E2 consisted of 50 standardized items.
5. The model was instructed to evaluate each item independently.
6. The structured model-generated responses were recorded.

The archived outputs provide the basis for the reported statistical analyses.

## Model-Generated Decision Fields

The experimental prompts requested three categorical decision fields:

- `Policy_Decision`
- `Operational_Interval`
- `Evidence_Priority`

A model-generated `Confidence` score was also recorded.

These fields appear in the original experimental JSON outputs.

**Operational_Strategy was not an additional field directly generated by the models.**

Instead, the operational response was examined using two analytical representations derived from the model-generated `Operational_Interval` field.

The researchers did not manually assign individual model decisions.

## Analytical Decision Measures

The three-level clinical decision hierarchy was evaluated using four analytical measures:

| Decision level | Analytical measure | Source |
|---|---|---|
| Level 1 — Policy | `Policy_Decision` | Model-generated |
| Level 2 — Operational | `Operational_Strategy` | Derived from model-generated operational response |
| Level 2 — Operational | `Operational_Interval` | Analytical categorization of model-generated operational response |
| Level 3 — Evidence | `Evidence_Priority` | Model-generated |

The four analytical measures do not imply that the models generated four independent categorical decision fields.

### Operational Category Mapping

The archived operational responses can be represented using two complementary analytical categorizations that reproduce the reported entropy values.

| Original model response | Operational_Strategy (K=3) | Analytical Operational_Interval (K=4) |
|---|---|---|
| `2h` | Fixed Interval | 2h |
| `3h` | Fixed Interval | 3h |
| `4h` | Fixed Interval | 4h |
| `Risk-based` | Risk-based | No Fixed Interval |
| `NotSpecified` | NotSpecified | No Fixed Interval |

These are deterministic category transformations of the archived model-generated responses.

Independent recalculation using these mappings reproduces the reported operational entropy values. The mappings are documented as a reproducible analytical representation; numerical agreement alone does not establish when they were originally adopted.

For a detailed explanation, see:

[Methodological Transparency and Reproducibility](methodological_transparency.txt)

## Entropy Analysis

Decision stability was evaluated using Shannon entropy.

For a categorical decision variable X:

\[
H(X)=-\sum_{i=1}^{K}p_i\log_2(p_i)
\]

where \(p_i\) is the empirical proportion of responses in category \(i\).

Entropy is measured in bits.

- Lower entropy indicates greater observed consistency.
- Higher entropy indicates greater variability across repeated outputs.
- Zero entropy indicates no observed variation within the repeated runs.

Entropy was calculated separately for each item across 20 repeated runs and then summarized within each model and experimental condition.

### Normalized Entropy

Normalized entropy was calculated as:

\[
H_{\mathrm{norm}}(X)=\frac{H(X)}{\log_2(K)}
\]

The analytical category counts were:

| Analytical measure | K |
|---|---:|
| Policy_Decision | 3 |
| Operational_Strategy | 3 |
| Operational_Interval | 4 |
| Evidence_Priority | 4 |

For the analytical `Operational_Interval` measure, the original responses `Risk-based` and `NotSpecified` were combined into `No Fixed Interval`.

Therefore, K=4 refers to the four analytical categories, rather than the five original operational response options.

## Verbalized Confidence

The models were asked to provide verbalized confidence scores on a 0–100 scale.

Confidence was summarized using mean and standard deviation.

Cohen's d was used to describe differences in verbalized confidence between experimental conditions.

These confidence scores represent model-generated self-reports, not calibrated probabilities of clinical correctness.

## Evidence Attribution Intervention

An additional E1 intervention examined whether requiring explicit evidence evaluation and prioritization affected decision stability.

In the primary 20-run experiments, the intervention was applied to both models.

The intervention was assessed separately across the four analytical measures.

Changes in entropy were interpreted as field-specific effects rather than evidence of uniform stabilization across the decision hierarchy.

An intervention could reduce variability in one analytical measure while leaving another unchanged or increasing variability elsewhere.

## Reproducibility

This repository supports inspection of the experimental materials and computational verification of the reported findings.

The principal analytical workflow is:

1. Organize archived model outputs by model, experimental condition, item, and run.
2. Extract the three directly generated categorical decision fields and confidence values.
3. Apply the documented operational category mappings.
4. Calculate item-level Shannon entropy across repeated runs.
5. Calculate normalized entropy using the analytical category count K.
6. Summarize entropy across items within each model and experimental condition.
7. Summarize verbalized confidence using mean and standard deviation.
8. Calculate descriptive effect sizes and uncertainty estimates where reported.
9. Generate the corresponding statistical tables and figures.

### Experimental Replication

The experimental prompts and evidence materials may be submitted again to the specified model versions under comparable conditions.

Because generative AI systems can change over time and produce variable responses, newly generated outputs may differ from the archived experimental results.

### Computational Reproducibility

Computational verification uses the archived 20-run outputs and documented analytical category mappings.

Independent recalculation from the archived outputs has reproduced the reported operational entropy values for the primary E1 baseline and intervention conditions.

The archived data, statistical result tables, and analytical documentation should be used together when verifying the published numerical results.

## Repository Contents

The repository organizes materials related to:

- Original research instructions.
- Methodological transparency and analytical definitions.
- E1 conflicting-evidence materials.
- E2 standardized experimental materials.
- Initial exploratory experiments.
- Revised 20-run experiments.
- Model-generated outputs and statistical results.
- Reproducibility documentation.

Key documentation:

- [Original Research Instructions](original_research_instructions.txt)
- [Methodological Transparency and Reproducibility](methodological_transparency.txt)

The complete primary experimental outputs and corresponding statistical tables are intended to accompany these methodological materials.

## Interpretation and Limitations

Decision stability is an empirical characteristic of repeated model behavior.

Greater stability does not necessarily indicate greater clinical correctness.

Likewise, lower entropy does not establish that a clinical recommendation is appropriate.

The experiments were designed to characterize where model decisions vary across policy, operational implementation, and evidence attribution.

E1 and E2 differ in task structure and response constraints, and cross-condition comparisons should therefore be interpreted descriptively.

The initial 7-run experiments and revised 20-run experiments also used different model versions and protocols. Cross-phase comparisons are exploratory rather than causal estimates of model improvement.

## Citation

If you use these materials, please cite the associated manuscript:

**Tang C, et al. Decision Stability under Conflicting Evidence in AI-Assisted Clinical Decision Systems: Experimental Study.**

Citation details will be updated following publication.

## License

Please refer to the repository license for conditions governing reuse of these materials.
