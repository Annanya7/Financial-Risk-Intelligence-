# Financial-Risk-Intelligence-


# Transactional Fraud Detection & Risk Intelligence Pipeline
This repository implements a modular, scalable fraud detection framework that ingests financial transaction data, performs feature engineering, calculates risk scores, and applies unsupervised anomaly detection to flag potentially fraudulent transactions. It also includes geospatial visualization of flagged activities.

# 🔬 Key Modules & Capabilities

## 1️⃣ Data Ingestion & Integration
Dynamic CSV Aggregation: Automatically reads and concatenates multiple CSVs from within a ZIP archive into a unified DataFrame.

Source Traceability: Each transaction is tagged with its originating file to maintain data lineage.

## 2️⃣ Data Cleaning & Standardization
Robust Preprocessing Pipeline:

Column normalization (snake_case standardization).

Date parsing & coercion (handling multi-format timestamps).

Data integrity checks (dropping nulls, coercing numerics).

## 3️⃣ Feature Engineering & Enrichment
Temporal Features:

Hour of day, day of week, weekend/weekday, night-time flags.

Transaction Behavior Patterns:

Velocity metrics: transaction count, total amount, daily averages per card.

Cross-border indicators: foreign currency/merchant flags.

Risk heuristics: round amounts, surcharge presence, high-value flags.

State-Level Profiling:

Transaction density per US state.

Statistical baselines (mean/std) for outlier detection at the state level.

## 4️⃣ Risk Scoring Engine
Rule-Based Risk Aggregation:

Scores are derived from compound heuristics, such as:

Large refunds

Multi-country transactions

High-value foreign transactions

Unusual transaction hours and delays

Weighted Risk Attribution:

Risk factors are assigned proportional weights to quantify relative fraud likelihood.

## 5️⃣ Machine Learning: Anomaly Detection
Isolation Forest Algorithm:

Trained on scaled numerical features for unsupervised fraud detection.

Outliers are flagged based on anomaly scores and ensemble voting.

Hybrid Risk Integration:

Combines rule-based risk scores with Isolation Forest predictions for enhanced fraud probability estimation.

## 6️⃣ Fraud Flagging & Root Cause Analysis
Explainable Anomalies:

Each flagged transaction is annotated with reason codes explaining why it was flagged (e.g., "Large Refund", "Multiple Countries", "High Velocity").

Fraud Probability Scoring:

Merges anomaly scores with domain risk scores for calibrated fraud likelihood.

## 7️⃣ Geospatial Intelligence
US Merchant Mapping:

Leverages state-level coordinates to plot flagged transactions on an interactive Folium map.

Supports quick hotspot detection of suspicious clusters geographically.

##  Technologies Used
Pandas & NumPy: Data manipulation & analysis.

scikit-learn: Isolation Forest, StandardScaler, performance metrics.

Folium & GeoPy: Interactive fraud mapping & geospatial processing.

Matplotlib & Seaborn: Visual analytics & diagnostics.

tqdm: Smart progress visualization.

Python Standard Libraries: zipfile, datetime, warnings, os.

## 📊 Why This Matters
This pipeline is designed for real-world fintech and banking environments, providing:

✅ Proactive Fraud Detection before losses escalate.
✅ Explainability & Auditability for compliance and trust.
✅ Scalable Engineering supporting batch or streaming workflows.
✅ Geospatial Awareness to detect fraud hotspots and trends.
