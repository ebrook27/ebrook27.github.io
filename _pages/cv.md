---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

## Education
**Ph.D. in Mathematics**  
University of Tennessee, Knoxville — *Expected 2026*  
Dissertation: *Opioid overdose mortality risk quantification and counterfactual policy simulation* (working title)

**B.S. in Mathematics**  
Birmingham–Southern College, 2018

**B.S. in Physics**  
Birmingham–Southern College, 2018

---

## Research & Applied Projects
**Opioid Overdose Mortality Modeling and Policy Counterfactuals**  
- Developed end-to-end county-level modeling pipelines for opioid overdose mortality forecasting and risk stratification  
- Introduced a model-based risk framework leveraging persistent predictive instability  
- Designed counterfactual simulation workflows to evaluate policy-relevant interventions (prescribing, insurance coverage, unemployment)  
- Integrated multi-source longitudinal data (SVI, mortality, prescriptions, unemployment, insurance) with reproducible ETL pipelines  

**Physics-Informed Time-Series Modeling for Additive Manufacturing**  
- Built nonlinear state-space models for online temperature prediction in Additive Friction Stir Deposition  
- Implemented Extended Kalman Filter (EKF)–based state estimation under noisy measurements  
- Conducted diagnostics on bias, stability, and regime-dependent model mismatch  

---

## Publications
**Saturn’s Multiple, Variable Periodicities: A Dual-Flywheel Model of Thermosphere–Ionosphere–Magnetosphere Coupling**  
*Journal of Geophysical Research: Space Physics*  
https://doi.org/10.1029/2019JA026870

---

## Technical Skills
**Strong:** Python, R, LaTeX, Git  
**Working knowledge:** SQL  
**Familiar:** Bash  

---

## Teaching & Communication
University of Tennessee, Knoxville  
Instructor of Record:  
- **Finite Mathematics** — 3 semesters  
- **Statistical Reasoning** — 1 academic year  

Consistently received strong student evaluations, with emphasis on clarity, interpretation, and communication of quantitative concepts to non-technical audiences.

---

## Talks & Presentations
<ul>
{% for post in site.talks reversed %}
  {% include archive-single-talk-cv.html %}
{% endfor %}
</ul>
