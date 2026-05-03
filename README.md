# Predicting Business Star Ratings from Early Review Text Using NLP

---

## Overview

This project builds a proactive machine learning pipeline that predicts the long-term star rating of a food business on Yelp using only its first 3 to 5 customer reviews. Rather than waiting for ratings to decline, the system enables business owners to detect early warning signs and act before reputational damage occurs. Insights are delivered through an interactive Power BI dashboard featuring sentiment trends, risk alerts, SHAP-based explanations, and a What-If simulator.

---

## Problem Statement

Online review platforms like Yelp reflect customer sentiment retrospectively. By the time a business owner identifies a pattern of negative feedback, the reputational damage has already happened and customer churn may have begun. This project addresses that gap by transforming review monitoring from a reactive process into a proactive one — using NLP and classification models to predict long-term outcomes from the very first reviews a business receives.

---

## Data Sources

| Source | Description |
|---|---|
| [Yelp Open Dataset](https://www.yelp.com/dataset) | Primary dataset containing over 8 million anonymized reviews (`review.json`) and business metadata (`business.json`) |

**Filtering applied:**
- Retained only food-related SMEs (restaurants, cafes, bakeries, etc.)
- Excluded top 100 most-reviewed chains
- Kept businesses with 20 to 750 reviews
- Reviews from 2015 onwards only
- Excluded users with fewer than 3 reviews and reviews under 5 words
- Final dataset: ~1.93 million reviews across 65 structured columns

---

## Models Used

| Model | Accuracy | Notes |
|---|---|---|
| Logistic Regression | 56% | Baseline; performed best on extreme ratings (1-star and 5-star) |
| Random Forest | 57% | Better generalization across mid-range classes; reduced overfitting |
| **XGBoost** | **61%** | **Best overall — selected for deployment** |

XGBoost was chosen for its superior balance across precision, recall, and F1 scores, and its ability to handle both structured and unstructured features efficiently. Model outputs are interpreted using **SHAP (SHapley Additive exPlanations)** to provide feature-level explanations for each prediction.

**Key predictive features identified via SHAP:**
- Sentiment score (VADER)
- Review length
- Useful / funny / cool vote counts
- Adjective and adverb density
- City and state (regional sentiment variation)

---

## SDG Alignment

| Goal | Relevance |
|---|---|
| **SDG 8 – Decent Work and Economic Growth** | Helps SMEs improve service quality, retain customers, and protect local employment through early feedback action |
| **SDG 9 – Industry, Innovation and Infrastructure** | Embeds AI-driven analytics and explainability tools into SME workflows, democratizing access to data-driven innovation |

---

## Tech Stack

| Category | Tools |
|---|---|
| Language | Python 3 |
| Data Processing | Pandas, NumPy, ast, datetime |
| NLP | NLTK, VADER (vaderSentiment), TextBlob, TF-IDF |
| Modelling | Scikit-learn, XGBoost |
| Explainability | SHAP |
| Visualization | Power BI, Matplotlib, Seaborn |
| Notebooks | Jupyter |
| Version Control | Git, GitHub |

---

## How to Run

**1. Clone the repository**
```bash
git clone https://github.com/YOUR_USERNAME/yelp-review-rating-predictor.git
cd yelp-review-rating-predictor
```

**2. Install dependencies**
```bash
pip install -r requirements.txt
```

**3. Download the Yelp dataset**

Download `review.json` and `business.json` from [https://www.yelp.com/dataset](https://www.yelp.com/dataset) and place them in a `/data` folder.

**4. Run the notebooks in order**
```bash
jupyter notebook notebooks/ClassificationV1.ipynb
jupyter notebook notebooks/6611_Classification_XGbooster.ipynb
```

> **Note:** Due to the size of the raw Yelp dataset (6.7M+ entries), initial preprocessing steps may be memory-intensive. The notebooks include filtering steps to reduce this to a manageable working subset.

---

## Project Report

The full technical report covering the Data Value Map, methodology, EDA, model evaluation, SHAP interpretation, Business Model Canvas, and future enhancements is available here:

📄 [`report/IS6611_IT_Artefact_V3_Report.pdf`](report/IS6611_IT_Artefact_V3_Report.pdf)

---

## Authors

**Group 6 — IS6611, MSc Business Analytics, University College Cork (2025)**

| Name |
|---|
| Aida F. George |
| Aiyman Mohammed |
| Aravind Ravichandran |
| Dheeraj Ravi |
| Mrunal Howale |
| Prashanth Punniyaseelan |
