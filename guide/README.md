# AI Evaluation and Model Selection Equations — Explanations

**Version 1.0.0 · 13 October 2026**  
Pacharapol Pimpa · Software Engineering bachelor’s student, Thammasat University  
**Independent Technical Companion — Not Peer Reviewed**

[Read the 22-page PDF](ai-evaluation-equations-v1.0.0.pdf) · [Editable Word document](ai-evaluation-equations-v1.0.0.docx) · [Original research manuscript](../paper/manuscript-v1.0.0.pdf)

## What this guide explains

This companion explains how to calculate task-specific AI quality, estimate complete operational cost, construct justified uncertainty and resource allowances, and choose the least-cost supported configuration under declared requirements.

It contains definitions and application instructions for six primary equations and 19 supporting formulas, 98 lines of worked mathematical calculations, and a complete 12-stage workflow. Classification, regression, paired binary-quality bounds, cost accounting, latency bounds and the earlier weighted-selection approach are covered.

## Calculation workflow

1. Define the task, metric, reference, quality floor, degradation margin, request horizon, budget and resource limits.
2. Separate development, selection and held-out data; freeze complete model and execution policies.
3. Collect paired outputs, failures, billable usage and resource measurements.
4. Audit completeness, comparability, units and sampling assumptions.
5. Calculate observed task quality and justified quality-preservation bounds.
6. Calculate expected horizon cost and separately justified budget and resource allowances.
7. Admit only configurations meeting every mandatory requirement with complete evidence.
8. Select by the declared cost objective and fixed tie rule, then confirm on untouched cases and reconcile actual billing.

The PDF provides the detailed calculations, variable definitions, boundary cases and full workflow. Missing evidence returns an explicit unsupported status; it is never assigned a favorable score.

## Evidence and limitations

The worked model-selection example uses constructed teaching inputs. It is not a new AI experiment, a current provider-price quotation or evidence of actual cost savings. The guide separately interprets reported results from the original Dry Bean and Bike Sharing case studies.

The proposed confidence-bound model-and-effort selector remains empirically unvalidated. This companion does not claim universal intelligence measurement, quality equivalence from nonsignificance or a new optimization theorem. Historical case-level records are not bundled; printed aggregates cannot recreate the original bootstrap experiments. No new model experiments or cloud jobs were run for this guide.

## Citation and rights

Pimpa, P. (2026). *AI Evaluation and Model Selection Equations — Explanations* (Version 1.0.0). Independent Technical Companion — Not Peer Reviewed. https://github.com/4d696e6b/ai-model-selection-research/tree/main/guide

[All rights reserved](../LICENSE). Public availability does not grant an open-source or Creative Commons license. Author affiliation does not imply university endorsement. AI assistance and author responsibility are disclosed in the PDF. No DOI has been assigned.
