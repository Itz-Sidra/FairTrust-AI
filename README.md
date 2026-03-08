# FairTrust AI — JEDI Code Compliance System

## Team

**Team:** Zen Devs  
**Competition:** PCCOE Hackathon 4.0 — PS9  
**Domain:** Hiring Systems — Gender, Race, Caste Bias

---

<div align="center">

![FairTrust AI](https://img.shields.io/badge/FairTrust-AI-1A2D4E?style=for-the-badge&logo=shield&logoColor=EBB255)
![Python](https://img.shields.io/badge/Python-3.9+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-2.x-000000?style=for-the-badge&logo=flask&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

**An end-to-end ethical AI auditing framework for bias detection in hiring algorithms**

*Evaluating fairness across 7 dimensions · Automated SHAP explainability · Role-based compliance reports*

[Features](#-features) · [Quick Start](#-quick-start) · [Installation](#-installation) · [Usage](#-usage) · [API Reference](#-api-reference) · [Architecture](#-architecture)

</div>

---

## Overview

**FairTrust AI** is an end-to-end ethical auditing framework that evaluates AI models for bias **before** deployment. It targets hiring algorithms — one of the highest-risk domains for algorithmic discrimination — and delivers a comprehensive **Ethical Score (0–1)** with a `PASS / CONDITIONAL / FAIL` certification verdict.

> *"Fairness cannot be assumed — it must be proven."*

### The Problem

- 70% of AI systems show measurable bias *(MIT, 2019)*
- Hiring algorithms reject qualified candidates based on gender, caste, and race — not qualifications
- India has no regulatory framework for AI ethics
- People affected by algorithmic decisions have no way to understand or challenge them

FairTrust AI is **the layer that sits between an AI model and the real world.**

---

## Features

| Feature | Description |
|---|---|
| **Automated Testing Pipeline** | Upload CSV → pipeline runs automatically → results in seconds |
| **7 Fairness Dimensions** | Demographic Parity, Equal Opportunity, Calibration, Disparate Impact, Counterfactual, Intersectional, Individual Fairness |
| **SHAP Explainability** | Feature importance charts with per-decision explanations |
| **3 Role-Based Reports** | Developer (technical), Regulator (compliance), End-User (plain English) |
| **Multi-Model Comparison** | Side-by-side audit comparison with delta scoring |
| **Admin Dashboard** | System health, alerts, user management, model registry |
| **Compliance Certification** | Auto-generated certificate with EU AI Act & GDPR readiness status |
| **Bias Instance Highlighting** | Concrete counterfactual pairs showing discriminatory decisions |

---

## Architecture

```
fairtrust-ai/
├── backend/
│   ├── app.py                    # Flask application entry point
│   ├── routes/
│   │   ├── dataset.py            # File upload & model registration
│   │   ├── evaluation.py         # Async evaluation pipeline
│   │   ├── dashboard.py          # Results dashboard API
│   │   ├── developer_report.py   # Technical report API
│   │   ├── regulator_report.py   # Compliance report API
│   │   ├── enduser_report.py     # Plain-language report API
│   │   ├── comparison.py         # Model comparison API
│   │   └── admin.py              # Admin dashboard API
│   ├── services/
│   │   ├── fairness.py           # 7-dimension fairness computation
│   │   ├── shap_explainer.py     # SHAP feature attribution
│   │   └── model_loader.py       # Pre-trained model loader & preprocessor
│   └── prisma/
│       └── schema.prisma         # Database schema
├── frontend/
│   ├── upload.html               # Dataset upload & configuration
│   ├── processing.html           # Real-time evaluation progress
│   ├── developerReport.html      # Technical report view
│   ├── regulatorReport.html      # Compliance & certification view
│   └── humanReport.html          # End-user plain-language view
├── models/
│   ├── hiring_model.pkl          # Pre-trained XGBoost/RF model
│   ├── scaler.pkl                # Feature scaler
│   ├── feature_order.json        # Expected feature order
│   └── numerical_cols.json       # Numerical column definitions
└── README.md
```

---

## Fairness Dimensions Tested

| # | Dimension | What It Checks |
|---|---|---|
| 1 | **Demographic Parity** | Equal positive outcome rates across groups |
| 2 | **Equal Opportunity** | Equal true positive rates across groups |
| 3 | **Calibration Bias** | Model confidence matches reality per group |
| 4 | **Disparate Impact** | Ratio of positive rates meets the 80% rule |
| 5 | **Counterfactual Fairness** | Prediction stability when protected attributes are flipped |
| 6 | **Intersectional Bias** | Compounded disadvantage at intersections (e.g. Female + SC caste) |
| 7 | **Individual Fairness** | Similar individuals receive similar predictions |

---

## Quick Start

```bash
# 1. Clone the repository
git clone https://github.com/Rishi-314/FairTrust-AI.git
cd FairTrust-AI

# 2. Set up Python environment
python -m venv venv
source venv/bin/activate          # Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Start the backend server
cd backend
python app.py

# 5. Open the app
Navigate to: http://127.0.0.1:5000/upload.html
```

---

## Installation

### Prerequisites

| Requirement | Version | Notes |
|---|---|---|
| Python | 3.9+ | 3.10 or 3.11 recommended |
| pip | 22+ | `pip install --upgrade pip` |
| Node.js | 18+ | Only if using Prisma / PostgreSQL |
| PostgreSQL | 14+ | Optional — in-memory store works without it |

---

### Step 1 — Clone the Repository

```bash
git clone https://github.com/Rishi-314/FairTrust-AI.git
cd fairtrust-ai
```

---

### Step 2 — Create a Virtual Environment

```bash
# Create environment
python -m venv venv

# Activate — macOS / Linux
source venv/bin/activate

# Activate — Windows (Command Prompt)
venv\Scripts\activate.bat

# Activate — Windows (PowerShell)
venv\Scripts\Activate.ps1
```

---

### Step 3 — Install Python Dependencies

```bash
pip install -r requirements.txt
```

If you don't have a `requirements.txt` yet, install the core packages manually:

```bash
pip install flask flask-cors pandas numpy scikit-learn xgboost shap fairlearn joblib openpyxl
```

<details>
<summary>Full dependency list (click to expand)</summary>

```txt
flask>=2.3.0
flask-cors>=4.0.0
pandas>=2.0.0
numpy>=1.24.0
scikit-learn>=1.3.0
xgboost>=1.7.0
shap>=0.42.0
fairlearn>=0.9.0
joblib>=1.3.0
openpyxl>=3.1.0
torch>=2.0.0          
```

</details>

---

### Step 4 — Configure Environment Variables

Create a `.env` file in the project root:

```env
# Database
DATABASE_URL=postgresql://user:password@localhost:5432/fairtrust

# Server settings
FLASK_ENV=development
FLASK_DEBUG=true
```

---

### Step 5 — Set Up the Database 

The system runs fully **in-memory by default** — no database required for evaluation or reporting. To enable persistent storage with PostgreSQL:

```bash
# Install Prisma CLI
npm install -g prisma

# Navigate to backend
cd backend

# Run migrations
npx prisma migrate dev --name init

# Generate Prisma client
npx prisma generate
```

---

### Step 6 — Pre-trained Models

Model artifacts are in the `models/` directory at the project root:

```
models/
├── hiring_model.pkl        # Trained classifier (XGBoost, RF, etc.)
├── scaler.pkl              # StandardScaler or similar
├── feature_order.json      # ["age", "education", "experience", ...]
└── numerical_cols.json     # ["age", "experience", "salary", ...]
```

---

### Step 7 — Start the Server

```bash
cd backend
python app.py
```

You should see:

```
✅ Pre-trained model loaded successfully

  Frontend : /path/to/fairtrust-ai/frontend
  Open     : http://127.0.0.1:5000/upload.html

 * Running on http://127.0.0.1:5000
```

Open your browser and go to: **http://127.0.0.1:5000/upload.html**

---

## Usage

### Evaluating a Model

#### Step 1 — Prepare Your Dataset

Your CSV/Excel/JSON file must contain:

- **Feature columns** — the inputs your model uses (age, education, experience, etc.)
- **Target column** — the ground truth label (e.g. `approved`, `outcome`, `label`)
- **Protected attribute columns** — the sensitive attributes to audit (e.g. `gender`, `race`, `caste`)

Example dataset structure:

```csv
age,education,experience,gender,race,caste,approved
32,Bachelor,5,Male,OBC,General,1
28,Master,3,Female,SC,SC,0
45,PhD,12,Male,General,General,1
...
```

#### Step 2 — Upload via the Web UI

1. Navigate to **http://127.0.0.1:5000/upload.html**
2. Drag & drop your dataset file (CSV, Excel, or JSON)
3. Enter the **Target Variable** name (e.g. `approved`)
4. Select **Sensitive Attributes** to test (Gender, Race, Caste, Age, etc.)
5. Adjust **Fairness Dimension weights** if desired
6. Choose your **Report Type**: Developer, Regulator, or End-User
7. Click **ANALYZE FAIRNESS →**

#### Step 3 — Monitor Progress

The processing page shows real-time progress across 7 steps:

```
Step 1: Data Validation
Step 2: EDA & Bias Detection
Step 3: Feature Engineering / Model Inference
Step 4: Fairness Analysis (all 7 dimensions)
Step 5: Model Evaluation (Accuracy, F1, ROC-AUC)
Step 6: SHAP Explanation
Step 7: Report Generation
```

#### Step 4 — View Your Report

After completion, you are automatically redirected to your chosen report:

| Report Type | Audience | Contents |
|---|---|---|
| **Developer** | ML Engineers | SHAP values, confusion matrix, per-attribute breakdown, raw fairness metrics |
| **Regulator** | Compliance Officers | Fairness contract, audit trail, certificate, EU AI Act / GDPR status |
| **End-User** | General Public | Plain-English verdict, bias indicators, recommended improvements |

---

### Using the REST API

You can also interact with FairTrust AI directly via its REST API.

#### Upload a Dataset

```bash
curl -X POST http://127.0.0.1:5000/datasets \
  -F "file=@/path/to/your/dataset.csv"
```

Response:
```json
{
  "dataset_id": "abc-123",
  "records": 32561,
  "columns": ["age", "education", "gender", "race", "approved"]
}
```

#### Register a Model

```bash
curl -X POST http://127.0.0.1:5000/models \
  -H "Content-Type: application/json" \
  -d '{"name": "HiringModelV2", "version": "2.0.0"}'
```

#### Start an Evaluation

```bash
curl -X POST http://127.0.0.1:5000/evaluate \
  -H "Content-Type: application/json" \
  -d '{
    "dataset_id": "abc-123",
    "model_id": "model-xyz",
    "target_variable": "approved",
    "sensitive_attributes": ["gender", "race", "caste"],
    "fairness_weights": {
      "individualFairness": 25,
      "groupFairness": 20,
      "demographicParity": 15,
      "calibrationError": 12,
      "disparateImpact": 10,
      "counterfactual": 10,
      "intersectional": 8
    },
    "report_type": "developer"
  }'
```

Response:
```json
{
  "evaluation_id": "eval-456",
  "status": "queued",
  "estimated_time": "2-3 minutes",
  "poll_url": "/evaluate/eval-456"
}
```

#### Retrieve Reports

```bash
# Developer report
curl http://127.0.0.1:5000/report/developer/eval-456

# Regulator report
curl http://127.0.0.1:5000/report/regulator/eval-456

# End-user report
curl http://127.0.0.1:5000/report/enduser/eval-456
```

---

## API Reference

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/datasets` | Upload dataset file |
| `POST` | `/models` | Register a model |
| `POST` | `/evaluate` | Start async evaluation |
| `GET` | `/evaluate/<id>` | Poll evaluation status |
| `GET` | `/evaluate` | List all evaluations |
| `GET` | `/report/developer/<id>` | Developer report |
| `GET` | `/report/regulator/<id>` | Regulator / certificate report |
| `GET` | `/report/enduser/<id>` | Plain-language end-user report |

---

## Understanding the Ethical Score

The Ethical Score is a **weighted average** of all 7 fairness dimensions, clamped to [0, 1]:

```
Ethical Score = mean([
    Individual Fairness,
    Group Fairness,
    1 - Demographic Parity Gap,
    Disparate Impact Ratio,
    1 - Calibration Error,
    Counterfactual Consistency,
    Intersectional Fairness
])
```

| Score Range | Verdict | Meaning |
|---|---|---|
| ≥ 0.80 | **PASS** | Model meets ethical standards for deployment |
| 0.60 – 0.79 | **CONDITIONAL** | Issues identified — conditional approval with remediation |
| < 0.60 | **FAIL** | Significant bias detected — do not deploy |

---

## Configuration

### Fairness Thresholds (Admin Panel)

Adjustable via `POST /admin/settings`:

```json
{
  "min_ethical_score": 0.75,
  "individual_fairness_min": 0.80,
  "disparate_impact_threshold": 0.80,
  "group_fairness_threshold": 0.80,
  "calibration_error_max": 0.05,
  "email_notifications": true,
  "slack_integration": false
}
```

### Supported File Formats

| Format | Extension | Notes |
|---|---|---|
| CSV | `.csv` | Recommended |
| Excel | `.xlsx`, `.xls` | Multi-sheet not supported |
| JSON | `.json` | Array of objects |

---

<div align="center">

*FairTrust AI — The layer between an AI model and the real world.*

</div>