# Concrete Strength Prediction

A CatBoost regression model that predicts concrete compressive strength from two 
additive materials — **FSA (Foundry Sand Ash)** and **JF (Jute Fiber)** — tested 
across synthetic datasets of increasing size (15 → 1,000 → 100,000 samples).

## Synthetic data notice

This project currently trains on **synthetic, randomly generated data**, not real 
laboratory measurements. The target variable (compressive strength) is generated 
from a formula the notebook defines itself (e.g. `0.5*FSA + 3*JF + noise`, with an 
added interaction/quadratic term in the largest experiment).
This is useful for prototyping the modeling pipeline 
and visualizing how CatBoost fits a known relationship, but **results here do not 
reflect real-world concrete performance** until the model is retrained on genuine 
experimental data ( which was not available at the time of the experiment).

## Overview

Concrete compressive strength depends nonlinearly on its ingredients. This notebook 
explores using **CatBoost**, a gradient boosting library with native handling of 
ordered boosting and symmetric trees, to model strength as a function of two 
additive materials:

- **FSA** — Foundry Sand Ash content (%)
- **JF** — Jute Fiber content (%)

Three experiments are run at increasing scale to see how the model behaves as 
dataset size grows.

## Contents

- `CSP.ipynb` — notebook containing all three experiments (data generation, model 
  training, evaluation, and visualization)

## Experiments

| # | Samples | Relationship modeled | CatBoost config | MAE |
|---|---------|----------------------|------------------|-----|
| 1 | 15 | Linear: `0.5·FSA + 3·JF + noise` | `iterations=1000, lr=0.1, depth=4` | **0.604** |
| 2 | 1,000 | Linear: `0.5·FSA + 3·JF + noise` | `iterations=1000, lr=0.05, depth=5` | **0.855** |
| 3 | 100,000 | Nonlinear: adds `FSA·JF` interaction and `FSA²` term | `iterations=500, lr=0.05, depth=6` | **0.805** |

Each experiment reports **Mean Absolute Error (MAE)** on a held-out test split, and 
produces three plots:
- Actual vs. predicted scatter plot
- 3D surface plot of predicted strength over the FSA/JF input space
- 2D contour plot of the same surface

### Requirements

```bash
pip install catboost scikit-learn pandas numpy matplotlib
```

### Run

Open `CSP.ipynb` in Jupyter or Google Colab and run all cells sequentially. Each 
experiment (small, medium, large) is self-contained within its own code cell.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Projit1101/Concrete-Strength-Prediction/blob/main/CSP.ipynb)




