# Python Financial Analytics & Market Data Project

## Overview

This project is a self-directed Python financial analysis notebook that updates legacy Quandl-style financial data workflows into a modern Nasdaq Data Link workflow. The notebook retrieves historical equity pricing data, prepares the data in pandas, and applies core financial analytics used in market analysis, risk review, and technical trend evaluation.

The project focuses on practical market-data handling using Python, including data retrieval, cleaning, visualization, returns analysis, volatility analysis, correlation analysis, candlestick charting, and moving-average trend indicators.

## Project Objective

The objective of this notebook is to build a beginner-friendly but finance-relevant workflow that shows how Python can be used to:

- Retrieve historical stock price data through Nasdaq Data Link
- Clean and structure time-series market data
- Visualize price and volume behavior
- Calculate returns and cumulative performance
- Analyze volatility and distribution behavior
- Compare multiple stocks through correlation
- Apply simple and exponential moving averages for trend review

## Tools and Libraries

- Python
- Jupyter Notebook
- pandas
- NumPy
- Matplotlib
- mplfinance
- SciPy
- Nasdaq Data Link API

## Data Source

The notebook uses Nasdaq Data Link table-based market data through the `nasdaqdatalink.get_table()` function. The workflow uses `WIKI/PRICES` examples and focuses on equity tickers such as:

- TSLA
- AAPL
- MSFT

The project uses `qopts` [query options] to request only the columns needed for analysis, such as ticker, date, and adjusted close price.

Example:

```python
qopts={"columns": ["ticker", "date", "adj_close"]}
```

## Key Workflow

The notebook covers the following financial analytics workflow:

1. Python setup and library imports
2. Basic data handling and dataframe inspection
3. Nasdaq Data Link API setup
4. Historical stock price retrieval
5. Price and volume data preparation
6. Adjusted close price visualization
7. Trading volume visualization
8. Candlestick chart construction
9. Daily return calculation
10. Cumulative return calculation
11. Return distribution analysis
12. Rolling volatility analysis
13. Q-Q plot diagnostics
14. Multiple stock data retrieval and concatenation
15. Correlation matrix construction
16. Simple and exponential moving average analysis

## Main Features

### Market Data Retrieval

The notebook retrieves equity pricing data using Nasdaq Data Link and stores the results in pandas DataFrames.

```python
df_tsla = nasdaqdatalink.get_table(
    datatable_code="WIKI/PRICES",
    ticker="TSLA",
    date={"gte": "2018-03-01", "lte": "2018-03-09"},
    qopts={"columns": ["ticker", "date", "adj_close"]},
    api_key=api_key
)
```

### Data Cleaning

The notebook converts date fields into datetime format, sorts observations, selects relevant price columns, and restructures data for time-series analysis.

### Price and Volume Visualization

The project creates line charts and bar charts to analyze historical adjusted close prices and trading volume patterns.

### Candlestick Charting

The notebook uses `mplfinance` to build candlestick charts using open, high, low, close, and volume data.

### Returns Analysis

The project calculates daily returns and cumulative returns to evaluate price performance over time.

### Distribution and Risk Review

The notebook uses histograms, descriptive statistics, Q-Q plots, and rolling volatility to analyze return behavior and risk characteristics.

### Multi-Stock Comparison

The notebook combines multiple single-stock DataFrames using `pd.concat()`, pivots the data into a ticker-based price table, and compares AAPL, MSFT, and TSLA.

### Correlation Matrix

The project calculates correlations between stock returns to evaluate cross-asset relationships.

### Moving Average Analysis

The notebook applies simple moving averages [SMA] and exponential moving averages [EMA] to evaluate short-term and longer-term price trends.

## Example Output

The notebook produces visual outputs such as:

- Adjusted close price charts
- Volume charts
- Candlestick charts
- Daily return plots
- Cumulative return plots
- Return histograms
- Q-Q plots
- Rolling volatility charts
- Multi-stock comparison charts
- Correlation matrix visuals
- SMA and EMA overlays

## Setup Instructions

### 1. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY-NAME.git
cd YOUR-REPOSITORY-NAME
```

### 2. Install required packages

```bash
pip install pandas numpy matplotlib scipy nasdaq-data-link mplfinance jupyter
```

### 3. Add your Nasdaq Data Link API key

Do not hardcode a live API key into a public GitHub repository. Use a placeholder or environment variable.

Example placeholder:

```python
api_key = "YOUR_NASDAQ_DATA_LINK_API_KEY"
```

Example environment variable approach:

```python
import os
api_key = os.getenv("NASDAQ_DATA_LINK_API_KEY")
```

### 4. Run the notebook

```bash
jupyter notebook
```

Open the notebook file and run the cells in order.

## Repository Structure

```text
.
├── UPDATED FINALDRAFT EDUCBA Python for Financial Analysis.ipynb
├── README.md
└── requirements.txt
```

## Suggested requirements.txt

```text
pandas
numpy
matplotlib
scipy
nasdaq-data-link
mplfinance
jupyter
```

## Business and Finance Relevance

This project demonstrates how Python can support market analysis workflows by combining API-based data retrieval, time-series cleaning, financial metric calculation, and investment-style visualization. The workflow is relevant to financial analytics, investment research, portfolio monitoring, equity research, and quantitative finance foundations.

## Important Notes

This project is for educational and portfolio purposes only. It is not financial advice, investment advice, or a trading recommendation. Historical price analysis does not guarantee future investment performance.

## Author

Bryant Paredes  
Finance Graduate, Financial Technology & Analytics Candidate  
GitHub: github.com/bparedes99
