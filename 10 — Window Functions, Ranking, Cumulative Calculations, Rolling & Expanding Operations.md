# **10 — Window Functions, Ranking, Cumulative Calculations, Rolling & Expanding Operations**

### **🎯 Objective**

* Use **window functions** (rolling, expanding)
* Calculate **moving averages**, **moving sums**, **moving counts**
* Compute **cumulative** values (sum, max, min, percentage)
* Apply **ranking** (dense, regular, percent rank)
* Use **shift()** and **lag/lead** analysis
* Apply window functions partitioned by groups
* Perform advanced time-series & analytical operations

This is essential for advanced analytics, forecasting, financial modeling, and BI dashboards.

---

# **📊 Dataset: `company_sales.csv`**

Monthly revenue for multiple stores.

| month      | store | revenue |
| ---------- | ----- | ------- |
| 2023-01-01 | A     | 120000  |
| 2023-02-01 | A     | 150000  |
| 2023-03-01 | A     | 130000  |
| 2023-04-01 | A     | 170000  |
| 2023-05-01 | A     | 160000  |
| 2023-01-01 | B     | 100000  |
| 2023-02-01 | B     | 110000  |
| 2023-03-01 | B     | 115000  |
| 2023-04-01 | B     | 130000  |
| 2023-05-01 | B     | 140000  |

Works perfectly for window analytics.

---

# **📚 Topics Covered in Lesson 10**

---

# **1. Convert month to datetime & sort**

```python
df["month"] = pd.to_datetime(df["month"])
df = df.sort_values(["store", "month"])
```

---

# **2. Cumulative Functions**

### Cumulative sum (YTD revenue)

```python
df["cumulative_revenue"] = df.groupby("store")["revenue"].cumsum()
```

### Cumulative max

```python
df["cum_max"] = df.groupby("store")["revenue"].cummax()
```

### Cumulative min

```python
df["cum_min"] = df.groupby("store")["revenue"].cumin()
```

### Cumulative percentage

```python
df["cumulative_pct"] = (
    df["cumulative_revenue"] / df.groupby("store")["revenue"].sum()
)
```

---

# **3. Ranking Functions**

### Rank revenue (highest → 1)

```python
df["rank"] = df.groupby("store")["revenue"].rank(ascending=False)
```

### Dense rank

```python
df["dense_rank"] = df.groupby("store")["revenue"].rank(method="dense", ascending=False)
```

### Percent rank

```python
df["pct_rank"] = df.groupby("store")["revenue"].rank(pct=True)
```

---

# **4. Rolling Window Calculations**

### 3-month moving average

```python
df["rolling_3ma"] = (
    df.groupby("store")["revenue"]
      .rolling(window=3, min_periods=1)
      .mean()
      .reset_index(level=0, drop=True)
)
```

### 3-month rolling sum

```python
df["rolling_3sum"] = (
    df.groupby("store")["revenue"]
      .rolling(3)
      .sum()
      .reset_index(level=0, drop=True)
)
```

---

# **5. Expanding Window Calculations (from beginning)**

### Expanding mean

```python
df["expanding_mean"] = (
    df.groupby("store")["revenue"]
      .expanding()
      .mean()
      .reset_index(level=0, drop=True)
)
```

### Expanding median

```python
df["expanding_median"] = (
    df.groupby("store")["revenue"]
      .expanding()
      .median()
      .reset_index(level=0, drop=True)
)
```

---

# **6. Shift(), Lag, Lead**

### Lag revenue (previous month)

```python
df["prev_month_rev"] = df.groupby("store")["revenue"].shift(1)
```

### Growth compared to previous month

```python
df["growth"] = df["revenue"] - df["prev_month_rev"]
```

### Percentage growth

```python
df["pct_growth"] = (df["growth"] / df["prev_month_rev"]) * 100
```

### Lead (next month)

```python
df["next_month_rev"] = df.groupby("store")["revenue"].shift(-1)
```

---

# **7. Window With Custom Function**

### Rolling window custom logic

```python
df["rolling_custom"] = (
    df.groupby("store")["revenue"]
      .rolling(3)
      .apply(lambda x: (x.max() - x.min()), raw=True)
      .reset_index(level=0, drop=True)
)
```

---

# **📝 Exercises**

1. Calculate:

   * cumulative revenue
   * cumulative max
   * cumulative percentage

2. Rank revenue by:

   * normal rank
   * dense rank
   * percent rank

3. Compute:

   * 3-month moving average
   * 3-month rolling sum

4. Compute:

   * expanding mean
   * expanding median

5. Use `shift()` to:

   * compare revenue to previous month
   * calculate month-over-month percentage growth

6. Create a custom rolling function:

   * rolling range = max - min
   * rolling difference between first & last

7. Compute:

   * next month revenue (lead)
   * expected revenue difference (lead - current)

---

# **🎯 Mini-Project for Lesson 10**

## **📌 Project:** **"Executive Financial Dashboard with Window Analytics"**

Students must:

### **Step 1 — Load & prepare the dataset**

* parse dates
* sort by store & month

---

### **Step 2 — Create all window analytics**

Must include:

* cumulative revenue
* cumulative percentage
* rolling 3-month average
* rolling 3-month sum
* expanding average
* previous month revenue
* next month revenue
* month-over-month growth %
* revenue ranking

---

### **Step 3 — Produce the following reports:**

### **Report A — Store Analytics**

* best month
* worst month
* highest growth month
* cumulative performance chart (if plotting)

### **Report B — Trend Analysis**

* 3-month trend per store
* rolling comparison table
* expanding performance vs actual revenue

### **Report C — Executive Summary**

* store with highest total revenue
* store with fastest growth rate
* best and worst performing months overall

---

### **Step 4 — Export final outputs**

* `financial_window_analysis.csv`
* `store_summary.csv`
* `growth_analysis.csv`
