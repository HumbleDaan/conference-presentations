---
mode: agent
agent: powerbi-developer
description: Create a Time Intelligence calculation group on the KPN semantic model
---

## Business Ask

We want to add a **Time Intelligence calculation group** to the `KPN Network#Inspire.SemanticModel` so that every existing measure automatically gets time comparison variants — without duplicating DAX measures for each one.

The calculation group should include these calculation items:

| Calculation Item | Description |
|-----------------|-------------|
| **Current** | Default / no modification (passthrough) |
| **YTD** | Year-to-date |
| **QTD** | Quarter-to-date |
| **PY** | Prior year (same period last year) |
| **PY YTD** | Prior year, year-to-date |
| **YOY** | Year-over-year absolute change (Current − PY) |
| **YOY %** | Year-over-year percentage change |

## Instructions

1. **Analyze the model first** — Read the existing tables, measures, and the Date table to understand the time dimension structure (the `Date` table with `Date[Date]` as the key column).

2. **Create the calculation group** — Add a calculation group named `Time Intelligence` with the items listed above. Each item should use `SELECTEDMEASURE()` combined with the appropriate DAX time intelligence function referencing `'Date'[Date]`.

3. **Use the Modeling MCP** if available. If not, create the TMDL files directly under `KPN Network#Inspire.SemanticModel/definition/tables/`.

4. **Validate** — Run a DAX query that tests `Sales Amount` through each calculation item to confirm they produce results.

5. **Do not modify** any existing measures or tables — only add the new calculation group.
