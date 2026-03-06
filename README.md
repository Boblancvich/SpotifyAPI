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
