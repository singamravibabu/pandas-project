# **8 — Melt, Stack, Unstack, Wide ↔ Long Transformation, Crosstab**

### **🎯 Objective**

* Convert **wide to long** format using `melt()`
* Convert **long to wide** format using `pivot()`, `pivot_table()`
* Use `stack()` & `unstack()` for hierarchical index reshaping
* Use `crosstab()` for frequency & comparison tables
* Work with multi-level indexes
* Reshape data for reporting, analytics, and visualization

---

# **📊 Dataset: `sales_quarter.csv`**

A wide-format dataset representing quarterly product sales.

| product | Q1_sales | Q2_sales | Q3_sales | Q4_sales |
| ------- | -------- | -------- | -------- | -------- |
| Laptop  | 150      | 180      | 200      | 220      |
| Mobile  | 300      | 350      | 370      | 400      |
| Shoes   | 120      | 140      | 130      | 150      |
| T-Shirt | 200      | 210      | 220      | 230      |

Perfect for teaching reshaping.

---

# **📚 Topics Covered in Lesson 8**

---

# **1. Wide → Long Format (melt)**

Turn Q1–Q4 sales into rows:

```python
df_long = df.melt(
    id_vars="product",
    value_vars=["Q1_sales", "Q2_sales", "Q3_sales", "Q4_sales"],
    var_name="quarter",
    value_name="sales"
)
```

Result:

| product | quarter  | sales |
| ------- | -------- | ----- |
| Laptop  | Q1_sales | 150   |
| Laptop  | Q2_sales | 180   |
| ...     | ...      | ...   |

---

# **2. Cleaning Melted Data (Optional)**

Remove `_sales` suffix:

```python
df_long["quarter"] = df_long["quarter"].str.replace("_sales", "")
```

---

# **3. Long → Wide Format (pivot)**

Convert back:

```python
df_wide = df_long.pivot(
    index="product",
    columns="quarter",
    values="sales"
)
```

---

# **4. Using `pivot_table()` for aggregation**

Equivalent to pivot but handles duplicates:

```python
df_pivot = df_long.pivot_table(
    index="product",
    columns="quarter",
    values="sales",
    aggfunc="sum"
)
```

---

# **5. stack() & unstack() (MultiIndex reshaping)**

### Unstack:

```python
df_long.groupby(["product", "quarter"])["sales"].sum().unstack()
```

### Stack:

```python
df_wide.stack()
```

---

# **6. Crosstab (Excel-like frequency table)**

Useful for comparing two categorical variables.

Example dataset for this part:

| customer | product | city      |
| -------- | ------- | --------- |
| Ravi     | Laptop  | Hyderabad |
| Priya    | Mobile  | Chennai   |
| Akshay   | Laptop  | Mumbai    |
| Kiran    | Shoes   | Delhi     |
| Ravi     | Mobile  | Hyderabad |

### Crosstab: count of customers by city vs product

```python
pd.crosstab(df["city"], df["product"])
```

---

# **7. Adding Totals to Crosstab**

```python
pd.crosstab(
    df["city"], 
    df["product"], 
    margins=True
)
```

---

# **8. Normalized Crosstab (Percentages)**

```python
pd.crosstab(
    df["city"], 
    df["product"], 
    normalize="index"
)
```

---

# **9. Multi-Level Crosstab**

```python
pd.crosstab(
    [df["city"], df["customer"]],
    df["product"]
)
```

---

# **📝 Exercises**

1. Convert `sales_quarter.csv` to long format using melt.

2. Remove `_sales` from the melted “quarter” column.

3. Convert the melted data back to wide format using:

   * `pivot`
   * `pivot_table`

4. Create a multi-level index with:

   * product
   * quarter
     and unstack it.

5. Create a crosstab using the mini customer–product–city dataset:

   * rows → city
   * columns → product

6. Create normalized (percentage) crosstabs.

7. Build a 2-level crosstab:

   * rows → city + customer
   * columns → product

---

# **🎯 Mini-Project for Lesson 8**

## **📌 Project:** **"Quarterly Sales Reshaping Dashboard"**

Students must:

### **Step 1 — Load the dataset**

### **Step 2 — Create THREE datasets:**

* long format (melted)
* summary wide format (pivot)
* stacked/unstacked reshaped format

### **Step 3 — Compute Advanced Analytics**

* total sales per product
* average quarterly sales per product
* best quarter per product
* difference between Q4 and Q1 sales

### **Step 4 — Crosstab Analysis**

Using a helper dataset (customers vs product):

* product popularity by city
* percentage distribution of each product per city
* most popular product per city

### **Step 5 — Export to CSV**

* `sales_long.csv`
* `sales_wide.csv`
* `sales_unstacked.csv`
* `sales_crosstab.csv`
