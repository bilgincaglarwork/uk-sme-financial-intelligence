# UK SME Financial Intelligence — Proprietary Research

**Author:** Bilgin Caglar, MBCS | Founder, [Notabyte Limited](https://notabyte.co.uk) (Companies House: 12567215)  
**Product:** [Get Clarity](https://clarityuk.app) — AI-powered accounting for UK sole traders & freelancers  
**Date:** April 2026  
**Purpose:** Proprietary analytical IP developed as part of the EIS Advance Assurance application for Get Clarity

---

## Overview

This repository contains two independent analytical notebooks developed to demonstrate the data science and financial intelligence capabilities underpinning Get Clarity's product architecture. The analyses were conducted using real UK SME financial datasets and a synthetic UK business dataset to establish sector benchmarks, risk models, and valuation frameworks — all of which directly inform Get Clarity's AI Copilot and HMRC MTD compliance features.

---

## Notebooks

### 1. `UK_SME_SYNTHETIC_ANALYSIS.ipynb`
**Dataset:** Synthetic UK SME dataset (5 merged datasets: Businesses, Credit, COVID, Loan, Individual)  
**Scope:** 1,000 companies | 6 analytical sections

| Section | Description |
|---|---|
| Data Engineering | 5-dataset merge pipeline, missing value imputation, integrity validation |
| EDA — Sector Benchmarking | Revenue, credit score, profit margin, debt ratio by sector |
| Feature Engineering | Company age, revenue growth, loan default flag, debt load classification |
| Resilience Score | Proprietary composite metric (0–100) quantifying COVID shock-absorption capacity |
| Risk Modelling | Random Forest default prediction — **AUC: 0.827** (5-fold cross-validated) |
| Corporate Valuation | Sector-adjusted Enterprise Value model with resilience adjustment (±15%) |
| Workforce Intelligence | Self-employment rates, qualification profiles, geographic distribution |

**Key Output: Resilience Score**  
A proprietary metric that became the single most important predictor of loan default (feature importance: 0.261). Derived from pandemic-period trading continuity, post-pandemic recovery, debt load, and default status — this score is directly implementable as a real-time risk signal within Get Clarity's HMRC MTD data pipeline.

**Model Performance:**

| Model | AUC | CV AUC (5-fold) |
|---|---|---|
| Random Forest (balanced) | 0.827 | Validated |
| Logistic Regression (balanced) | 0.551 | Baseline |

---

### 2. `UK_SME_ANALYSIS.ipynb`
**Dataset:** HMRC-aligned real UK SME financial data (Feb 2018 – Feb 2023)  
**Scope:** Wide-format 250-column dataset, melted and pivoted to long format | 77 analytical cells

| Section | Description |
|---|---|
| Data Cleaning | Type conversion, null imputation via sectoral median, column standardisation |
| Data Restructuring | Wide-to-long melt transformation (250 cols → normalised structure) |
| Regional Analysis | Turnover by UK region — HMRC MTD compliance risk mapping |
| Sectoral Analysis | Profit margin, outlier detection (IQR + Z-score), top sectors by revenue |
| HMRC Risk Signals | Tax efficiency ratio, sectoral risk flags aligned with HMRC audit profiles |
| Revenue Growth | Year-on-year proxy growth rate per SME entity |
| Allowable Expense Distribution | HMRC-compliant expense category breakdown |
| Seasonality Analysis | Monthly revenue patterns — cash flow forecasting input |
| GetClarity Insight Summary | Strategic intelligence layer connecting all findings to product features |

---

## Analytical Highlights

### Resilience Score Framework
```
Resilience Score (0–100) =
    pandemic_trading_rate × 40
  + recovery_trading_rate × 40
  + (1 − high_debt_flag)  × 10
  + (1 − loan_default_flag) × 10

→ Normalised to 0–100 scale
→ Single strongest predictor of default (importance: 0.261)
```

### Three-Tier Market Segmentation

| Tier | Count | Avg EV | Avg Resilience | Get Clarity Plan |
|---|---|---|---|---|
| 🌟 Resilience Stars | 233 | £404,825 | 92.22 | Pro / Business |
| 🔵 Stable Core | 544 | £419,554 | 85.03 | Starter / Pro |
| 🔴 Risk Cluster | 223 | £392,052 | 46.78 | Free → Starter |

### EIS Relevance
- **Predictive moat:** AUC 0.827 confirms default risk is measurable from data already in Get Clarity's HMRC MTD pipeline
- **Proprietary IP:** Resilience Score + real-time MTD data creates a forward-looking financial intelligence layer unavailable in any existing UK SME accounting tool
- **Market scale:** Methodology applicable to UK's 5.5M SME population

---

## Technology Stack

```
Python 3.11+
pandas, numpy
matplotlib, seaborn
scikit-learn (RandomForestClassifier, LogisticRegression, StandardScaler)
scipy
```

---

## Installation

```bash
git clone https://github.com/bilgincaglarwork/uk-sme-financial-intelligence
cd uk-sme-financial-intelligence
pip install -r requirements.txt
jupyter notebook
```

---

## Data Sources

- UK SME Synthetic Dataset — synthetic business financial statistics (Kaggle)
- HMRC-aligned UK SME financial data — real turnover/profit/tax records (Kaggle)
- Sector EV/Revenue multiples — BDO UK SME Valuation Report 2023; Deloitte UK Private Company Index; Beauhurst Deal Data 2022–2024

---

## About Get Clarity

Get Clarity (clarityuk.app) is an AI-powered accounting platform built for UK sole traders and freelancers. It combines HMRC Making Tax Digital (MTD) compliance, real-time bank feeds via Open Banking, AI contract analysis, and an intelligent Copilot — all in a single mobile-first application.

The analytical frameworks developed in this repository directly inform Get Clarity's:
- AI risk flagging engine
- Sector benchmarking dashboard
- Proactive cash flow insights
- HMRC compliance scoring

**Notabyte Limited** | Companies House: 12567215 | ICO: ZC108811  
**BCS MBCS** | Membership No: 995176973  
**HMRC MTD Production Application** | Reference: 2026-EMV042

---

*This research was conducted independently by Notabyte Limited as proprietary analytical IP. It is submitted as supporting evidence for the EIS Advance Assurance application for Get Clarity.*
