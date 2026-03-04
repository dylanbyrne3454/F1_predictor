# F1 Podium Predictor

A machine learning project that attempts to predict the podium of a given Formula 1 race based on historical data. For this project I implemented Logistic Regression, Random Forest, XGBoost and Neural Network models and compared their accuracy.

For training I used the "ground effect" era of F1, using the 2022–2024 seasons as training data and the 2025 season as the test set.

---

## Results

| Model | Accuracy | F1 Score | AUC |
| --- | --- | --- | --- |
| Random Forest | **0.934** | **0.785** | **0.959** |
| XGBoost | 0.896 | 0.675 | 0.936 |
| Logistic Regression | 0.853 | 0.661 | 0.947 |
| Neural Network | 0.880 | 0.508 | 0.926 |

Key finding: Grid position and recent form (average finish over last 3 races) are the strongest predictors of podium finishes, as confirmed by SHAP analysis.

---

## Features

All features use only information available **before the race** to avoid data leakage.

| Feature | Description |
| --- | --- |
| `GridPosition` | Starting grid position from qualifying |
| `DriverPointsBefore` | Individual championship points before this race |
| `TeamPointsBefore` | Constructor championship points before this race |
| `AvgFinishLast3` | Driver's average finish position over last 3 races |

---

## Project Structure

```
F1_PREDICTOR/
│
├── data/
│   ├── race_results_22_24.csv   # Training data (2022-2024)
│   └── race_results_25.csv      # Test data (2025)
│
├── plots/                        # Generated visualisations
│
├── 01_data_collection.ipynb     # FastF1 data collection
├── 02_creating_models.ipynb     # Feature engineering, modelling and evaluation
│
├── requirements.txt
└── .gitignore
```

---

## How to Run

1. Install dependencies: `pip install -r requirements.txt`
2. Run `01_data_collection.ipynb` to collect data
3. Run `02_creating_models.ipynb` for feature engineering, modelling and results

---

## Limitations

- Small dataset (~1,200 training rows across 3 seasons)
- Regulation changes each season may reduce cross-year generalisability
- Rookie drivers in 2025 have no prior championship points history