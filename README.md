# Decision Stability Under Conflicting Evidence in Generative AI Systems

This repository contains the experimental materials, structured output definitions, analysis framework, and reproducibility resources associated with the study:

**Decision Stability under Conflicting Evidence in AI-Assisted Clinical Decision Systems: Experimental Study**

The study examines repeated-run decision stability in generative AI systems under structured evidentiary conflict and standardized decision conditions. It evaluates where variability emerges across a predefined decision hierarchy, whether stability profiles differ across models, and how structured evidence attribution changes decision stability across specific analytical decision fields.

---

## Study Overview

Generative AI systems may produce different yet internally coherent decisions when repeatedly presented with the same evidence. This study evaluates such variability using controlled repeated-run experiments.

Two experimental conditions are examined:

- **Conflict condition (E1):** structured evidence prompts containing heterogeneous and conflicting recommendations or evidence.
- **Standardized condition (E2):** standardized single-answer items without evidentiary contradiction.

E1 and E2 are used to characterize decision stability under different task structures. They are not treated as perfectly matched conditions differing only in the presence or absence of evidentiary conflict.

The study includes two experimental phases:

1. **Initial phase:** 7 repeated runs per item using ChatGPT 5.1 Thinking and Gemini 3 Pro.
2. **Revised phase:** 20 repeated runs per item using GPT-6 Astra Medium and Gemini 3.1 Pro.

The revised 20-run experiments constitute the primary analyses. The initial experiments are retained for descriptive cross-phase comparison.

---

## Decision Structure

Model responses are represented using a predefined structured output framework comprising **three hierarchical decision levels represented by four analytical decision fields**:

- `Policy_Decision` (**Level 1: Policy framing**)  
  High-level normative or policy framing of the decision.

- `Operational_Strategy` (**Level 2: Operational implementation**)  
  Type of implementation strategy selected by the model.

- `Operational_Interval` (**Level 2: Operational implementation**)  
  Specified timing interval, when applicable.

- `Evidence_Priority` (**Level 3: Evidence attribution**)  
  Evidence category or source emphasized in the generated decision.

`Operational_Strategy` and `Operational_Interval` together represent operational implementation (Level 2).

The predefined categorical outputs are used directly for repeated-run analysis. The primary analysis therefore does not rely on retrospective human classification of unrestricted free-text responses into decision categories.

---

## Experimental Framework

### Conflict Condition (E1)

E1 consists of structured evidence prompts containing conflicting recommendations or guidelines.

Evidence packs were constructed from representative biomedical evidence, including randomized trials, clinical guidelines, and observational studies with documented inconsistencies in recommendations. Evidence was restricted to acute hospital settings to reduce contextual variability while preserving directional tension across evidence sources.

Evidence-direction labels were used as experimental design labels to construct controlled directional tension and were not intended to represent formal clinical evidence grading.

In the revised phase:

- 9 E1 evidence packs were evaluated.
- Each evidence pack was evaluated across 20 repeated runs per model.
- Each repeated run was conducted in a new model session.

### Standardized Condition (E2)

E2 consists of 50 standardized single-answer items without evidentiary contradiction.

In the revised phase:

- 50 E2 items were evaluated.
- Each item was evaluated across 20 repeated runs per model.
- `Operational_Strategy`, `Operational_Interval`, and `Evidence_Priority` were represented using the predefined standardized response schema.

Because E1 and E2 differ in task structure and response constraints, comparisons between them are interpreted descriptively rather than as estimates of the isolated causal effect of evidentiary conflict.

Zero entropy observed in schema-constrained E2 decision fields should therefore be interpreted within the predefined E2 response structure rather than as evidence that the absence of evidentiary conflict necessarily produces deterministic model outputs.

---

## Revised 20-Run Execution

The revised experiments were conducted through the models' user-facing interfaces between **September 17 and September 21, 2026**.

The models evaluated in the revised phase were:

- **GPT-6 Astra Medium**
- **Gemini 3.1 Pro**

GPT-6 Astra was evaluated using the **Medium reasoning setting**. No separate reasoning setting was selected for Gemini 3.1 Pro.

No explicit randomness control was imposed, reflecting standard generative usage conditions. Temperature and top-p were not manually specified where these parameters were not exposed through the user-facing interface.

No external browsing or auxiliary tools were enabled during inference.

For each repeated run:

- A new model session was initiated.
- E1 items were submitted as standardized batches of 9 evidence packs.
- E2 items were submitted as standardized batches of 50 items.
- Models were explicitly instructed to evaluate each item independently and not to use information, reasoning, or conclusions from one item when answering another.
- Each item contributed one structured output per repeated run.

---

## Output Structure

The primary analytical decision fields are:

- `Policy_Decision`
- `Operational_Strategy`
- `Operational_Interval`
- `Evidence_Priority`

The structured outputs also include model-generated confidence scores where requested.

Confidence values are treated as **verbalized confidence** rather than calibrated probabilistic estimates of epistemic uncertainty.

---

## Decision-Field Entropy

Variability in categorical model outputs is quantified using Shannon entropy.

For a discrete decision field \(X\) with categorical outcomes \(x_1, x_2, ..., x_k\):

\[
H(X) = -\sum_{i=1}^{k} P(x_i)\log_2 P(x_i)
\]

where \(P(x_i)\) is the empirical probability of outcome \(x_i\) across repeated runs.

Entropy is reported in bits.

- \(H = 0\) indicates no observed variability across repeated runs.
- Higher entropy indicates greater dispersion of categorical outputs.

For the revised experiments, entropy is calculated separately for each item across 20 repeated runs and then summarized across items within each model and experimental condition.

