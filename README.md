# Concrete Strength Prediction

A gradient boosting model for predicting the compressive strength of concrete mixes 
that incorporate **FSA (Fly-ash/Slag Aggregate)** and **Jute Fibre** as reinforcing 
materials, using ordered boosting and symmetric decision trees (CatBoost-style).

## Overview

Concrete compressive strength is a highly nonlinear function of its ingredients and 
curing conditions. This project trains a gradient boosting regressor to predict 
strength from mix composition, and benchmarks it against more conventional approaches.

The model outperforms:
- Random Forest
- Support Vector Regression (SVR)
- Traditional Gradient Boosted Decision Trees (GBDT)

Performance gains come primarily from native categorical feature encoding (avoiding 
one-hot/label-encoding artifacts) and tuned L2 regularization.

## Contents

- `CSP.ipynb` — main notebook: data loading, preprocessing, model training, 
  evaluation, and comparison against baseline models

## Approach

1. **Data preparation** — cleaning and structuring the concrete mix dataset (inputs 
   such as cement, water, aggregate, FSA, and Jute Fibre content; target = compressive 
   strength)
2. **Baseline models** — Random Forest, SVR, and standard GBDT trained for comparison
3. **Gradient boosting model** — trained using ordered boosting and symmetric trees, 
   with native categorical feature handling
4. **Regularization tuning** — L2 penalty tuned to reduce overfitting and improve 
   generalization
5. **Evaluation** — models compared on held-out test performance (e.g. RMSE / R²)

## Getting Started

### Requirements

```bash
pip install catboost scikit-learn pandas numpy matplotlib
```

### Run

Open `CSP.ipynb` in Jupyter or Google Colab and run all cells sequentially.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Projit1101/Concrete-Strength-Prediction/blob/main/CSP.ipynb)

## Results

_Add your final metrics table here, e.g.:_

| Model             | RMSE | R²   |
|-------------------|------|------|
| SVR               |      |      |
| Random Forest     |      |      |
| Traditional GBDT  |      |      |
| **This model**    |      |      |

## License

MIT
