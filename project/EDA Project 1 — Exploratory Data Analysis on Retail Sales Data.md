## **EDA Project 1 — Exploratory Data Analysis on Retail Sales Data**

### **Project Title**

📊 **Retail Store Sales Analysis using Pandas**

---

### **Objective**

To analyze retail sales data to understand:

* Sales trends over time
* Best-selling products
* Revenue contribution by category
* Customer purchase behavior

---

### **Dataset**

**Name:** Retail Sales Dataset
**Format:** CSV
**Typical Columns:**

* `InvoiceNo`
* `Date`
* `CustomerID`
* `Product`
* `Category`
* `Quantity`
* `UnitPrice`
* `TotalAmount`
* `Country`

You can use:

* Kaggle: *Online Retail Dataset*
* Or create a synthetic dataset (good for teaching)

---

### **Key Questions (EDA Goals)**

1. What is the total revenue?
2. Which products generate the highest sales?
3. Which categories contribute most to revenue?
4. How do sales vary monthly?
5. Which countries/customers buy the most?

---

### **Step 1: Import Libraries**

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

---

### **Step 2: Load Dataset**

```python
df = pd.read_csv("retail_sales.csv")
df.head()
```

---

### **Step 3: Basic Exploration**

```python
df.info()
df.describe()
df.isnull().sum()
```

---

### **Step 4: Data Cleaning**

```python
df.dropna(inplace=True)
df['Date'] = pd.to_datetime(df['Date'])
df['TotalAmount'] = df['Quantity'] * df['UnitPrice']
```

---

### **Step 5: Revenue Analysis**

```python
total_revenue = df['TotalAmount'].sum()
print("Total Revenue:", total_revenue)
```

---

### **Step 6: Top-Selling Products**

```python
top_products = df.groupby('Product')['TotalAmount'].sum().sort_values(ascending=False).head(10)
top_products
```

---

### **Step 7: Category-wise Sales**

```python
category_sales = df.groupby('Category')['TotalAmount'].sum()
category_sales.plot(kind='bar', title='Sales by Category')
plt.show()
```

---

### **Step 8: Monthly Sales Trend**

```python
df['Month'] = df['Date'].dt.to_period('M')
monthly_sales = df.groupby('Month')['TotalAmount'].sum()

monthly_sales.plot(figsize=(10,5), title='Monthly Sales Trend')
plt.show()
```

---

### **Insights You Can Derive**

* Seasonal sales patterns
* High-performing product categories
* Customer purchasing concentration
* Business growth or decline trends

---

### **Skills Demonstrated**

✅ Pandas data cleaning
✅ GroupBy operations
✅ Time-series analysis
✅ Visualization
✅ Business insights

---
