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


---

## Setup
```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>

# (recommended) virtual env
python -m venv .venv
# mac/linux
source .venv/bin/activate
# windows
# .venv\Scripts\activate

pip install -r requirements.txt

--------------

## Build Data & Train
Open and run the notebook:
notebooks/01_build_dataset.ipynb

This will:
Create data/raw_tracks.csv
Train LR / RF / XGB
Save artifacts to models/
No Spotify keys? The notebook automatically uses a synthetic dataset with realistic distributions so training finishes without errors.

-----

## Run the App
streamlit run app.py
Open the URL Streamlit prints (usually http://localhost:8501).
In the app you can:
Move sliders for danceability, energy, valence, tempo
See hit probability from LR / RF / XGB
Compare to Top-100 and All-data averages
Inspect feature importances (RF)

------

## Results 
(Metrics vary by dataset; below are representative demo values.)
Class balance (hit=1): ~0.82
Logistic Regression: acc 0.69, f1 0.78, roc_auc 0.79
Random Forest: acc 0.77, f1 0.87, roc_auc 0.67
XGBoost: acc 0.78, f1 0.87, roc_auc 0.59
Takeaway: RF/XGB deliver strong F1/accuracy; LR is simpler and well-calibrated. The app surfaces all three so you can choose per use case.
-----------

## Deploy on Snowflake
In Snowflake, go to Projects → Streamlit → + Streamlit App.
Add these files as app assets (or stage them):
app.py
data/raw_tracks.csv
models/model_*.joblib
Select a warehouse (e.g., XSMALL) and click Run.
Share the generated app URL.
The same app.py runs locally and in Snowflake. Dependencies are listed in requirements.txt.
_______________



