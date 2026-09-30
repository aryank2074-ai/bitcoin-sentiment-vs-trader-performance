# bitcoin-sentiment-vs-trader-performance
# 📈 Bitcoin Market Sentiment vs Trader Performance

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-Interactive%20Charts-3F4F75?logo=plotly&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

> **Do traders make more money when the market is greedy or fearful?**
> This project merges **211,224 Hyperliquid trades** with the **Bitcoin
> Fear & Greed Index** to explore how market psychology relates to
> profitability, risk, and trading activity.

---

## 📌 Table of Contents
- [Overview](#-overview)
- [Datasets](#-datasets)
- [Workflow](#-workflow)
- [Questions Answered](#-questions-answered)
- [Key Findings](#-key-findings)
- [Tech Stack](#-tech-stack)
- [Getting Started](#-getting-started)
- [Limitations](#-limitations)
- [Future Improvements](#-future-improvements)
- [Disclaimer](#-disclaimer)

---

## 🎯 Overview
Sentiment indicators like the Fear & Greed Index are widely followed in crypto,
but do they line up with real trader outcomes? This project joins the daily
sentiment score with historical trade records and uses exploratory data
analysis (EDA) and interactive visualizations to compare performance across
five sentiment categories: **Extreme Fear, Fear, Neutral, Greed, Extreme Greed**.

## 📊 Datasets

| Dataset | Rows | Description |
|---|---|---|
| `historical_data.csv` | 211,224 | Hyperliquid trades: account, coin, price, size (USD/tokens), side, direction, closed PnL, fee, timestamp |
| `fear_greed_index.csv` | 2,644 | Daily Fear & Greed Index: value (0-100), classification, date |

- 32 unique trader accounts
- 246 unique coins
- No missing values or duplicates in either raw dataset

## 🔄 Workflow
Load Data → Inspect & Clean → Convert Dates → Extract Trade Date
→ Merge on Date (left join) → Feature Engineering (Win/Loss)
→ Aggregate by Sentiment → Visualize → Conclusions


**Key preprocessing steps**
- Converted `Timestamp IST` to `datetime` and extracted the trade date
- Merged trades with sentiment on `date` (left join)
- Created a `Trade Result` feature (Win / Loss) from `Closed PnL`

## ❓ Questions Answered
1. Does market sentiment affect the **average profit** per trade?
2. Which sentiment generated the **highest total profit**?
3. During which sentiment were the **most trades** executed?
4. What were the **largest single profit and loss** under each sentiment?
5. Which **5 coins** generated the most cumulative profit?
6. Do **larger trades** produce higher profits?
7. How does the **distribution of profits** vary across sentiments?
8. How are the numeric trading variables **correlated**?

## 💡 Key Findings

| Metric | Result |
|---|---|
| Highest average PnL per trade | **Extreme Greed** (~$67.89) |
| Highest total PnL | **Fear** (~$3.36M) |
| Most trades executed | **Fear** (61,837 trades) |
| Largest single profit | **Fear** (~$135K) |
| Largest single loss | **Greed** (~-$118K) |
| Top coins by total PnL | `@107`, `HYPE`, `SOL`, `ETH`, `BTC` |

**Takeaways**
- Extreme Greed had the best *average* profit per trade, but **Fear** produced
  the most *total* profit, mainly because far more trades happened in Fear.
- The biggest single loss occurred during **Greed**, hinting at higher downside
  risk when markets feel euphoric.
- Sentiment appears to be a useful **supporting indicator**, not a standalone
  trading signal.

## 🛠️ Tech Stack
- **Language:** Python
- **Libraries:** Pandas, NumPy, Matplotlib, Seaborn, Plotly
- **Environment:** Jupyter Notebook

## 🚀 Getting Started

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/bitcoin-sentiment-vs-trader-performance.git
cd bitcoin-sentiment-vs-trader-performance

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn plotly jupyter

# 3. Launch the notebook
jupyter notebook sentiment_analysis.ipynb
```

> Place `historical_data.csv` and `fear_greed_index.csv` in the same folder as
> the notebook.

## ⚠️ Limitations
- Analysis is **descriptive**: it shows association, not causation.
- Only 32 accounts, so a few large traders can heavily influence results.
- Averages include opening trades that have a `Closed PnL` of 0.
- Some trades (6 rows) had no matching sentiment date.

## 🔮 Future Improvements
- Compare **win rate** and **risk-adjusted returns** across sentiments
- Analyze per-trader behaviour (leverage, position sizing, long vs short)
- Use the numeric Fear & Greed **value**, not just the category
- Add statistical tests (e.g., ANOVA / Kruskal-Wallis) across sentiments
- Build a predictive model or a Streamlit dashboard

## 📜 Disclaimer
This project is for **educational purposes only** and is not financial advice.

## 🤝 Contributing
Suggestions and pull requests are welcome!

⭐ If you found this useful, consider giving the repo a star!
