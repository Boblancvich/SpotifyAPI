# 🎧 SpotifyAPI — Feature‑Driven Music Insights & Artist Classification

This project brings together two complementary parts:

1. **Artist Classification (ML):** A decision‑tree–based model trained on tabular audio features (e.g., BPM, danceability, acousticness) to predict an **artist** label from a track’s attributes.
2. **Spotify Data Explorer:** A small Spotipy-based pipeline that pulls two artists’ discographies, computes **audio feature aggregates**, and prints a head‑to‑head comparison.

It’s ideal for quick music data experiments, feature importance exploration, and explainable decision‑tree visualizations.

---

## ✨ Features

- **ExtraTrees feature importance** to understand which attributes move the predictions.
- **DecisionTree** model with a **Graphviz** export (`.dot`) for explainability.
- **Spotify audio features** pull (acousticness, danceability, energy, etc.) and popularity for side‑by‑side artist comparisons.
- **CSV outputs** for analysis and reproducibility.

---

## 📦 Project Contents

> Adjust names if your repo uses different filenames.

**What each file is for**

- **`ai music.csv`** — The main labeled dataset. Your pipeline uses these input columns as features:
  - `bpm`, `nrgy`, `dnce`, `dB`, `live`, `val`, `dur`, `acous`, `spch`
  - Target: `artist`
- **`Spotipy-stats.csv`** — Appended dataset of tracks fetched from the Spotify Web API with computed audio features and popularity, plus an `Artist` column (the artist you queried).
- **`kpop.dot`** — Graphviz description of the trained decision tree for explainability (render to PNG/PDF).
- **`main.py` (or your notebook)** — Contains:
  - **ML block**: feature selection, train/test split, ExtraTrees importances plot, DecisionTree fit and export.
  - **Spotify block**: asks for two artists, fetches albums → tracks → audio features, aggregates stats by artist, and prints a comparison.

---

## 🚀 Quickstart

### 1) Create & activate a virtual environment
```bash
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS/Linux
source .venv/bin/activate
