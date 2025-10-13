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








