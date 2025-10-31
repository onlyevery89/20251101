 (cd "$(git rev-parse --show-toplevel)" && git apply --3way <<'EOF' 
diff --git a/README.md b/README.md
new file mode 100644
index 0000000000000000000000000000000000000000..c3a897c289300628d598e834c03fb32800ddcc41
--- /dev/null
+++ b/README.md
@@ -0,0 +1,47 @@
+# Market Data Overview
+
+This repository contains `temp.csv`, a multi-asset price history covering Samsung Electronics (005930.KS), Apple (AAPL), and Nvidia (NVDA). The file stores 516 trading days of data from **2023-10-16** through **2025-10-10** with daily Open, High, Low, Close, and Volume fields for each ticker.
+
+## File Layout
+
+`temp.csv` is organized with a two-row header: the first row labels each metric (Close, High, Low, Open, Volume) and the second row lists the corresponding ticker. After combining both rows you obtain column names such as `Close_AAPL`, `High_NVDA`, and so on. Each subsequent row represents one trading day.
+
+## Summary Statistics
+
+The table below summarizes the core price and volume metrics across the full sample period.
+
+| Ticker | Field  | Min | Mean | Max |
+|--------|--------|-----|------|-----|
+| 005930.KS | Close | 48,968.97 | 66,471.53 | 94,400.00 |
+| 005930.KS | Open  | 49,263.38 | 66,509.00 | 94,000.00 |
+| 005930.KS | High  | 50,784.92 | 67,202.08 | 94,500.00 |
+| 005930.KS | Low   | 48,968.97 | 65,822.65 | 92,700.00 |
+| 005930.KS | Volume| 2,957,915 | 19,481,204.69 | 57,691,266 |
+| AAPL | Close | 163.82 | 209.52 | 258.10 |
+| AAPL | Open  | 164.17 | 209.29 | 257.99 |
+| AAPL | High  | 165.21 | 211.47 | 259.24 |
+| AAPL | Low   | 162.91 | 207.33 | 256.72 |
+| AAPL | Volume| 23,234,700 | 56,558,297.39 | 318,679,900 |
+| NVDA | Close | 40.30 | 115.60 | 192.57 |
+| NVDA | Open  | 40.43 | 115.59 | 193.51 |
+| NVDA | High  | 40.85 | 117.54 | 195.62 |
+| NVDA | Low   | 39.21 | 113.41 | 191.06 |
+| NVDA | Volume| 105,157,000 | 325,122,504.81 | 1,142,269,000 |
+
+All averages, minima, and maxima are computed across the available trading days in `temp.csv`.
+
+## Daily Return Behavior
+
+Daily Close-to-Close returns show distinct risk-return profiles:
+
+- **Samsung (005930.KS)** averaged a daily gain of 0.07% with 1.91% volatility.
+- **Apple (AAPL)** averaged a daily gain of 0.11% with 1.76% volatility.
+- **Nvidia (NVDA)** averaged a daily gain of 0.37% with 3.18% volatility.
+
+Pairwise correlations of daily returns indicate a moderate positive relationship between Apple and Nvidia (0.37), while Samsung’s returns are weakly related to the U.S. equities in this sample (≈0.02 vs. AAPL, ≈-0.03 vs. NVDA).
+
+## Usage Tips
+
+1. When loading the CSV, use the first row to determine the financial metric and the second row to identify the ticker.
+2. Combine the two header rows (e.g., `metric` + `ticker`) to create unique column names before analysis.
+3. Convert the `Date` column to a date type to facilitate time-series operations.
 
EOF
)
