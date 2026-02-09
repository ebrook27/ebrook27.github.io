---
title: "Opioid Overdose Mortality Modeling, Risk Stratification, and Policy Counterfactuals"
excerpt: "County-level forecasting, risk identification via predictive instability, and scenario-based policy simulations."
collection: portfolio
order: 1
---

## Problem Context
Opioid overdose mortality in the United States exhibits strong geographic persistence, particularly in rural regions such as central Appalachia. While a large body of work has focused on predicting mortality rates using socioeconomic and prescribing data, less attention has been paid to **where and why predictive models systematically fail**—and what those failures reveal about underlying, place-based risk.

This project develops an **end-to-end modeling framework** to:

1. identify counties experiencing *persistent, elevated mortality risk*, and  
2. evaluate how predicted mortality responds to changes in policy-relevant variables under structured counterfactual scenarios.

Rather than treating prediction error as noise, the framework explicitly **leverages predictive instability as a signal of structural risk**.

<figure>
  <img
    src="/images/mortality_model_error_compare.png"
    alt="For a given model, areas with low mortality were relatively over-predicted, and regions with high mortality were relatively under-predicted."
    style="width:85%; height:auto;"
  >
  <figcaption>
    <em>For a given model, areas with low mortality were relatively over-predicted, and regions with high mortality were relatively under-predicted.</em>
  </figcaption>
</figure>

---

## Data and Scope
The analysis integrates multiple nationwide, county-level datasets spanning 2014–2022:

- **Opioid overdose mortality** from CDC WONDER (Multiple Cause of Death), using standard ICD-10 codes for opioid-involved overdoses. To address systematic suppression in low-population counties, we use a spatially imputed mortality series that preserves rural coverage and spatial coherence.
- **Structural vulnerability indicators** from the CDC Social Vulnerability Index (SVI), providing a parsimonious representation of socioeconomic and demographic risk factors.
- **Prescription opioid dispensing rates**, constructed from CDC data and extended historical series.
- **Unemployment rates** from the Bureau of Labor Statistics, included explicitly to support interpretable, policy-relevant counterfactuals.
- **Health insurance coverage** from the Census Bureau’s Small Area Health Insurance Estimates (SAHIE), using a consistent county-year measure for ages 0–64.

Together, these data support both predictive modeling and scenario-based analysis across urban and rural counties.

---

## Modeling Framework
We train machine learning models to predict **next-year county-level opioid overdose mortality** using lagged covariates. Predictions are generated out-of-sample via 5-fold cross-validation, ensuring that every county-year observation is evaluated under held-out conditions.

To verify robustness, we employ multiple model classes:

- Gradient-boosted trees (XGBoost),
- Random Forests, and
- A multi-layer perceptron (MLP).

Across models, we observe a consistent pattern:  
**counties with the highest mortality are systematically under-predicted**, while low-mortality counties are over-predicted. This phenomenon persists across algorithms, suggesting it reflects underlying data structure rather than model choice.

---

## Risk as Persistent Predictive Instability
We define county-level **risk** not as a single-year prediction, but as the **accumulated difficulty models have in forecasting mortality over time**.

For each county, we compute a cumulative loss-based risk score derived from repeated out-of-sample prediction errors. Counties that are consistently under-predicted—indicating mortality trajectories exceeding what observed covariates would suggest—are interpreted as experiencing **structural epidemiological risk** not fully captured by standard indicators.

To emphasize recent shocks and evolving dynamics, we extend this definition using an **Exponentially Weighted Moving Average (EWMA)** of prediction errors. The EWMA formulation is particularly effective at highlighting post-2020 mortality spikes and persistent rural hotspots.

Empirically, EWMA-based risk stratification reveals:

- concentrated high-risk regions in central Appalachia,
- sustained predictive instability in specific rural counties,
- and meaningful separation between structurally high- and low-risk areas even after accounting for prescribing levels and socioeconomic indicators.

---

## Counterfactual Policy Simulations
Building on the risk framework, we conduct **counterfactual mortality predictions** to evaluate how modeled outcomes respond to changes in policy-relevant variables.

These simulations are **not causal effect estimates**. Instead, they are structured sensitivity analyses that explore how learned mortality relationships respond to controlled perturbations of inputs, holding other covariates fixed.

We examine counterfactual scenarios involving:

- reductions in opioid prescription dispensing rates,
- changes in unemployment, and
- changes in insurance coverage.

The magnitude of these interventions is informed by historically observed policy shifts (e.g., post-2016 prescribing guidelines), but the results are interpreted conservatively as **model-consistent responses**, not causal claims.

Crucially, we evaluate counterfactual responses **by risk strata**, revealing that:

- high-risk counties often exhibit different sensitivity profiles than low-risk counties,
- uniform national interventions can produce heterogeneous—and sometimes counterintuitive—effects across risk groups,
- and structural vulnerability continues to shape outcomes even under aggressive supply-side interventions.

<figure>
  <img
    src="/images/mlp_percent_change_rx.png"
    alt="Percentage change in mean predicted mortality, for a risk-informed RX reduction scenario, using a multi-layer perceptron (MLP) model."
    style="width:75%; height:auto;"
  >
  <figcaption>
    <em>Percentage change in mean predicted mortality, for a risk-informed RX reduction scenario, using a multi-layer perceptron (MLP) model.</em>
  </figcaption>
</figure>
  

<figure>
  <img
    src="/images/mlp_actual_change_rx.png"
    alt="Actual change in mean predicted mortality, for a risk-informed RX reduction scenario, using a multi-layer perceptron (MLP) model."
    style="width:75%; height:auto;"
  >
  <figcaption>
    <em>Actual change in mean predicted mortality, for a risk-informed RX reduction scenario, using a multi-layer perceptron (MLP) model.</em>
  </figcaption>
</figure>

---

## Why This Matters
This framework reframes opioid mortality modeling in two important ways:

1. **Risk is defined dynamically**, based on persistent model failure rather than static covariates alone.  
2. **Policy evaluation is stratified by structural risk**, highlighting where interventions may have limited or uneven impact.

For public health stakeholders—particularly in rural contexts—this approach supports:

- identification of counties experiencing entrenched, place-based risk,
- comparison of intervention strategies under realistic assumptions,
- and more nuanced interpretation of model outputs beyond headline prediction accuracy.

---

## Limitations and Ongoing Work
This analysis does not claim causal identification, and results should not be interpreted as estimates of intervention effectiveness. Ongoing work focuses on:

- incorporating additional lag structures and mediators,
- integrating causal and dynamic modeling frameworks,
- and refining risk definitions to support operational decision-making.

---

## Code and Reproducibility
Full code, data pipelines, and model diagnostics are available here:  
**GitHub:** https://github.com/ebrook27/Opioid_Risk
