## **EDA Project 3 — Customer Churn Analysis using Pandas**

### **Project Title**

📉 **Exploratory Data Analysis of Telecom Customer Churn**

---

### **Objective**

To analyze customer churn data and understand:

* Why customers leave a service
* Which customer segments churn the most
* Relationship between tenure, charges, and churn
* Service features influencing churn

---

### **Dataset**

**Name:** Telecom Customer Churn Dataset
**Format:** CSV

**Typical Columns:**

* `CustomerID`
* `Gender`
* `SeniorCitizen`
* `Tenure`
* `InternetService`
* `Contract`
* `MonthlyCharges`
* `TotalCharges`
* `PaymentMethod`
* `Churn`

You can use:

* Kaggle: *Telco Customer Churn*
* IBM sample dataset

---

### **Key Questions (EDA Goals)**

1. What percentage of customers churn?
2. Does contract type affect churn?
3. How does tenure impact churn?
4. Are monthly charges related to churn?
5. Which services retain customers better?

---

### **Step 1: Load Libraries & Data**

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv("telecom_churn.csv")
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
df['TotalCharges'] = pd.to_numeric(df['TotalCharges'], errors='coerce')
df.dropna(inplace=True)
```

---

### **Step 4: Churn Distribution**

```python
churn_rate = df['Churn'].value_counts(normalize=True) * 100
churn_rate
```

```python
sns.countplot(x='Churn', data=df)
plt.title("Customer Churn Distribution")
plt.show()
```

---

### **Step 5: Contract Type vs Churn**

```python
df.groupby('Contract')['Churn'].value_counts(normalize=True).unstack()
```

```python
sns.countplot(x='Contract', hue='Churn', data=df)
plt.title("Churn by Contract Type")
plt.show()
```

---

### **Step 6: Tenure Analysis**

```python
sns.boxplot(x='Churn', y='Tenure', data=df)
plt.title("Tenure vs Churn")
plt.show()
```

---

### **Step 7: Monthly Charges vs Churn**

```python
sns.boxplot(x='Churn', y='MonthlyCharges', data=df)
plt.title("Monthly Charges vs Churn")
plt.show()
```

---

### **Step 8: Internet Service Impact**

```python
df.groupby('InternetService')['Churn'].value_counts(normalize=True).unstack()
```

---

### **Insights You Can Derive**

* Month-to-month contracts have higher churn
* Customers with higher monthly charges churn more
* Longer tenure → lower churn probability
* Certain internet services retain customers better

---

### **Skills Demonstrated**

✅ Binary classification insight
✅ Business analytics
✅ Feature relationship analysis
✅ Customer segmentation
✅ Visualization & storytelling

---