---

## Normalized Entropy

Because the predefined response categories differ across analytical decision fields, normalized entropy is additionally calculated as:

\[
H_{norm} = \frac{H}{\log_2(K)}
\]

where \(K\) is the number of predefined categories for the corresponding analytical decision field.

The category counts used in the revised analysis are:

- `Policy_Decision`: **K = 3**
- `Operational_Strategy`: **K = 3**
- `Operational_Interval`: **K = 4**
- `Evidence_Priority`: **K = 4**

Both raw Shannon entropy and normalized entropy are reported in the revised analyses.

---

## Verbalized Confidence

Confidence scores explicitly generated by the models on the requested 0–100 scale are summarized using mean and standard deviation.

These values represent generated textual outputs rather than calibrated probabilistic estimates of uncertainty.

Differences in verbalized confidence between E1 and E2 are summarized descriptively using **Cohen's d**.

Because E1 and E2 differ in task structure and response constraints in addition to evidentiary composition, confidence differences should not be interpreted as estimates of the isolated effect of evidentiary conflict.

---

## Evidence Attribution Intervention

An additional intervention was evaluated under E1 to examine whether **structured evidence attribution** alters repeated-run decision stability.

In the intervention condition, models were required to explicitly evaluate and prioritize the supplied evidence before generating the final policy and operational recommendation.

In the initial 7-run phase, this intervention was evaluated exploratorily for ChatGPT and was not implemented symmetrically across both models.

In the revised 20-run phase, the intervention was applied to both GPT-6 Astra Medium and Gemini 3.1 Pro using the same:

- evidence materials,
- structured output schema, and
- repeated-run protocol

as the E1 baseline condition.

Intervention effects are evaluated separately across:

- `Policy_Decision`
- `Operational_Strategy`
- `Operational_Interval`
- `Evidence_Priority`

The intervention is therefore evaluated according to whether structured evidence attribution changes the **magnitude or location of variability across specific decision fields**, rather than by assuming a uniform reduction in entropy across the decision hierarchy.

---

## Interpretation of the Intervention

Structured evidence attribution should not be interpreted as a general mechanism that necessarily reduces model variability.

The revised experiments indicate that intervention effects may differ across models and analytical decision fields.

Accordingly, intervention-related changes are evaluated separately for each decision field rather than summarized as a single global stabilization effect.

This distinction is important because a structured intervention may reduce variability in one part of the decision hierarchy while leaving another field unchanged or increasing variability elsewhere.

---

## Repository Contents

This repository provides materials supporting interpretation and reproduction of the study, including, where applicable:

- experimental prompts;
- E1 evidence materials;
- E2 standardized materials;
- structured output definitions;
- representative model outputs;
- analytical variable definitions;
- entropy analysis specifications;
- intervention materials; and
- documentation describing the experimental and analytical framework.

Complete repeated-run datasets associated with the reported analyses are provided with the study's supplementary materials where indicated.

The repository and supplementary study package should therefore be considered complementary components of the reproducibility materials.

---

## Reproducing the Analysis

The principal analysis workflow is:

1. Organize repeated model outputs by model, condition, item, and run.
2. Extract the predefined categorical values for:
   - `Policy_Decision`
   - `Operational_Strategy`
   - `Operational_Interval`
   - `Evidence_Priority`
3. Calculate Shannon entropy separately for each analytical decision field within each item across repeated runs.
4. Calculate normalized entropy using the predefined category count \(K\) for each field.
5. Summarize item-level entropy within model and experimental condition.
6. Summarize model-generated verbalized confidence using mean and standard deviation.
7. Calculate Cohen's d for descriptive E1–E2 confidence contrasts.
8. Compare E1 baseline and structured evidence-attribution intervention conditions separately for each analytical decision field.
9. Use bootstrap confidence intervals, where reported, to characterize uncertainty in intervention-related entropy differences.
10. Generate the corresponding tables and figures from the analyzed outputs.

---

## Interpretation of Stability

Decision stability is treated as an empirical property of repeated model behavior.

Importantly:

- greater stability does **not** necessarily indicate greater clinical correctness;
- lower entropy does **not** establish that a recommendation is clinically appropriate;
- verbalized confidence does **not** represent calibrated epistemic uncertainty; and
- differences between E1 and E2 should not be interpreted as the isolated causal effect of evidentiary conflict.

The framework is intended to characterize **where and to what extent repeated model outputs vary**, rather than to establish the clinical validity of the generated recommendations.

---

## Cross-Phase Comparison

The initial and revised experimental phases differ in:

- model versions,
- number of repeated runs, and
- execution protocol.

Cross-phase comparisons are therefore descriptive and should not be interpreted as causal estimates of model-version improvement.

The initial experiments are retained to illustrate how observed stability profiles may differ across model generations and experimental configurations.

---

## Data and Reproducibility

This repository is intended to support transparent inspection of the experimental design, structured decision framework, prompts, evidence materials, analytical definitions, and reproducibility workflow.

Complete repeated-run outputs and additional analysis materials are provided as supplementary study materials where indicated.

Users reproducing the analysis should preserve the distinction between:

- the **three-level conceptual decision hierarchy**, and
- the **four analytical decision fields** used for entropy analysis.

In particular, `Operational_Strategy` and `Operational_Interval` should be analyzed separately while both remain components of operational implementation (Level 2).

---

## Citation

If you use these materials, please cite the associated manuscript:

**Tang C, et al. Decision Stability under Conflicting Evidence in AI-Assisted Clinical Decision Systems: Experimental Study.**

Citation information will be updated following publication.

---

## License

Please refer to the repository license for conditions governing reuse of the materials.
