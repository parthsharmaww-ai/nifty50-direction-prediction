# Nifty 50 Next-Day Direction Prediction

Predicting the next-day price direction (up/down) of the Nifty 50 index using
technical indicators and classical machine learning models.

## Status
🚧 In progress — building step by step.

## Project Overview
This project builds an end-to-end ML pipeline that:
- Collects historical Nifty 50 OHLCV data
- Engineers technical indicator features (RSI14, MA5, MA20, Volatility)
- Trains and compares three models — Logistic Regression, Random Forest, and XGBoost
- Benchmarks all models against a 55% naive baseline
- Reports results transparently, including where models underperform

## Repository Structure
nifty50-direction-prediction/
├── data/
│ ├── raw/ # raw downloaded data
│ └── processed/ # cleaned, feature-engineered data
├── notebooks/ # staged analysis notebooks
├── src/ # reusable Python modules
├── requirements.txt
└── README.md


## Roadmap
- [ ] 1. Data collection
- [ ] 2. Feature engineering
- [ ] 3. Exploratory data analysis
- [ ] 4. Logistic Regression baseline
- [ ] 5. Random Forest
- [ ] 6. XGBoost
- [ ] 7. Evaluation, comparison & cleanup

## Setup
```bash
git clone https://github.com/<your-username>/nifty50-direction-prediction.git
cd nifty50-direction-prediction
python -m venv venv
venv\Scripts\activate      # Windows
pip install -r requirements.txt
```

## Results
*(To be added once models are trained and evaluated.)*

## Author
Parth Sharma