# Climate Anomalies, Disaster Frequency, and U.S. Equity Market Risk

## Group Members
Zilun He

## Research Question
Are higher temperature anomalies and more frequent climate-related disasters associated with higher U.S. equity market risk and different sector-level risk patterns?

## Project Summary
This project will combine climate data, disaster frequency data, and financial market data to study whether high-climate-risk periods are associated with higher equity-market volatility, deeper drawdowns, and different sector-level risk patterns. I will use NASA temperature anomaly data as the climate signal, NOAA billion-dollar disaster frequency data as a disaster-risk proxy, and `yfinance` data for SPY, VIX, and sector ETFs. The analysis will align the datasets by time, compare normal and high-climate-risk periods, and produce clear figures showing climate anomalies, disaster frequency, market volatility, sector differences, and long-horizon risk behavior.

## Datasets
1. NASA GISTEMP Gridded Temperature Anomaly Data  
   Source: https://data.giss.nasa.gov/gistemp/data_v4.html  
   Planned use: Load with Xarray and compute global or U.S.-level temperature anomaly over time.

2. NASA Global Temperature Anomaly CSV  
   Source: https://data.giss.nasa.gov/gistemp/data_v4.html  
   Planned use: Use as a simpler global anomaly benchmark and validation dataset.

3. NOAA Billion-Dollar Disaster Frequency Data  
   Source: https://www.ncei.noaa.gov/access/billions/mapping  
   Planned use: Aggregate U.S. disaster counts by year, state, and disaster category.

4. yfinance Market Data  
   Tickers: `SPY`, `^VIX`, `^IRX`, `XLE`, `XLU`, `XLI`, `XLK`, `XLF`  
   Planned use: Download broad-market, volatility-index, risk-free-rate, and sector ETF data for market-risk analysis.

## Planned Analysis
I will first clean and align the climate, disaster, and financial datasets at a monthly or annual frequency. I will define high-climate-risk periods as periods in the top quartile of temperature anomaly or disaster frequency. Then I will compare market risk measures, including rolling volatility, drawdowns, downside return percentiles, and sector ETF volatility, across high- and lower-climate-risk periods.

As an extension, I will compute long-horizon variance ratios:

```text
VR_k = Var(R_{t,t+k}) / [k * Var(R_{t,t+1})]
```

This statistic will be used descriptively to compare whether long-horizon equity risk appears higher during high-climate-risk periods than would be implied by simply scaling short-term volatility.

## Planned Figures
1. Global or U.S. temperature anomaly over time.
2. U.S. billion-dollar disaster frequency by year and disaster category.
3. Relationship between temperature anomaly and disaster frequency.
4. SPY and sector ETF rolling volatility or drawdowns during high-climate-risk periods.
5. Long-horizon variance ratio comparison across SPY and sector ETFs.

## Tools
Python, Pandas, Xarray, NumPy, `yfinance`, Matplotlib, SciPy or Statsmodels.

## Expected Contribution
This project will not make a causal claim that temperature directly drives equity returns. Instead, it will evaluate whether public data show descriptive links between climate anomalies, disaster frequency, market risk, sector sensitivity, and long-horizon variance behavior.
