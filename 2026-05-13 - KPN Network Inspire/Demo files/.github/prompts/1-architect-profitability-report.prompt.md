---
mode: agent
agent: powerbi-architect
description: Design a Product Profitability dashboard from a business requirement
---

## Business Ask

Our finance team wants a **Product Profitability Dashboard** that helps them understand which product categories and individual products are driving margin, and which are underperforming.

They want to see:
- **Gross margin** (Sales Amount minus Cost Amount) by product category
- **Margin percentage** by category and product
- A **top 10 / bottom 10** products by margin
- **Trend over time** — monthly margin development to spot if a category is declining
- A **cost breakdown** visual showing Unit Cost vs. Net Price distribution
- Ability to **filter by year** and **by store/region**

The data is in the existing **KPN Network#Inspire** semantic model which already has Sales (with Quantity, Net Price, Unit Cost), Product (with Category, Subcategory, Product Name), Store, and Date tables.

## Instructions

1. Analyze the existing `KPN Network#Inspire.SemanticModel` to understand available tables, columns, and measures.
2. Identify which new DAX measures are needed (e.g., `Cost Amount`, `Gross Margin`, `Margin %`).
3. Produce a full spec document in `specs and principles/Product-Profitability-Report.spec.md` including:
   - Requirements with acceptance criteria (EARS notation)
   - Architecture diagram (Mermaid)
   - Visual layout table with positions
   - Data source mapping
   - New measures with DAX definitions
   - Task breakdown for the developer agent
4. Ask clarifying questions only if critical information is missing.

## Follow-up

After the spec is complete, ask the user whether they want to hand it off to the `powerbi-developer` agent to implement it. If yes, invoke `@powerbi-developer` with the prompt:

> Implement the spec at `specs and principles/Product-Profitability-Report.spec.md`. Create all required measures in the semantic model and build the report with all visuals, following the task list in the spec.
