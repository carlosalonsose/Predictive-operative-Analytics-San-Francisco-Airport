<div align="center">

# ✈️ Predictive Operative Analytics — San Francisco Airport

**LSTM forecasting and strategic analysis of passenger traffic at SFO**

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-LSTM-FF6F00?logo=tensorflow&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-Dashboard-FF4B4B?logo=streamlit&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-Charts-3F4F75?logo=plotly&logoColor=white)

</div>

---

## 📌 Overview

Business Intelligence & Analytics project built on the public **SFO Air Traffic Passenger Statistics** dataset (1999 → 2025). It combines a deep-learning forecast of passenger volume with a business-oriented analysis of how traffic is distributed across terminals, airlines and fare categories.

The goal is to turn raw monthly counts into decisions: **where will demand land, which terminals will feel it, and how exposed is the airport to a single airline?**

## ✨ Features

| | |
|---|---|
| 🔮 **LSTM forecast** | Univariate LSTM (look-back of 3, Dropout, early stopping) trained on monthly passenger totals, with train/test validation and RMSE. |
| 📅 **Future predictions** | Recursive multi-month forecast (1–24 months) and projected impact on each terminal. |
| 📈 **Seasonality** | Trend / seasonal / residual decomposition of the series. |
| 🏢 **Terminal analysis** | Yearly passenger share per terminal (T1, T2, T3, International, Other). |
| 🚪 **Operations & commercial** | Gate-level congestion, airline distribution, low-cost vs. premium evolution. |
| ⚠️ **Risk assessment** | Airline dependency analysis and a risk simulation with an automated strategic read-out. |

## 🗂️ Repository structure

```
├── Business_LTSM.ipynb            # Full analysis: LSTM, forecasts, terminal & airline analysis
├── Business_LTSM_Years.ipynb      # LSTM on yearly aggregated data
├── Business_LTSM_dashboard.py     # Interactive Streamlit dashboard
└── Data/
    └── Air_Traffic_Passenger_Statistics_20251204.csv
```

## 🖥️ Dashboard

The Streamlit app has five tabs:

1. **Terminal Trends** — seasonal decomposition and terminal distribution
2. **Forecast & Strategy** — train the LSTM (adjustable epochs and neurons) and forecast ahead
3. **Ops & Commercial Insights** — congestion, airlines, low cost vs. premium
4. **Dependency Analysis** — reliance on individual airlines per terminal
5. **Risk Assessment** — airline-loss simulation

## 🚀 Getting started

```bash
git clone https://github.com/carlosalonsose/Predictive-operative-Analytics-San-Francisco-Airport.git
cd Predictive-operative-Analytics-San-Francisco-Airport

pip install streamlit pandas numpy plotly matplotlib tensorflow scikit-learn statsmodels jupyter
```

The notebooks and the dashboard read the CSV from the **current directory**, so copy it next to them first:

```bash
cp Data/Air_Traffic_Passenger_Statistics_20251204.csv .
```

Run the dashboard:

```bash
streamlit run Business_LTSM_dashboard.py
```

Or open the notebooks:

```bash
jupyter notebook Business_LTSM.ipynb
```

## 🧠 Methodology

1. **Preparation** — passenger counts aggregated by month; chronological 80/20 train/test split.
2. **Scaling** — `MinMaxScaler` fitted on train only, then applied to test (no leakage).
3. **Model** — `LSTM(32)` → `Dropout` → `Dense(1)`, Adam optimizer, MSE loss, `EarlyStopping` on validation loss.
4. **Evaluation** — RMSE on train and test in original units.
5. **Forecasting** — recursive prediction feeding each forecast back as input.

## 📊 Data

[SFO Air Traffic Passenger Statistics](https://data.sfgov.org/Transportation/Air-Traffic-Passenger-Statistics/rkru-6vcg) — DataSF open data portal. Monthly enplaned/deplaned passengers by airline, terminal, boarding area and fare category.

## 👤 Author

**Carlos Alonso** — Business Intelligence & Analytics, Erasmus.
