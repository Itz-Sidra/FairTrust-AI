# FairTrust AI — JEDI Code Compliance System
### Ethical AI Auditing Framework | PS9 | PCCOE Hackathon 4.0

**Team:** Zen Devs  
**Domain:** Hiring Systems (Gender, Race, Caste Bias)  
**Stack:** Python · PyTorch · Flask · HTML/CSS/JS · Vercel

---

## What This Does

FairTrust AI is an end-to-end ethical auditing framework that evaluates AI models for bias before deployment. It targets hiring algorithms — one of the highest-risk domains for algorithmic discrimination.

You upload a dataset and model predictions. The system automatically runs bias tests across 7 fairness dimensions, explains individual decisions using SHAP, and generates role-specific compliance reports for developers, regulators, and end users.

**The output:** An Ethical Score (0–1) with a PASS / CONDITIONAL / FAIL certification verdict.

---

## The Problem

70% of AI systems show measurable bias (MIT, 2019). Hiring algorithms reject qualified candidates based on gender, caste, and race — not qualifications. India has no regulatory framework for AI ethics. People affected by these decisions have no way to understand or challenge them.

FairTrust AI is the layer that sits between an AI model and the real world.

---

## Domain

**Hiring Systems** — auditing income prediction algorithms used in candidate screening.

Protected attributes tested: Gender, Race, Caste (via proxy)

---

## Fairness Dimensions Tested (7)

| Dimension | What It Checks |
|---|---|
| Demographic Parity | Equal positive outcome rates across groups |
| Equal Opportunity | Equal true positive rates across groups |
| Calibration Bias | Model confidence matches reality per group |
| Disparate Impact | Ratio of positive rates meets 80% rule |
| Counterfactual Fairness | Prediction stability when protected attributes are flipped |
| Intersectional Bias | Compounded disadvantage at intersections (e.g. Female + SC caste) |
| Individual Fairness | Similar individuals receive similar predictions |

**Spec compliance:** Implements Demographic Parity, Equal Opportunity, Calibration, and Transparency — exceeding the minimum requirement of two dimensions.

---

## Key Features

**Automated Testing Pipeline**
Upload CSV → pipeline runs automatically → results generated in seconds. No manual configuration required after attribute selection.

**Multi-Model Simultaneous Comparison**
Audits four models in parallel: XGBoost, Neural Network, Logistic Regression, Random Forest. Scores are compared side by side on the results dashboard.

**SHAP Explainability**
Shows exactly why a model made a specific decision. Feature contribution charts for individual decisions. Three report types generated automatically.

**Visual Scorecard**
Each fairness criterion gets an explicit PASS or FAIL badge. Color coded. Immediately readable by non-technical stakeholders.

**Specific Bias Instance Highlighting**
Surfaces concrete examples of discriminatory decisions — not just aggregate statistics. Shows counterfactual pairs where identical qualifications led to different outcomes based on protected attributes.

**Role-Based Reports**
- Developer: SHAP values, confusion matrices, feature importance, raw audit data
- Regulator: Compliance status, disparate impact ratios, audit trail, versioned model card
- End User: Plain English decision explanation, key factors, appeal mechanism

*FairTrust AI — The layer between an AI model and the real world.*
