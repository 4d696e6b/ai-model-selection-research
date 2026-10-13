# Measuring AI Performance and Selecting Models Under Quality and Cost Constraints

**Framework Proposal and Empirical Case Studies · Research version 1.0.0**  
Pacharapol Pimpa · Software Engineering bachelor’s student, Thammasat University  
**Independent Research Manuscript — Not Peer Reviewed**

[Read the manuscript PDF](paper/manuscript-v1.0.0.pdf) · [Citation](CITATION.cff)

## Equation explanations and worked calculations

A separate **version 1.0.0 instructional companion** is now available: [AI Evaluation and Model Selection Equations — Explanations](guide/README.md). [Read its 22-page PDF](guide/ai-evaluation-equations-v1.0.0.pdf) or download the [editable Word document](guide/ai-evaluation-equations-v1.0.0.docx).

The guide explains variables, mathematical workings and the complete selection workflow. Its teaching examples are explicitly constructed; it reports no new model experiments or measured cost savings. The original research manuscript and its evidence remain unchanged.

## Overview and motivation

Choosing a model means deciding whether its task quality, latency, resource use and total cost meet a particular deployment need. A high benchmark score alone cannot answer that question. This project specifies a transparent task-conditioned selection framework and preserves two completed empirical case studies of an earlier weighted-selection approach.

The completed study implements historical weighted predictive-pipeline selection; its software is not bundled in this manuscript repository. The confidence-bound optimizer, LLM model-and-effort selection and full operational-cost validation remain proposals. This repository does not establish cost savings with preserved quality.

## Research questions

1. Can a common evidence contract represent task quality, operational cost and mandatory constraints while exposing missing or incomparable evidence?
2. Can least-cost admissible selection reduce complete operational cost against a fixed reference while meeting prespecified quality requirements on untouched cases?
3. How sensitive are decisions to quality thresholds, budgets, workload composition and supported inference policies?

Historical case studies partially address evidence handling and preference/resource sensitivity. The central cost-preservation question remains unanswered.

## Proposed mathematical framework

Task-specific observed quality is

$$Q_t^D(c)=M_t\big((y_i,f_c(z_i))_{i\in D}\big).$$

Projected cost for a horizon of $N$ requests is

$$C_N(c)=C_{\mathrm{setup}}(c)+N\sum_h p_h\mathbb E[v_h(c)]+C_{\mathrm{support},N}(c).$$

The proposed selection principle is

$$\begin{aligned}
c^*&=\arg\min_{c\in\mathcal C_t} C_N(c)\\
\text{subject to}\quad L_\alpha[Q_t(c)]&\ge q_{\min},\\
U_\alpha[Q_t(c_{\rm ref})-Q_t(c)]&\le\delta,\\
C_N^U(c)&\le B_N,\\
r_l^U(c)&\le b_l\quad\forall l.
\end{aligned}$$

Here $c$ identifies a complete, frozen model and execution policy; $t$ identifies the task; $D$ contains evaluation case identities; $M_t$ is a declared higher-is-better metric; $Q_t$ is unknown population quality. Costs and budget share one currency and horizon. Lower/upper quality bounds must have a justified, multiplicity-aware error policy. $q_{\min}$ is the absolute quality floor; $\delta$ is the permitted degradation in the metric’s units; $c_{\rm ref}$ is the fixed reference. Operational bounds have their own declared meanings: $C_N^U$ is a conservative cost bound, and $r_l^U,b_l$ are measured/planned resource bounds and limits in matching units.

The finite candidate set contains supported, comparable configurations with complete evidence. Missing evidence and demonstrated infeasibility are different outcomes. Ties use projected cost, then conservative cost, optional resource utilization, then immutable identifier. If no candidate qualifies, return no supported selection. Minimizing a conservative upper cost bound would be a different objective. These are established constrained decision principles, not a new optimization theorem. Full definitions and application instructions are in Section 5 of the manuscript.

## Completed methodology

Azure CPU experiments compared linear, random-forest and histogram-boosting pipelines on UCI Dry Bean classification and Bike Sharing sequential one-hour-ahead prediction. Dataset-aware splits, bounded hyperparameter searches, frozen decisions, simulated operating-loss profiles, resource profiling, paired bootstrap comparisons and same-author cloud refits were used. Four operating profiles compared weighted selection with highest validation quality, cheapest feasible warm-compute proxy, fixed linear and minimum validation loss. The detailed protocol is retained in Appendix B of the manuscript.

## Key findings

- Weighted selection chose linear for Bean and boosting for Bike.
- Bean held-out macro-F1 ranged from 0.9290 to 0.9297 across the three candidate families. The linear-versus-boosting operating-loss comparison was inconclusive and failed its precision target.
- Bike boosting had lower MAE than linear (49.8233 versus 51.9836), but higher RMSE (84.3342 versus 78.2904). Metric choice mattered.
- In the Bike underprediction-heavy quality profile, boosting had **higher** simulated loss than linear: difference 7.5731 weighted-count units/hour, adjusted conditional interval [3.0698, 12.1578].
- In the Bike resource profile, the direction favored boosting, but the declared precision target was missed. Identical deployment comparisons are identities, not quality-equivalence tests.
- Fresh same-author refits and internal consistency checks supported repeatability. They are not independent academic validation.

The warm CPU-dollar proxy excludes substantial operational costs and is not billed expenditure. No LLM inference-cost reduction is reported.

## Repository contents and reproduction status

This repository contains the final manuscript PDF, an equation-use companion in PDF and editable Word form, an overview and citation information. Historical code, datasets, case-level predictions, fitted models, complete cloud logs and aggregate report files are not bundled here.

**Internally repeated; not independently reproducible with the materials published in this repository.** The manuscript documents the dataset sources, splits, model settings, statistical procedures, environment and cloud job lineage. Independent reproduction requires additional original artifacts or an explicitly documented reconstruction. Same-author refits and automated consistency checks do not constitute independent academic validation. No new ML experiments were run for this manuscript release.

## Limitations and future work

The operating-loss preferences are illustrative, comparisons are conditional on fitted models and dependence assumptions, and two small classical ML tasks cannot validate general LLM selection. Proposed future work is implementation of the quality-bound optimizer and a separate frozen code-generation study with complete cost accounting. The manuscript describes this work; the repository does not present it as implemented software.

## Citation and licensing

Pimpa, P. (2026). *Measuring AI Performance and Selecting Models Under Quality and Cost Constraints: Framework Proposal and Empirical Case Studies* (Version 1.0.0). Independent Research Manuscript — Not Peer Reviewed.

Machine-readable citations: [CITATION.cff](CITATION.cff), [BibTeX](paper/citation.bib). No DOI has been assigned.

Published on GitHub on 12 October 2026; the manuscript retains its 11 October 2026 date. Research version 1.0.0.

**All rights reserved**, as stated in [LICENSE](LICENSE). Public availability does not grant an open-source or Creative Commons reuse license. Referenced datasets and dependencies retain their own rights; none are bundled. Author affiliation does not imply university endorsement. The manuscript retains its research-assistance disclosure.
