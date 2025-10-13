# Spotify Song Hit Prediction
**End-to-End ML App with Streamlit** 
**Snowflake deployment**  
**License:** MIT

>Spotify Song Popularity Prediction is a production-style mini project that predicts the likelihood a Spotify track becomes a hit based on core audio features. It showcases the full DS workflow—data prep, model training (Logistic Regression, Random Forest, XGBoost), evaluation, and an interactive Streamlit dashboard—plus optional deployment on Snowflake Streamlit Apps. **Snowflake Streamlit Apps**.

---

## Project Overview
**HitCast** frames hit prediction as a **binary classification** problem using four Spotify audio features — `danceability`, `energy`, `valence`, and `tempo`. The pipeline includes:

- Robust data generation (uses real Spotify features if available; otherwise a **deterministic demo dataset** so the project always runs)
- Model triage with **Logistic Regression**, **Random Forest**, and **XGBoost**
- An **interactive Streamlit app** for what-if analysis and stakeholder demos
- Deployment on **Snowflake Streamlit Apps** (no web server to manage)

---

## Features
- **Model comparison**: LR / RF / XGB probabilities side-by-side  
- **Interactive sliders** for audio features  
- **Top-100 vs All-data** benchmarks in-app  
- **Feature importance** (RF) for interpretability  
- **Always runnable**: synthetic fallback if Spotify access/region is limited

---

## Tech Stack
- **Python 3.9+**, **pandas**, **numpy**  
- **scikit-learn**, **xgboost**, **joblib**  
- **Streamlit** (UI)  
- **spotipy** (Spotify data collection)  
- ***Snowflake Streamlit Apps** (deployment)

---

## Project Structure
HitCast/
├─ app.py # Streamlit dashboard
├─ notebooks/
│ └─ 01_build_dataset.ipynb # Build data + train models (deterministic fallback)
├─ data/
│ └─ raw_tracks.csv # Created by notebook (small demo)
├─ models/
│ ├─ model_logreg.joblib
│ ├─ model_rf.joblib
│ └─ model_xgb.joblib
├─ .streamlit/
│ └─ config.toml # (optional) theming
├─ requirements.txt
├─ .gitignore
└─ README.md







