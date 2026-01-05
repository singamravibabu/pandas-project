## **EDA Project 4 — COVID-19 Data Analysis using Pandas**

### **Project Title**

🦠 **Exploratory Data Analysis of COVID-19 Pandemic Data**

---

### **Objective**

To analyze COVID-19 data to understand:

* Spread of cases over time
* Country-wise impact
* Death and recovery trends
* Relationship between cases, deaths, and recoveries

---

### **Dataset**

**Name:** COVID-19 Global Dataset
**Format:** CSV

**Typical Columns:**

* `Date`
* `Country`
* `Confirmed`
* `Deaths`
* `Recovered`
* `Active`
* `NewCases`
* `NewDeaths`

You can use:

* Johns Hopkins University COVID-19 Dataset
* Kaggle COVID-19 datasets

---

### **Key Questions (EDA Goals)**

1. How did cases grow over time?
2. Which countries were most affected?
3. What is the death rate per country?
4. How do recoveries compare to confirmed cases?
5. When did peaks occur?

---

### **Step 1: Load Libraries & Data**

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv("covid_data.csv")
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
df.fillna(0, inplace=True)
```

---

### **Step 4: Global Case Trends**

```python
global_cases = df.groupby('Date')[['Confirmed','Deaths','Recovered']].sum()

global_cases.plot(figsize=(12,6))
plt.title("Global COVID-19 Trends")
plt.xlabel("Date")
plt.ylabel("Cases")
plt.show()
```

---

### **Step 5: Top Affected Countries**

```python
top_countries = (
    df.groupby('Country')['Confirmed']
    .max()
    .sort_values(ascending=False)
    .head(10)
)
top_countries
```

---

### **Step 6: Death Rate Analysis**

```python
country_stats = df.groupby('Country').max()
country_stats['DeathRate'] = (
    country_stats['Deaths'] / country_stats['Confirmed']
) * 100

country_stats[['DeathRate']].sort_values(by='DeathRate', ascending=False).head(10)
```

---

### **Step 7: Active Cases Trend**

```python
sns.lineplot(data=df, x='Date', y='Active', hue='Country')
plt.title("Active COVID-19 Cases Over Time")
plt.show()
```

---

### **Step 8: Correlation Analysis**

```python
df[['Confirmed','Deaths','Recovered','Active']].corr()
```

---

### **Insights You Can Derive**

* Pandemic growth patterns and waves
* Countries with high fatality rates
* Recovery efficiency comparisons
* Strong correlation between confirmed and deaths

---

### **Skills Demonstrated**

✅ Time-series analysis
✅ Aggregation across geography
✅ Public health insights
✅ Correlation analysis
✅ Pandas + visualization mastery

---
