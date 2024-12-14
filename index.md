# TL;DR
This blog introduces the concept of moving averages, a fundamental tool in financial analysis used to smooth time series data. We’ll explain what moving averages are, why they're used, visualize their effects on time series data, and present Python code for both a simple and optimized implementation. We’ll also analyze the time complexity of each approach.

---

## What Are Moving Averages?

A moving average is a technique used to smooth out fluctuations in time series data. By calculating the average of data points over a sliding window, moving averages reduce noise and reveal trends more clearly. 

### Types of Moving Averages
- **Simple Moving Average (SMA):** The unweighted average over a fixed number of data points.
- **Exponential Moving Average (EMA):** Applies exponentially decreasing weights to older data points.

### Formula for Moving Averages
- **Simple Moving Average (SMA):**
  
  \[
  \text{SMA}_t = \frac{1}{w} \sum_{i=0}^{w-1} x_{t-i}
  \]
  
  Where:
  - \( \text{SMA}_t \) is the moving average at time \( t \),
  - \( w \) is the window size,
  - \( x \) is the time series data.

- **Exponential Moving Average (EMA):**

  \[
  \text{EMA}_t = \alpha \cdot x_t + (1 - \alpha) \cdot \text{EMA}_{t-1}
  \]

  Where:
  - \( \alpha \) is the smoothing factor, often calculated as \( \frac{2}{w+1} \).

---

## Why Are Moving Averages Used?

1. **Trend Identification:** Detect long-term trends in financial time series like stock prices.
2. **Noise Reduction:** Eliminate short-term volatility to focus on significant movements.
3. **Decision Support:** Used in strategies for buying/selling financial instruments.

---

## Visualization: Smoothing a Time Series

Below is an example of raw and smoothed stock price data using a moving average. This demonstrates how the smoothing process reduces fluctuations while retaining the overall trend.

![Insert visualization of raw vs smoothed data here]

*The data used is derived from Yahoo Finance. For demonstration, we use a simple moving average with a window size of 5 days.*

---

## Python Code: Simple Implementation

Here’s how you can compute a simple moving average in Python using basic libraries.

```python
import numpy as np
import pandas as pd

# Sample time series data (e.g., daily stock prices)
data = [100, 102, 104, 98, 97, 95, 96, 99, 101, 102]

# Convert to Pandas DataFrame
df = pd.DataFrame(data, columns=['Price'])

# Compute Simple Moving Average with a window size of 3
window_size = 3
df['SMA'] = df['Price'].rolling(window=window_size).mean()

print(df)
