## **EDA Project 5 — Stock Market Data Analysis using Pandas**

### **Project Title**

📈 **Exploratory Data Analysis of Stock Market Prices**

---

### **Objective**

To analyze stock market data to understand:

* Price movement over time
* Volatility and risk
* Trading volume behavior
* Relationships between Open, Close, High, and Low prices

---

### **Dataset**

**Name:** Stock Market Historical Data
**Format:** CSV

**Typical Columns:**

* `Date`
* `Open`
* `High`
* `Low`
* `Close`
* `AdjClose`
* `Volume`

You can use:

* Yahoo Finance historical stock data
* Kaggle stock datasets

---

### **Key Questions (EDA Goals)**

1. How does the stock price change over time?
2. What is the daily return?
3. How volatile is the stock?
4. Are there volume spikes during price changes?
5. What patterns exist between OHLC prices?

---

### **Step 1: Load Libraries & Data**

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv("stock_data.csv")
df.head()
```

---

### **Step 2: Initial Exploration**

```python
df.info()
df.describe()
df.isnull().sum()
```

---

### **Step 3: Data Cleaning**

```python
df['Date'] = pd.to_datetime(df['Date'])
df.sort_values('Date', inplace=True)
df.dropna(inplace=True)
```

---

### **Step 4: Closing Price Trend**

```python
plt.figure(figsize=(10,5))
plt.plot(df['Date'], df['Close'])
plt.title("Closing Price Over Time")
plt.xlabel("Date")
plt.ylabel("Price")
plt.show()
```

---

### **Step 5: Daily Returns**

```python
df['DailyReturn'] = df['Close'].pct_change()

sns.histplot(df['DailyReturn'].dropna(), bins=50)
plt.title("Distribution of Daily Returns")
plt.show()
```

---

### **Step 6: Volatility (Rolling Standard Deviation)**

```python
df['Volatility'] = df['DailyReturn'].rolling(window=20).std()

plt.plot(df['Date'], df['Volatility'])
plt.title("20-Day Rolling Volatility")
plt.show()
```

---

### **Step 7: Volume Analysis**

```python
plt.figure(figsize=(10,5))
plt.plot(df['Date'], df['Volume'])
plt.title("Trading Volume Over Time")
plt.show()
```

---

### **Step 8: OHLC Relationship**

```python
df[['Open','High','Low','Close']].corr()
```

---

### **Insights You Can Derive**

* Long-term price trends
* Periods of high market volatility
* Relationship between volume and price movement
* Risk assessment patterns

---

### **Skills Demonstrated**

✅ Financial time-series analysis
✅ Feature engineering (returns & volatility)
✅ Statistical understanding
✅ Pandas proficiency
✅ Data storytelling

---

## ✅ Summary of All 5 EDA Projects

1. Retail Sales Analysis
2. Student Performance Analysis
3. Customer Churn Analysis
4. COVID-19 Data Analysis
5. Stock Market Data Analysis
