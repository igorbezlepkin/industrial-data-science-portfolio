# Industrial Data Science Portfolio

## Overview

This repository presents selected industrial-grade data science projects focused on scalable modeling, analytics automation, and decision-support systems.

All production codebases are private due to corporate restrictions.  
This portfolio describes architecture, modeling approaches, and technical solutions.

---

## 🗺 1. Geo Store Potential Model

**Objective**  
Estimate commercial potential of store locations using geospatial and gravity-based modeling.

**Tech Stack**
- Python 3.9
- GeoPandas
- H3 spatial indexing
- OSMnx / Overpass API
- Huff gravity model

**What Was Built**
- H3 hex-based demand estimation
- Competitor density modeling
- Customer flow redistribution using gravity logic
- Feature dataset for ML-ready scoring

**Scale**
City-level modeling with thousands of hex cells and competitor objects.

**Impact**
Enabled data-driven comparison of store locations before investment decisions.

---

## 📊 2. Store-Level Daily Sales Forecasting

**Objective**  
Build a scalable forecasting pipeline for daily store sales.

**Tech Stack**
- Python
- pandas
- statsmodels (SARIMAX)
- SQL

**Model**
SARIMAX (1,1,1)x(1,1,1,12)  
Holidays as exogenous variables  
Analog-store substitution for sparse data

**Pipeline**
Data → Cleaning → Feature engineering → Model → Accuracy validation → BI export

**Impact**
Automated forecasting for operational planning and financial control.

---

## 🤖 3. AI-Assisted Interview Evaluation

**Objective**  
Reduce subjectivity in hiring decisions.

**Tech Stack**
- Python
- Video-to-text transcription
- LLM API
- JSON structured evaluation
- Streamlit prototype

**Pipeline**
Video interview → Transcription → Competency extraction → Structured scoring → Summary generation

**Impact**
Standardized evaluation process with consistent competency scoring.

---

## 📈 4. KPI Insight Automation (LLM-enhanced)

**Objective**  
Automate explanation of KPI deviations inside BI dashboards.

**Tech Stack**
- SQL Server
- Power BI (DAX)
- Python
- LLM API

**Approach**
- KPI deviation detection
- Business rule triggers
- LLM-generated natural language explanations

**Impact**
Reduced manual analytical workload and accelerated managerial decision-making.

---

## 🛒 5. Product Complementarity & Similarity Model

**Objective**  
Identify complementary and substitute products from large-scale transaction data.

**Tech Stack**
- Python 3.9
- Dask
- Pandas
- SciPy Sparse (COO/CSR)
- NumPy
- Scikit-learn

**Architecture**
- Sparse matrix A (Product × Basket)
- Complementarity matrix via normalized co-purchase structure
- Cosine similarity in complementarity space
- Statistical + business filtering

**Scale**
Tens of millions of transaction rows  
Multi-GB files processed without memory overflow

**Key Engineering Shift**
Replaced dense O(n²) computations with sparse-matrix architecture optimized for retail-scale datasets.

---

## 📉 6. Multi-Timeframe Quant Model

**Objective**  
Evaluate event-based trading strategies using multi-timeframe context.

**Tech Stack**
- Python
- Backtrader
- pandas

**Features**
- 4H + Daily timeframe integration
- EMA, RSI, MACD, ATR filters
- Event-driven signal logic
- Strategy funnel logging

**Evaluation**
Win rate  
Yearly return distribution  
Time-in-market  
Risk diagnostics

---

## Technical Challenges & Engineering Solutions

### Memory Constraints
Solved via sparse matrix representation + chunk-based Dask processing.

### O(n²) Similarity Explosion
Reduced using sparse multiplication + threshold filtering.

### Sparse Historical Data
Implemented analog-based surrogate modeling.

### Subjective Decision Bottlenecks
Structured LLM-based JSON scoring systems.

---

## Positioning

This portfolio reflects production-oriented data science focused on:

- Scalable computation
- Memory-aware modeling
- Hybrid rule-based + ML systems
- End-to-end pipeline engineering
- Business-integrated analytics
