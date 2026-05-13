---
mode: agent
agent: powerbi-developer
description: Run BPA + self-service usability analysis on a semantic model and produce a remediation report
---

## Business Ask

We want to understand how healthy and **self-service-friendly** our semantic models are. This means two things:

1. **Best Practice Analysis (BPA)** — Run the standard BPA rules to catch performance, naming, and structural issues.
2. **Self-service usability analysis** — Evaluate how easy the model is for a business user to explore on their own in Power BI. Consider:
   - Are all measures and columns described (do they have `description` properties)?
   - Are field names business-friendly (no `CamelCase`, no `tbl_` prefixes, no cryptic abbreviations)?
   - Is there a clean star schema structure (clear fact/dimension separation)?
   - Are hidden fields used appropriately (keys and technical columns hidden, business fields visible)?
   - Are display folders used to organize measures and columns?
   - Is there a date table marked as such for time intelligence?
   - Are format strings set sensibly (currency, percentages, integers)?

## Instructions

1. **Scope:** Analyze **both** semantic models in this repo:
   - `KPN Network#Inspire.SemanticModel`
   - `Contoso Sales.SemanticModel`

2. **Step 1 — BPA:** Run the BPA script at `.github/skills/powerbi-semantic-model-authoring/scripts/bpa.ps1` with the custom rules file against each model. Collect and interpret the results.

3. **Step 2 — Self-service audit:** For each model, read all TMDL table files and evaluate the usability criteria listed above. Score each criterion as ✅ (good), ⚠️ (partial), or ❌ (missing).

4. **Step 3 — Remediation report:** Produce a single report at `specs and principles/Model-Health-Report.md` structured as:
   - Executive summary (which model is in better shape?)
   - BPA findings per model (grouped by severity)
   - Self-service usability scorecard per model
   - Prioritized remediation steps — what to fix first for maximum impact
   - Estimated effort per fix (quick win / moderate / significant)

5. Do NOT apply any fixes yet — this is an analysis-only task. The report should be actionable for a developer to pick up.

## Follow-up

After presenting the remediation report, ask the user:

> "I've identified [N] remediation items across both models. Want me to hand these off to a developer agent to start fixing them? I can kick off parallel work streams:
> - `@powerbi-developer` to fix the **KPN Network#Inspire** model
> - `@powerbi-developer` to fix the **Contoso Sales** model
>
> Or I can tackle them one model at a time. What do you prefer?"

If the user agrees, invoke the developer agent(s) with the specific remediation steps from the report, referencing the model paths and the prioritized action plan.
