# 🎧 SpotifyAPI — Feature‑Driven Music Insights & Artist Classification

This project brings together two complementary parts:

1. **Artist Classification (ML):** A decision‑tree–based model trained on tabular audio features (e.g., BPM, danceability, acousticness) to predict an **artist** label from a track’s attributes.
2. **Spotify Data Explorer:** A small Spotipy-based pipeline that pulls two artists’ discographies, computes **audio feature aggregates**, and prints a head‑to‑head comparison.

---

## ✨ Features

- **ExtraTrees feature importance** to understand which attributes move the predictions.
- **DecisionTree** model with a **Graphviz** export (`.dot`) for explainability.
- **Spotify audio features** pull (acousticness, danceability, energy, etc.) and popularity for side‑by‑side artist comparisons.
- **CSV outputs** for analysis and reproducibility.

---

## 📦 Project Contents


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
Dependencies

- pandas
- numpy
- matplotlib
- scikit-learn
- spotipy
- graphviz
- ipywidgets

## How it works

1) Feature importance & model training

Loads ai music.csv, selects the 9 numeric audio features as X, and artist as y.
Splits train/test (test_size=0.2).
Trains ExtraTreesClassifier → plots top features.
Trains DecisionTreeClassifier → exports Graphviz .dot tree to kpop.dot.

2) Spotify data collection & aggregation

Prompts for two artists (e.g., “GOT7”, “BTS”).
Uses Spotipy to:

Find the artist URI via search.
Enumerate albums → tracks → audio features (acousticness, danceability, energy, instrumentalness, liveness, loudness, speechiness, tempo, valence) and popularity.


Produces a deduplicated, popularity‑sorted CSV (Spotipy-stats.csv) with one row per unique track.
Aggregates by Artist (means) and prints percent differences.

## Findings

The printed importances (matching bpm, nrgy, dnce, dB, live, val, dur, acous, spch) were:
[0.1103, 0.1071, 0.1185, 0.0864, 0.0984, 0.1180, 0.1227, 0.1390, 0.0995]

Top contributors appear to be:

acous (acousticness) ≈ 0.139
dur (duration) ≈ 0.123
dnce (danceability) ≈ 0.119
val (valence) ≈ 0.118

Interpretation: in this dataset, timbre/production signals (acousticness), track length, and movement/positivity proxies (danceability/valence) are the strongest signals for predicting the artist label.

## Sample artist comparison

Various features were computed:

Mean acousticness
Mean danceability
Mean energy
…etc.

For each artist in the dataset, eg: GOT7 and BTS, we can compare a features such as:

| Artist    | Mean Acousticness |
| -------- | ------- |
| BTS  | 11.4188    |
| GOT7 | 13.6988     |

Difference=11.41877313.698829−11.418773​×100≈20%

*GOT7 is approximately 20% more acoustic than BTS.*


---

## Future improvements
- Fix output typo
- Fix tree layers and complexity





