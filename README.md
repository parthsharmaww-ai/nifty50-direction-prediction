# Nifty 50 Next-Day Direction Prediction

Predicting the next-day price direction (up/down) of the Nifty 50 index using
technical indicators and classical machine learning models.

## Status
✅ Complete — see Results below.

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
- [X] 1. Data collection
- [X] 2. Feature engineering
- [X] 3. Exploratory data analysis
- [X] 4. Logistic Regression baseline
- [X] 5. Random Forest
- [X] 6. XGBoost
- [X] 7. Evaluation, comparison & cleanup

## Setup
```bash
git clone https://github.com/<parthsharmaww-ai>/nifty50-direction-prediction.git
cd nifty50-direction-prediction
python -m venv venv
venv\Scripts\activate      # Windows
pip install -r requirements.txt
```

## Results

Three model families were trained on technical indicators (MA5, MA20, RSI14, Volatility) 
to predict next-day Nifty 50 direction, using a chronological 80/20 train/test split 
(train: Jan 2015 – Oct 2023, test: Oct 2023 – Dec 2025).

| Model                              | Accuracy | Baseline | Delta      |
|-------------------------------------|----------|----------|------------|
| Logistic Regression                 | 54.09%   | 53.72%   | +0.37pp*   |
| Logistic Regression (balanced)      | 48.14%   | 53.72%   | -5.58pp    |
| Random Forest (max_depth=5)         | 46.28%   | 53.72%   | -7.44pp    |
| Random Forest (max_depth=3)         | 46.84%   | 53.72%   | -6.88pp    |
| XGBoost                             | 49.81%   | 53.72%   | -3.91pp    |

\* *Misleading result — this model predicted "Up" for 97% of test samples rather than 
learning real signal (recall on "Down" class: 0.03). Not a genuine edge over baseline.*

**Baseline:** always predicting the majority class in the test set (53.72% "Up" days).

### Key Findings

- **No model meaningfully beat the baseline.** The one result that appeared to (unbalanced 
  Logistic Regression) turned out to be a degenerate classifier predicting almost 
  exclusively "Up" — exposed once class-balancing was applied.
- **Feature importances were evenly distributed** across all four indicators in both 
  tree-based models (RSI14: ~0.28, Volatility: ~0.25, MA20: ~0.23-0.25, MA5: ~0.22-0.23), 
  with no single feature dominating — indicating none carry strong individual or 
  interaction-based predictive power for this target.
- **This is consistent with EDA (Stage 3):** correlation between all four features and 
  next-day direction was near-zero (|r| < 0.06) prior to any modeling.
- **Likely cause:** daily index direction is close to a random walk. Technical indicators 
  derived purely from historical price/volume, without external signals (news, macro 
  data, order flow), carry limited next-day predictive information — consistent with 
  weak-form market efficiency.

### Future Directions

1. Incorporate macroeconomic indicators (interest rates, FII/DII flows, global indices)
2. Add sentiment/news-based features
3. Test longer prediction horizons (e.g. 5-day or 20-day direction instead of next-day)
4. Reframe as a magnitude/volatility regression task rather than binary direction

## Author
Parth Sharma
