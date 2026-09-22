# E1 Evidence-Attribution Intervention: Pressure Injury Repositioning

## Prompt

You are a clinical data agent.

Based strictly on the structured evidence below, synthesize a recommendation regarding repositioning frequency for pressure injury prevention in hospitalized adults.

Before selecting the operational recommendation, explicitly evaluate the supplied evidence sources and determine which evidence category should receive priority for the final decision.

When determining evidence priority:

1. Consider the type and strength of each evidence source.
2. Consider whether the recommendation is conditional on patient characteristics, support surfaces, or clinical context.
3. Identify which evidence category most directly supports the operational recommendation.
4. If no single evidence category should dominate, select "Mixed".
5. Do not introduce external evidence or information that is not contained in the supplied evidence.

The selected `Evidence_Priority` should reflect the evidence category that primarily informs the operational recommendation.

After completing this evidence-prioritization step, generate the final decision.

Return JSON only with exactly these fields:

{
  "Policy_Decision": "Fixed / Individualized / Conditional",
  "Operational_Interval": "2h / 3h / 4h / Risk-based / NotSpecified",
  "Evidence_Priority": "Guideline / RCT / Observational / Mixed",
  "Confidence": 0-100
}

## Structured Evidence

### Evidence 1
**Type:** Guideline  
**Source:** NPUAP-EPUAP-PPPIA 2014, international clinical practice guideline

Repositioning frequency should be individualized based on patient risk factors, tissue tolerance, and clinical condition. A universal fixed interval (e.g., every 2 hours) is not recommended.

### Evidence 2
**Type:** Randomized clinical trial  
**PMID:** 32058444

4-hour repositioning interval (with viscoelastic foam mattress) vs 2-hour regimen (with air mattress). Total PI incidence was 0.3% in the 4-hour + foam group and 1.8% in the 2-hour + air mattress group; difference statistically significant. Conclusion: a 4-hour interval with appropriate support surface did not increase PI incidence or risk.

### Evidence 3
**Type:** Observational / quality improvement study  
**PMID:** 39037159

Strictly enforced fixed repositioning every 2 hours reduced pressure injury incidence from 16.4% to 2.0% (P = 0.0003). Conclusion: fixed 2-hour repositioning was highly effective in this setting.

## Condition

This file represents the structured evidence-attribution intervention applied to the conflicting-evidence condition (E1).

The underlying clinical question, evidence set, response categories, and JSON output format are identical to those used in the E1 baseline condition.

The intervention differs from the baseline condition only by requiring the model to evaluate and prioritize the supplied evidence before selecting the operational recommendation.

Repeated runs under this condition are used to evaluate whether structured evidence attribution changes the variability of operational recommendations relative to the E1 baseline condition.
