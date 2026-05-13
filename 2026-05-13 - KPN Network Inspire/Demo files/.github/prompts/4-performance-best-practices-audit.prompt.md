---
mode: agent
agent: powerbi-developer
description: Analyze semantic models against performance best practices from the previous presentation
---

## Business Ask

The previous presenter shared best practices for improving semantic model performance. I want to check how well our models follow that advice and what concrete steps we should take.

## Performance Best Practices to Check

> **Fill these in during the presentation. Replace the examples below with the actual recommendations.**

1. Prefer Import over Direct Query
2. Optimize data load for encoding and compression
3. Use star schema design with fact and dimension tables
4. Check for relationship ambiguity
5. Sanity check on the level of detail, are we at the right grain?  
6. <!-- Add more as needed -->

## Instructions

1. **Scope:** Analyze **every** semantic model in this repo:
   - `KPN Network#Inspire.SemanticModel`
   - `Contoso Sales.SemanticModel`

2. **For each best practice listed above**, check every model:
   - Does the model currently follow this practice? (Yes / No / Partially)
   - If no: what specifically violates it? (list the tables, columns, relationships, or measures)
   - Should it be implemented for this model? (Yes / Not applicable — explain why)
   - What is the estimated effort? (Quick win / Moderate / Significant)

3. **Produce a comparison report** as a formatted table:

   | Best Practice | KPN Network#Inspire | Contoso Sales | Priority |
   |--------------|--------------------:|-------------:|----------|
   | Practice 1   | ✅ / ❌ details     | ✅ / ❌ details | High/Med/Low |

4. **End with a prioritized action plan** — ordered by impact, with quick wins first.

5. **Do NOT apply any changes** — this is analysis only. The output should be actionable for a developer to implement afterward.
