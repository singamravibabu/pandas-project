# **6 — Datetime Handling, Time-Series Analysis, Resampling & Trends**

### **🎯 Objective**

* Parse datetime columns
* Extract date parts: year, month, day, weekday
* Filter and sort using datetime
* Resample data (daily, weekly, monthly)
* Group time-series
* Build trend summaries
* Handle missing dates
* Work with multiple time-based data types

---

# **📊 Dataset: `website_traffic.csv`**

A time-series dataset representing daily website visits.

| date       | visitors | signups | sales |
| ---------- | -------- | ------- | ----- |
| 2023-01-01 | 1200     | 45      | 10    |
| 2023-01-02 | 1500     | 60      | 12    |
| 2023-01-03 | 900      | 30      | 5     |
| 2023-01-04 | 1800     | 70      | 15    |
| 2023-01-05 | 2000     | 85      | 18    |
| 2023-01-06 | 1700     | 55      | 11    |
| 2023-01-07 | 2200     | 95      | 21    |
| 2023-01-08 | 2500     | 120     | 30    |
| 2023-01-09 | 2400     | 110     | 28    |
| 2023-01-10 | 2100     | 100     | 25    |

Consistent daily data → perfect for resampling, grouping, trends.

---

# **📚 Topics Covered in Lesson 6**

---

## **1. Convert Date Column to Datetime**

```python
df["date"] = pd.to_datetime(df["date"])
```

---

## **2. Extract Date Components**

```python
df["year"] = df["date"].dt.year
df["month"] = df["date"].dt.month
df["day"] = df["date"].dt.day
df["weekday"] = df["date"].dt.day_name()
```

---

## **3. Sorting by Date**

```python
df.sort_values("date")
```

---

## **4. Filtering by Date Range**

```python
df[df["date"] >= "2023-01-05"]
df[(df["date"] >= "2023-01-03") & (df["date"] <= "2023-01-08")]
```

---

## **5. Resampling (Time-Series Aggregation)**

### Daily → Weekly

```python
df.set_index("date").resample("W").sum()
```

### Daily → Monthly

```python
df.set_index("date").resample("M").mean()
```

---

## **6. Moving Averages (Trend Analysis)**

### 3-day moving average for visitors

```python
df["visitors_3dma"] = df["visitors"].rolling(window=3).mean()
```

### 7-day moving average

```python
df["visitors_7dma"] = df["visitors"].rolling(window=7).mean()
```

---

## **7. Handling Missing Dates**

If some dates are missing:

```python
df = df.set_index("date").asfreq("D")
```

Fill missing values:

```python
df["visitors"].fillna(method="ffill", inplace=True)
```

---

## **8. Feature Engineering — Engagement Rate**

```python
df["engagement_rate"] = df["signups"] / df["visitors"]
```

---

## **9. Time-Based Grouping**

### Group by weekday

```python
df.groupby(df["date"].dt.day_name())["visitors"].mean()
```

### Group by weekend vs weekday

```python
df["is_weekend"] = df["date"].dt.weekday >= 5
df.groupby("is_weekend")["visitors"].sum()
```

---

# **📝 Exercises**

1. Convert the date column to datetime.

2. Extract year, month, day, and weekday.

3. Filter:

   * dates after 2023-01-05
   * dates between 2023-01-03 and 2023-01-07

4. Resample:

   * weekly visits
   * monthly average signups

5. Create:

   * 3-day moving average for sales
   * 5-day moving average for visitors

6. Compute engagement rate (`signups / visitors`).

7. Find:

   * busiest weekday
   * total weekend traffic

8. Handle missing dates by:

   * reindexing to daily
   * forward filling missing values

---

# **🎯 Mini-Project for Lesson 6**

### **Project:** **"Website Performance Time-Series Dashboard"**

Students must:

### **Step 1 — Load & Clean**

* convert date to datetime
* ensure sorted

### **Step 2 — Create New Columns**

* year, month, weekday
* visitors_3dma, visitors_7dma
* engagement rate

### **Step 3 — Generate Time-Based Reports**

1. Weekly traffic summary
2. Monthly signup average
3. Most active week
4. Day-wise average traffic (Mon–Sun)
5. Total weekend vs weekday visitors

### **Step 4 — Export Reports**

* `weekly_summary.csv`
* `monthly_summary.csv`
* `weekday_summary.csv`

### **Step 5 — Bonus Chart Suggestion (if using Jupyter)**

(Not required since charts weren’t requested earlier)
