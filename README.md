# Spotify-Song-Popularity-Prediction
Spotify Song Popularity Prediction is a production-style mini project that predicts the likelihood a Spotify track becomes a hit based on core audio features. It showcases the full DS workflow—data prep, model training (Logistic Regression, Random Forest, XGBoost), evaluation, and an interactive Streamlit dashboard—plus optional deployment on Snowflake Streamlit Apps.

# Project Overview
Binary Classification (Tabular): Predict hit vs non-hit using danceability, energy, valence, and tempo.
Model Triage: Compare Logistic Regression, Random Forest, and XGBoost side-by-side.
Interactive App: Streamlit UI with sliders, probability outputs, feature importance, and benchmarks vs Top-100 averages.
Deployable: Runs locally or inside Snowflake (no web server to manage).

# Tech Stack
Python 3.9+
Streamlit (interactive dashboard)
scikit-learn, XGBoost, pandas, numpy
joblib (model artifacts)
Spotipy for data collection
Snowflake Streamlit Apps for deployment

# Data
Source: Spotify audio features from public playlists (or a synthetic fallback so the project always runs).
Label: hit = 1 if popularity ≥ threshold (default 80).
Features: danceability, energy, valence, tempo.

# Repository Structure
HitCast/
├── app.py                           # Streamlit app (interactive dashboard)
├── notebooks/
│   └── 01_build_dataset.ipynb       # Build data & train models
├── data/
│   └── raw_tracks.csv               # Created by notebook (kept small for demo)
├── models/
│   ├── model_logreg.joblib
│   ├── model_rf.joblib
│   └── model_xgb.joblib
├── .streamlit/
│   └── config.toml                  # (Optional) app theming
├── requirements.txt
├── .gitignore
└── README.md

# Setup & Installation
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
pip install -r requirements.txt

# Build Data & Train Models
Open and run the notebook:
notebooks/01_build_dataset.ipynb
This will:
Create data/raw_tracks.csv
Train LR / RF / XGB
Save artifacts to models/
If Spotify API isn’t available, the notebook automatically uses a fallback generator so training completes without errors.

# Launch the Dashboard
streamlit run app.py
Adjust sliders (danceability, energy, valence, tempo).
See predicted hit probability from LR / RF / XGB.
Compare your inputs to the Top-100 and All-data averages.
View feature importance (RF) for quick interpretability.

# Results
Metrics vary by dataset; these are representative.
Class balance (hit=1): ~0.82
Logistic Regression: acc 0.69 · f1 0.78 · roc_auc 0.79
Random Forest: acc 0.77 · f1 0.87 · roc_auc 0.67
XGBoost: acc 0.78 · f1 0.87 · roc_auc 0.59
Takeaway: RF/XGB yield strong F1/accuracy; LR offers best calibration/ROC and is most interpretable. The app exposes all three for informed trade-offs.

# Deploy on Snowflake Streamlit Apps
In Snowflake, go to Projects → Streamlit → + Streamlit App.
Upload app.py, data/raw_tracks.csv, and models/*.joblib as app files (or stage them).
Select a warehouse (e.g., XSMALL).
Run and share the app URL.

# License
MIT License — feel free to use, learn from, and adapt this project with attribution.
# HitCast — Spotify Song Hit Prediction
**End-to-End ML App with Streamlit (optional Snowflake deployment)**  
**License:** MIT

> Predict whether a Spotify track will be a *hit* using core audio features. Train multiple models (Logistic Regression, Random Forest, XGBoost), evaluate them, and interact with predictions in a Streamlit dashboard. The same app can run locally or inside **Snowflake Streamlit Apps**.

---

## 📌 Table of Contents
1. [Overview](#overview)  
2. [Features](#features)  
3. [Tech Stack](#tech-stack)  
4. [Project Structure](#project-structure)  
5. [Setup](#setup)  
6. [Build Data & Train](#build-data--train)  
7. [Run the App](#run-the-app)  
8. [Results (Example)](#results-example)  
9. [Deploy on Snowflake (Optional)](#deploy-on-snowflake-optional)  
10. [Why This Project (For Recruiters)](#why-this-project-for-recruiters)  
11. [Roadmap](#roadmap)  
12. [License](#license)

---

## Overview
**HitCast** frames hit prediction as a **binary classification** problem using four Spotify audio features — `danceability`, `energy`, `valence`, and `tempo`. The pipeline includes:

- Robust data generation (uses real Spotify features if available; otherwise a **deterministic demo dataset** so the project always runs)
- Model triage with **Logistic Regression**, **Random Forest**, and **XGBoost**
- An **interactive Streamlit app** for what-if analysis and stakeholder demos
- Optional deployment on **Snowflake Streamlit Apps** (no web server to manage)

---

## Features
- 🧠 **Model comparison**: LR / RF / XGB probabilities side-by-side  
- 🎚️ **Interactive sliders** for audio features  
- 📊 **Top-100 vs All-data** benchmarks in-app  
- 🔍 **Feature importance** (RF) for interpretability  
- 🧪 **Always runnable**: synthetic fallback if Spotify access/region is limited

---

## Tech Stack
- **Python 3.9+**, **pandas**, **numpy**  
- **scikit-learn**, **xgboost**, **joblib**  
- **Streamlit** (UI)  
- *(Optional)* **spotipy** (Spotify data collection)  
- *(Optional)* **Snowflake Streamlit Apps** (deployment)

---

## Project Structure








