# Quant Intro, ETF Returns, Risk, and Drawdown Analysis

This project is an introductory quantitative finance notebook that uses Python to pull market data, calculate monthly returns, evaluate risk and return, and visualize portfolio growth and drawdowns. The notebook began from a Finance 101 Python workflow and was expanded into a cleaner quantitative finance analysis with updated data, reusable functions, and additional risk analytics.

## Project Objective

The goal of this notebook is to demonstrate the foundation of market data analysis using Python. It focuses on SPY as an equity market benchmark and BND as a bond market benchmark, then compares their historical monthly returns, volatility, annualized performance, raw Sharpe ratio, wealth index, and drawdown behavior.

This is intended as an educational quantitative finance project for learning, portfolio analytics practice, and GitHub portfolio development.

## Key Updates in This Version

This notebook includes several components as the base Finance 101 structure:

- Pulls live ETF data using `yfinance`.
- Uses monthly market data for SPY and BND.
- Sets a historical start date for the analysis.
- Cleans the dataset by dropping missing observations after BND begins trading.
- Converts price data into monthly percentage returns.
- Calculates compound total returns.
- Demonstrates pandas indexing with `.loc`, `.iloc`, column selection, and date slicing.
- Calculates monthly standard deviation as a first-pass risk measure.
- Defines reusable functions for annualized returns and annualized volatility.
- Calculates a raw Sharpe-style ratio, defined as annualized return divided by annualized volatility.
- Builds a cumulative wealth index from monthly returns.
- Adds a SPY drawdown analysis using `auto_adjust=True`.
- Visualizes wealth index, previous peaks, and drawdowns.
- Annotates SPY's maximum drawdown on the chart.

## Notebook Workflow

The notebook is organized around a practical quant research workflow:

1. Import core Python libraries, including NumPy, pandas, matplotlib, and yfinance.
2. Download monthly SPY data.
3. Download monthly SPY and BND data together.
4. Clean the combined ETF price dataset.
5. Plot price history.
6. Convert prices into monthly returns.
7. Plot return behavior.
8. Calculate compound returns.
9. Review key pandas operations for time-series analysis.
10. Calculate volatility.
11. Annualize returns and volatility.
12. Calculate a raw Sharpe-style risk-adjusted return metric.
13. Build and plot a cumulative wealth index.
14. Run a focused SPY drawdown analysis.
15. Identify and annotate maximum drawdown.

## Sample Results From the Notebook Run

The values below reflect the sample notebook output from the uploaded version. Because the notebook pulls live market data, results may change when rerun.

| Metric | BND | SPY |
|---|---:|---:|
| Compound Return | 77.24% | 602.98% |
| Annualized Return | 3.04% | 10.76% |
| Annualized Volatility | 4.65% | 15.77% |
| Raw Sharpe-Style Ratio | 0.6551 | 0.6822 |

Additional SPY drawdown result:

| Metric | Result |
|---|---:|
| SPY Maximum Drawdown | -50.78% |

## Methodology

### Return Calculation

Monthly returns are calculated using percentage change:

```python
rets = rets.pct_change().dropna()
```

### Compound Return

Compound returns are calculated by compounding monthly returns across the full sample:

```python
compound_returns = (rets + 1).prod() - 1
```

### Annualized Return

The notebook annualizes returns by converting total compounded growth into an annualized rate:

```python
def annualize_rets(r, periods_per_year=12):
    compounded_growth = (1+r).prod()
    n_periods = r.shape[0]
    return compounded_growth**(periods_per_year / n_periods) - 1
```

### Annualized Volatility

Monthly volatility is annualized using the square-root-of-time rule:

```python
def annualize_vol(r, periods_per_year=12):
    return r.std() * (periods_per_year**0.5)
```

### Raw Sharpe-Style Ratio

The notebook calculates a simplified volatility-adjusted return measure:

```python
annualize_rets(rets) / annualize_vol(rets)
```

Note: this is a raw Sharpe-style ratio because it does not subtract a risk-free rate. A production-grade Sharpe ratio should use excess returns.

### Wealth Index

The cumulative wealth index shows how $1 invested would grow over time:

```python
wealth_index = (1+rets).cumprod()
```

### Drawdown Analysis

The drawdown section compares cumulative wealth against prior peaks:

```python
previous_peaks = wealth_index.cummax()
drawdowns = (wealth_index - previous_peaks)/previous_peaks
```

This helps quantify peak-to-trough losses, which is important for risk management, portfolio construction, and investor behavior analysis.

## Technologies Used

| Tool | Purpose |
|---|---|
| Python | Core programming language |
| pandas | Data cleaning, time-series analysis, return calculations |
| NumPy | Numerical computing support |
| matplotlib | Data visualization |
| yfinance | Market data extraction |
| Jupyter Notebook | Interactive research environment |

## How to Run This Project

Clone the repository or download the notebook, then install the required packages:

```bash
pip install numpy pandas matplotlib yfinance jupyter
```

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Open the notebook file and run the cells from top to bottom.

## Suggested Repository Structure

```text
quant-intro-finance/
├── README.md
├── v2 Updated Quant Intro.ipynb
└── requirements.txt
```

Optional `requirements.txt`:

```text
numpy
pandas
matplotlib
yfinance
jupyter
```

## Skills Demonstrated

This project demonstrates foundational skills that are directly relevant to financial analytics, investment research, and quantitative finance:

- Market data extraction
- ETF return analysis
- Time-series data cleaning
- Monthly return calculation
- Compound return calculation
- Annualized return modeling
- Volatility estimation
- Risk-adjusted performance analysis
- Wealth index construction
- Drawdown analysis
- Python-based investment analytics
- pandas workflow management
- Data visualization for financial decision-making

## Why This Project Matters

This notebook turns raw ETF price data into investment decision metrics. Instead of only downloading prices, it shows how to convert data into risk and return insights that investors, analysts, and portfolio managers actually use.

The project also shows a clear progression from basic Python syntax into applied portfolio analytics, making it a strong early-stage quantitative finance project for a GitHub portfolio, resume, or interview discussion.

## Future Improvements

Potential next upgrades include:

- Add a true Sharpe ratio using a risk-free rate.
- Add rolling volatility and rolling returns.
- Add rolling drawdown charts.
- Add Sortino ratio, Calmar ratio, and maximum drawdown tables.
- Compare additional ETFs, such as QQQ, IWM, GLD, TLT, and VTI.
- Add portfolio weights and rebalance logic.
- Build a simple 60/40 equity-bond portfolio analysis.
- Export results to CSV or Excel.
- Add a clean summary dashboard using Plotly or Streamlit.

## Disclaimer

This project is for educational and portfolio demonstration purposes only. It is not financial advice, investment advice, or a recommendation to buy or sell any security.

## Credit

This project was adapted from an introductory Finance 101 Python notebook structure and expanded with updated ETF data, annualized performance functions, risk analytics, cumulative wealth indexing, and drawdown visualization.
