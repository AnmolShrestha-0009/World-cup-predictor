# ⚽ FIFA Men's World Cup Match Winner Predictor

A machine learning project that predicts the winner of a FIFA men's World Cup match using an ensemble of **Random Forest** and **XGBoost** classifiers. The project generates match features from team statistics, obtains predictions from both models, and combines them to produce a final prediction.

---

## 📌 Project Overview

This project aims to predict the outcome of a football match between two teams using historical performance statistics and machine learning.

The prediction pipeline consists of:

* Feature generation from team statistics
* Random Forest prediction
* XGBoost prediction
* Ensemble averaging of both model probabilities
* Final match winner prediction

The project is designed to be modular, making it easy to update team statistics, retrain models, or extend the prediction pipeline with additional models.

---

## 🏗️ Project Architecture

```text
                    User Input
              (Home Team, Away Team)
                         │
                         ▼
               Feature Generation
                         │
         ┌───────────────┴───────────────┐
         ▼                               ▼
   Random Forest Features         XGBoost Features
         │                               │
         ▼                               ▼
      Random Forest Model         XGBoost Model
         │                               │
         ▼                               ▼
   Win Probability (RF)          Win Probability (XGB)
         └───────────────┬───────────────┘
                         ▼
               Ensemble Averaging
                         ▼
               Final Match Prediction
```

---

## 📂 Project Structure

```text
├── data/
│   ├── goalscores.csv
│   └── result.csv
│
├── models/
│   ├── rf_model.pkl
│   └── xgb_model.pkl
│
├── notebooks/
│   ├── wcsimulator.ipynb
│   └── wcsimulator2.ipynb
│
├── predictor.py
├── requirements.txt
└── README.md
```

---

## ⚙️ Features

* Ensemble of Random Forest and XGBoost
* Automatic feature generation from team statistics
* Probability-based prediction
* Easy-to-use prediction function
* Modular architecture for future expansion
* Reusable trained models stored as `.pkl` files

---

## 📊 Machine Learning Models

### Random Forest

Used to capture nonlinear relationships between ranking and team performance statistics.

### XGBoost

Used as a gradient boosting model to improve predictive performance and reduce variance.

### Ensemble Prediction

The final prediction is computed as:

```text
Final Probability =
(Random Forest Probability + XGBoost Probability) / 2
```

---

## 📈 Input Features

The models use engineered features such as:

* Home Team Ranking
* Away Team Ranking
* Ranking Difference
* Home Goals Scored Ratio
* Home Goals Conceded Ratio
* Away Goals Scored Ratio
* Away Goals Conceded Ratio
* Neutral Venue Indicator (XGBoost)

## 🧹 Data Collection & Feature Engineering

The project uses historical international football match data combined with manually collected FIFA team rankings to improve predictive performance.

### Data Sources

* Historical international match results (`result.csv`)
* Goal scoring statistics (`goalscores.csv`)
* FIFA Men's World Rankings (manually collected from the official FIFA rankings page)

The ranking information was manually incorporated into the dataset to ensure that each match reflected the relative strength of the competing teams at the time of prediction.

### Feature Engineering

Several domain-specific features were engineered from the raw data to provide the machine learning models with more informative inputs.

The engineered features include:

* Home Team FIFA Ranking
* Away Team FIFA Ranking
* Ranking Difference (`rank_diff`)
* Home Team Goals Scored Ratio
* Home Team Goals Conceded Ratio
* Away Team Goals Scored Ratio
* Away Team Goals Conceded Ratio
* Neutral Venue Indicator

These features were created by aggregating historical match statistics and combining them with FIFA ranking information. The goal was to capture each team's offensive strength, defensive performance, and overall competitive level rather than relying solely on raw match results.

Feature engineering played a significant role in improving the predictive capability of both the Random Forest and XGBoost models by providing meaningful numerical representations of team performance.

---

## 🚀 Usage

Load the trained models:

```python
import joblib

rf = joblib.load("rf_model.pkl")
xgb = joblib.load("xgb_model.pkl")
```

Generate a prediction:

```python
predict("Spain", "Belgium")
```

Example output:

```text
Match: Spain vs Belgium

Random Forest : 72.14%
XGBoost       : 69.83%
Final         : 70.99%

Predicted Winner: Spain
```

---
## 🏆 Knockout Stage Prediction 

```text
                           FIFA men's World Cup
                           Knockout Stage Bracket

Quarter-finals                     Semi-finals                     Final

France      ───────────┐
                       ├── France ────────┐
Morocco     ───────────┘                  │
                                          ├── Spain ─────────────┐
Spain       ───────────┐                  │                      │
                       ├── Spain ─────────┘                      │
Belgium     ───────────┘                                         │
                                                                 ├── 🏆 Spain
England     ───────────┐                                         │
                       ├── England ───────┐                      │
Norway      ───────────┘                  │                      │
                                          ├── Argentina ─────────┘
Argentina   ───────────┐                  │
                       ├── Argentina ─────┘
Switzerland ───────────┘
```

### Predicted Results

| Stage         | Match                    | Predicted Winner |
| ------------- | ------------------------ | ---------------- |
| Quarter-final | France vs Morocco        | 🇫🇷 France      |
| Quarter-final | Spain vs Belgium         | 🇪🇸 Spain       |
| Quarter-final | England vs Norway        | 🏴 England       |
| Quarter-final | Argentina vs Switzerland | 🇦🇷 Argentina   |
| Semi-final    | France vs Spain          | 🇪🇸 Spain       |
| Semi-final    | England vs Argentina     | 🇦🇷 Argentina   |
| Final         | Spain vs Argentina       | 🏆 **Spain**     |

```
```


## 📦 Dependencies

* Python 3.10+
* pandas
* numpy
* scikit-learn
* xgboost
* joblib

---

## 🔮 Future Improvements

* Support for additional machine learning models (LightGBM, CatBoost)
* Dynamic team statistics loaded from CSV or API
* Probability calibration using Platt Scaling or Isotonic Regression
* Streamlit or Flask web application
* Tournament simulation using Monte Carlo methods
* Hyperparameter optimization
* SHAP-based model explainability

---

## 📄 License

This project is released under the MIT License.

---

## 👨‍💻 Author

**Anmol Shrestha**
