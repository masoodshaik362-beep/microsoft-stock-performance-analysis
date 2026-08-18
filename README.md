# 📊 Microsoft (MSFT) Stock Performance Analysis & Excel Dashboard

An end-to-end financial equity research and quantitative performance model built entirely in **Microsoft Excel**. The project evaluates Microsoft Corporation's (NASDAQ: MSFT) daily price action, moving-average trends, volatility metrics, trading liquidity, and peak-to-trough drawdowns across 246 trading sessions (August 18, 2025 – August 17, 2026).

---

## 🗂️ Excel Workbook Architecture

The project workbook (`Microsoft_Stock_Performance_Analysis_Android_Compatible.xlsx`) contains four dedicated worksheets optimized for desktop and mobile spreadsheet engines:

* **Dashboard:** Executive KPI scorecard tracking starting/ending valuations, 52-week extremes, moving averages, and maximum drawdown indicators.
* **Cleaned Data:** 246-day historical time-series containing daily OHLCV values, calculated **Daily Return %**, **20-day SMA (`MA20`)**, **50-day SMA (`MA50`)**, and **Daily Intraday Range %**.
* **Monthly Summary:** Aggregated monthly metrics including average close price, month-end close, trading volume, monthly trading ranges, and percentage return performance.
* **Data Quality Notes:** Transparent documentation of raw data anomalies and inferred decimal placement corrections.

---

## 📌 Executive KPI Summary

| Performance Metric | Excel Formula / Method | Value |
| :--- | :--- | :---: |
| **Observation Window** | `=COUNT(A:A)` | **246 Trading Days** |
| **Starting Close** | `INDEX(E:E, MATCH(MIN(A:A), A:A, 0))` | **$517.10** |
| **Ending Close** | `INDEX(E:E, MATCH(MAX(A:A), A:A, 0))` | **$485.16** |
| **Period Return** | `=(End_Close - Start_Close) / Start_Close` | **-6.18%** |
| **52-Week Peak Close** | `=MAX(E:E)` | **$542.07** *(Oct 28, 2025)* |
| **52-Week Trough Close** | `=MIN(E:E)` | **$352.83** *(Jun 25, 2026)* |
| **Average Close** | `=AVERAGE(E:E)` | **$447.81** |
| **Average Daily Volume** | `=AVERAGE(G:G)` | **31.42M Shares** |
| **Daily Volatility (Std Dev)** | `=STDEV.S(Daily_Returns)` | **2.04%** |
| **Maximum Drawdown (MDD)** | `=MIN(Drawdown_Series)` | **-34.91%** |
| **Best Single-Day Return** | `=MAX(Daily_Returns)` | **+15.51%** *(Jul 30, 2026)* |
| **Worst Single-Day Return** | `=MIN(Daily_Returns)` | **-9.99%** *(Jan 29, 2026)* |

---

## 🛠️ Data Quality & Data Cleaning in Excel

To ensure time-series integrity, decimal input entry errors were identified and cleaned prior to running dynamic calculations:

* **2025-10-08:** Low corrected from `$23.09` ➔ `$513.09`; Close corrected from `$24.85` ➔ `$524.85`
* **2025-12-26:** High corrected from `$48,812.00` ➔ `$488.12`; Close corrected from `$48,771.00` ➔ `$487.71`

---

## 📈 Excel Modeling & Formula Logic

* **Daily Return (%):** `=(E3 - E2) / E2`
* **20-Day Moving Average:** `=AVERAGE(E2:E21)`
* **50-Day Moving Average:** `=AVERAGE(E2:E51)`
* **Peak-to-Trough Drawdown:**
  * Running High: `=MAX($E$2:E2)`
  * Drawdown %: `=(E2 - MAX($E$2:E2)) / MAX($E$2:E2)`
* **Monthly Aggregation:** Built using Excel Pivot Tables and `SUMPRODUCT`/`AVERAGEIFS` functions for monthly returns, average volume, and monthly high/low close prices.

---

## 📅 Monthly Performance Summary

| Month | Avg Close | Month-End Close | Avg Volume | High Close | Low Close | Monthly Return (%) |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **2025-08** | $507.34 | $506.69 | 22.45M | $517.10 | $502.04 | — |
| **2025-09** | $507.95 | $517.95 | 20.19M | $517.95 | $495.00 | +2.22% |
| **2025-10** | $521.20 | $517.81 | 19.07M | $542.07 | $510.96 | -0.03% |
| **2025-11** | $496.77 | $492.01 | 25.24M | $517.03 | $472.12 | -4.98% |
| **2025-12** | $483.85 | $483.62 | 22.22M | $490.00 | $476.12 | -1.71% |
| **2026-01** | $465.05 | $430.29 | 34.20M | $483.47 | $430.29 | -11.03% |
| **2026-02** | $402.03 | $392.74 | 42.12M | $423.37 | $384.47 | -8.73% |
| **2026-03** | $390.25 | $370.17 | 33.88M | $410.68 | $356.77 | -5.75% |
| **2026-04** | $401.90 | $407.78 | 32.14M | $432.92 | $369.37 | +10.16% |
| **2026-05** | $417.59 | $450.24 | 34.95M | $450.24 | $405.21 | +10.41% |
| **2026-06** | $394.93 | $373.02 | 48.47M | $460.52 | $352.83 | -17.15% |
| **2026-07** | $396.00 | $464.72 | 37.05M | $464.72 | $381.58 | +24.58% |
| **2026-08** | $495.18 | $485.16 | 31.65M | $506.06 | $485.16 | +4.40% |

---

## 🖼️ Dashboard Charts & Visualizations

* **Price Trajectory & Trend Indicators:** Combo line chart showing closing prices with 20-day and 50-day moving average trendlines.
* **Daily Return Distribution:** Clustered bar chart identifying single-day volatility shocks and return dispersion.
* **Liquidity Dynamics:** Volume bar chart capturing liquidity surges, notably the 186.20M peak on June 26, 2026.
* **Drawdown Profile:** Area chart tracking continuous peak-to-trough capital decline.

---

## 📑 Analytical Insights & Conclusions

* **Drawdown Risk:** The stock experienced a -34.91% maximum drawdown, bottoming at $352.83 in late June 2026 before recovering toward $485.16 by August 2026.
* **Volume Confirmation:** Sharp price inflections coincided with extreme volume surges, highlighting institutional accumulation near support levels.
* **Volatility Profile:** With a daily volatility of 2.04%, MSFT displayed significant periodic fluctuations despite a modest net 1-year change (-6.18%).
