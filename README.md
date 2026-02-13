# Industrial Data Science Portfolio

## Overview

This repository presents selected data science projects focused on scalable modeling, analytics automation, and decision-support systems.

All production codebases are private due to corporate restrictions.  
This portfolio outlines architecture, modeling approaches, and technical solutions implemented in production environments.

---
## Table of Contents
- [1. Geo Store Potential Model](#geo-store-potential-model)
- [2. Store-Level Daily Sales Forecasting](#store-level-daily-sales-forecasting)
- [3. AI-Assisted Interview Evaluation](#ai-assisted-interview-evaluation)
- [4. KPI Insight Automation (LLM-enhanced)](#kpi-insight-automation-llm-enhanced)
- [5. Product Complementarity & Similarity Model](#product-complementarity-similarity-model)
- [6. Multi-Timeframe Quant Model](#multi-timeframe-quant-model)
- [Technical Challenges & Engineering Solutions](#technical-challenges-engineering-solutions)

<a id="geo-store-potential-model"></a>
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
- Feature dataset prepared for scoring and comparative analysis

**Scale**
City-level modeling with thousands of hex cells and competitor objects.

**Impact**
Enabled structured comparison of store locations prior to investment decisions.

---
<a id="store-level-daily-sales-forecasting"></a>
## 📊 2. Store-Level Daily Sales Forecasting

**Objective**  
Build a forecasting pipeline for daily store sales.

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
Data ingestion → Cleaning → Feature engineering → Model training → Accuracy validation → BI export

**Impact**
Established automated forecasting workflow supporting operational planning and financial monitoring.

---
<a id="ai-assisted-interview-evaluation"></a>
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
Standardized evaluation process with consistent competency-based scoring logic.

---
<a id="kpi-insight-automation-llm-enhanced"></a>
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
- LLM-generated natural language explanations integrated into dashboards
  
**Pipeline**
SQL extracts (joins/filters) → Python ETL (dedup/trim) → KPI pre-calculation → compression/encoding for token reduction → prompt assembly → LLM call (rate-limit handling / API key rotation) → JSON insights → BI integration

**Impact**
Reduced manual analytical workload and improved turnaround time for managerial review.

---
<a id="product-complementarity-similarity-model"></a>
## 🛒 5. Product Complementarity & Similarity Model

**Objective**  
Identify complementary and substitute products using large-scale transaction data.

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
- Statistical and business-rule filtering

**Scale**
Tens of millions of transaction rows  
Multi-GB files processed with memory-aware architecture

**Key Engineering Shift**
Transitioned from dense O(n²) computations to sparse-matrix architecture optimized for retail-scale datasets.

---
<a id="multi-timeframe-quant-model"></a>
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
- Strategy-level logging

**Evaluation**
- Win rate  
- Yearly return distribution  
- Time-in-market  
- Risk diagnostics
- Funnel by events 
---
<a id="technical-challenges-engineering-solutions"></a>
## Technical Challenges & Engineering Solutions

### 🗺 Geo Store Potential Model

**Challenge: Heavy geospatial computations & API limits**  
Large map areas, competitor density modeling, and external API requests (OSM / Overpass) caused performance bottlenecks.

**Solutions:**
- Spatial partitioning using H3 hex grid
- Radius-based query restriction instead of full-area scans
- Request batching & API throttling
- Local caching of geodata
- Incremental recomputation instead of full rebuild

**Result:**  
Significant reduction in API calls and computation time while preserving model accuracy.

---

### 🛒 Product Complementarity & Similarity Model

**Challenge: Memory overflow due to dense O(n²) computations**  
Pairwise similarity across thousands of SKUs and millions of transactions exceeded RAM capacity.

**Solutions:**
- Sparse matrix representation (COO → CSR)
- Chunk-based processing with Dask
- Cosine similarity in complementarity space
- Threshold filtering to reduce candidate pairs

**Result:**  
Multi-GB transaction datasets processed efficiently without memory overflow.

---

### 📊 Store-Level Forecasting

**Challenge: Sparse historical data for new or low-activity stores**

**Solutions:**
- Analog-store matching by region/format
- Surrogate modeling
- Automated validation pipeline

**Result:**  
Stable forecasting coverage across heterogeneous store portfolio.

---

### 📈 KPI Insight Automation (LLM-Enhanced)

**Challenge: Large context size & API cost control**

**Solutions:**
- SQL-side aggregation & KPI pre-calculation
- Python preprocessing (deduplication, trimming irrelevant fields)
- Token-efficient encoding before prompt assembly
- Multi-key rotation & rate-limit handling
- Structured JSON output for BI integration

**Result:**  
Cost-efficient, scalable AI insight layer embedded into BI dashboards.

---

### 🤖 Interview Evaluation

**Challenge: Unstructured video input & inconsistent scoring**

**Solutions:**
- Video → audio extraction
- Speech-to-text transcription pipeline
- Structured competency schema
- JSON-based standardized evaluation

**Result:**  
Consistent and reproducible candidate assessment workflow.

---

## Positioning

This portfolio reflects applied data science work focused on:

- Scalable computation
- Memory-aware modeling
- Hybrid rule-based and statistical systems
- End-to-end pipeline implementation
- Business-integrated analytics
