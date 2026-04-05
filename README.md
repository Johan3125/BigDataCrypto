# BigDataCrypto

A real-time cryptocurrency price trend prediction system built with PySpark, simulated Kafka streaming, and ML models — designed to run on Google Colab.

## 🎯 Objective

Build a complete end-to-end streaming pipeline that predicts crypto price trends (UP/DOWN) in real time using technical indicators (RSI, MACD) and machine learning.

## 📊 System Architecture

```
Binance API → Producer (threading) → Kafka Queue (simulated) → Spark Streaming → Feature Engineering → Prediction → Storage (CSV) → Visualization
```

| Component | Solution |
|---|---|
| Data Source | Binance REST API (`/api/v3/klines`) |
| Message Queue | Python `queue.Queue` (Kafka simulation) |
| Stream Processing | PySpark Structured Streaming (micro-batch) |
| Feature Engineering | RSI (14), MACD (12/26/9) |
| Prediction | Rule-based + Logistic Regression + Random Forest |
| Storage | CSV file (Cassandra/HBase simulation) |
| Visualization | Matplotlib real-time dashboard |

## 🚀 Getting Started

Open [`CryptoStreamingPrediction.ipynb`](CryptoStreamingPrediction.ipynb) in [Google Colab](https://colab.research.google.com/) and run cells top-to-bottom.

### Steps

| Step | Description |
|---|---|
| 1 | Install environment (PySpark, scikit-learn, ...) |
| 2 | Import libraries and configuration |
| 3 | Fetch OHLCV data from Binance API |
| 4 | Simulated Kafka queue (Producer/Consumer) |
| 5 | Compute RSI and MACD indicators |
| 6 | Rule-based prediction logic |
| 7 | Train ML models (Logistic Regression + Random Forest) |
| 8 | Initialize PySpark session and schemas |
| 9 | Spark Streaming micro-batch processor |
| 10 | CSV storage (simulated database) |
| 11 | Real-time visualization dashboard |
| 12 | Run the full streaming pipeline |
| 13 | Final result analysis |
| 14 | Spark SQL queries |
| 15 | Cleanup |

## 📈 Output

- **Real-time table**: `timestamp`, `price`, `RSI`, `MACD`, `signal` (rule-based), `ml_lr`, `ml_rf` (ML predictions)
- **Charts**: Price + MA20/MA50, RSI panel, MACD histogram
- **CSV file**: `/content/crypto_predictions.csv`

## ⚙️ Technical Indicators

### RSI (Relative Strength Index)
- Period: 14
- RSI > 70 → **SELL** (overbought)
- RSI < 30 → **BUY** (oversold)

### MACD (Moving Average Convergence Divergence)
- Fast EMA: 12 | Slow EMA: 26 | Signal: 9
- MACD crosses above signal → **UP**
- MACD crosses below signal → **DOWN**

## 📦 Dependencies

- `pyspark==3.5.0`
- `pandas`
- `numpy`
- `scikit-learn`
- `matplotlib`
- `requests`

> **Note**: Real Kafka is replaced with `queue.Queue` + `threading` for Colab compatibility.
