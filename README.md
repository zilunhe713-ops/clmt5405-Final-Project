# Climate Anomalies, Disaster Frequency, and U.S. Equity Market Risk

## Group Members
Zilun He

## Main Notebook
[climate_finance_risk_analysis.ipynb](climate_finance_risk_analysis.ipynb)

## Research Question
Can a simple Climate VaR-style risk signal, built from temperature anomalies and disaster frequency, help explain U.S. equity-market risk and guide a mock sector-allocation portfolio?

## Project Summary
This project applies a simplified Climate VaR methodology to public data. It uses NASA temperature anomalies as the climate input, NOAA billion-dollar disaster frequency as a physical-damage proxy, and `yfinance` ETF data as the financial-market outcome. Instead of estimating a full firm-level Climate VaR or running an integrated assessment model, the notebook builds a transparent climate-risk score, tests whether that score lines up with market and sector risk, and then runs a $50 million mock climate-risk-aware portfolio against an equal-weight benchmark from 2009 onward.

In the historical backtest, the climate-risk-aware mock portfolio ends at about **$570 million**, compared with about **$411 million** for the equal-weight benchmark. The mock portfolio also has a lower maximum drawdown in this sample. This result is a transparent historical illustration, not an investment recommendation.

## Datasets
1. NASA GISTEMP Global Temperature Anomaly CSV  
   Source: https://data.giss.nasa.gov/gistemp/data_v4.html  
   Use: Main climate anomaly dataset.

2. NOAA Billion-Dollar Disaster Frequency Data  
   Source: https://www.ncei.noaa.gov/access/billions/mapping  
   Use: Disaster frequency proxy, aggregated by year and disaster category.

3. yfinance Market Data  
   Tickers: `SPY`, `XLE`, `XLU`, `XLI`, `XLK`, `XLF`  
   Use: Broad-market and sector ETF prices for market-risk analysis.

## Analysis
The notebook follows a simplified version of the Climate VaR chain:

```text
climate input -> physical damage proxy -> financial risk measure -> portfolio implication
```

It first cleans and aligns the climate, disaster, and financial datasets. It then builds a climate-risk score from standardized temperature anomalies and standardized disaster frequency:

```text
ClimateRisk_t = z(TemperatureAnomaly_t) + z(DisasterFrequency_t)
```

High-climate-risk years are defined as years in the top quartile of this score. The analysis compares SPY volatility and sector ETF volatility across climate-risk regimes. Finally, it uses the previous year's climate-risk state to run a mock allocation rule: in lower-risk years the portfolio is equal-weighted across sector ETFs, while after high-climate-risk years it tilts toward utilities and technology and away from energy and industrials. The result is compared with an equal-weight benchmark using cumulative wealth, annualized return, volatility, downside return, and drawdown.

## Figures
1. Global temperature anomaly, U.S. billion-dollar disaster frequency, disaster-type breakdown, and five-year climate-input averages.
2. Climate-risk score and high-climate-risk years.
3. Portfolio allocation rule across sector ETFs.
4. $50 million mock portfolio cumulative wealth and drawdown.
5. Annual return comparison and yearly return difference.

## Tools
Python, Pandas, NumPy, `yfinance`, and Matplotlib.

## Contribution
This project will not make a causal claim that temperature directly drives equity returns. Instead, it shows how Climate VaR methodology can be translated into a reproducible data-analysis workflow: build a climate-risk signal, compare financial risk across climate regimes, and evaluate a simple mock portfolio implication.

## How to Run
Open `climate_finance_risk_analysis.ipynb` and run the notebook from top to bottom. The data are downloaded directly inside the notebook.
