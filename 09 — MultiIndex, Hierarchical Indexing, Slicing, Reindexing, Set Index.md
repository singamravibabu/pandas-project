# **9 — MultiIndex, Hierarchical Indexing, Slicing, Reindexing, Set Index**

### **🎯 Objective**

* Create and use **MultiIndex / Hierarchical Index**
* Slice MultiIndex rows & columns
* Set and reset index efficiently
* Reindex with new labels
* Use `.loc` and `.xs` with MultiIndex
* Sort MultiIndex
* Filter using MultiIndex
* Understand advanced indexing in real analytics contexts

---

# **📊 Dataset: `sales_store.csv`**

This dataset has natural multi-level dimensions: **store**, **year**, **quarter**.

| store | year | quarter | product | revenue |
| ----- | ---- | ------- | ------- | ------- |
| A     | 2022 | Q1      | Laptop  | 120000  |
| A     | 2022 | Q2      | Laptop  | 150000  |
| A     | 2022 | Q3      | Shoes   | 30000   |
| A     | 2022 | Q4      | T-Shirt | 45000   |
| B     | 2022 | Q1      | Mobile  | 90000   |
| B     | 2022 | Q2      | Mobile  | 110000  |
| B     | 2022 | Q3      | Shoes   | 35000   |
| B     | 2022 | Q4      | Jeans   | 40000   |
| C     | 2022 | Q1      | Laptop  | 100000  |
| C     | 2022 | Q2      | T-Shirt | 50000   |

---

# **📚 Topics Covered in Lesson 9**

---

# **1. Setting a MultiIndex**

```python
df = df.set_index(["store", "year", "quarter"])
```

Index becomes:

* level 1 → store
* level 2 → year
* level 3 → quarter

---

# **2. Accessing Data with MultiIndex**

### Using `.loc`

```python
df.loc["A"]
df.loc[("A", 2022)]
df.loc[("A", 2022, "Q2")]
```

---

# **3. Slicing MultiIndex**

### Range slice

```python
df.loc["A":"B"]
```

### Slice inner levels

```python
df.loc[("A", slice(None), slice(None)), :]
```

### Slice specific range in inner level:

```python
df.loc[(slice("A","B"), 2022, slice("Q1","Q3")), :]
```

---

# **4. Selecting a Cross-Section (xs)**

Great for selecting one level only:

### All stores, Q2:

```python
df.xs("Q2", level="quarter")
```

### All quarters for store “A”

```python
df.xs("A", level="store")
```

---

# **5. Resetting Index**

```python
df_reset = df.reset_index()
```

---

# **6. Sorting MultiIndex**

```python
df = df.sort_index()
df = df.sort_index(level="quarter")
```

---

# **7. Filter MultiIndex with boolean mask**

```python
df[df["revenue"] > 50000]
```

---

# **8. Reindexing**

### Add missing quarters for each store

```python
new_index = pd.MultiIndex.from_product(
    [["A", "B", "C"], [2022], ["Q1","Q2","Q3","Q4"]],
    names=["store","year","quarter"]
)

df2 = df.reindex(new_index)
```

Fill missing values:

```python
df2["revenue"].fillna(0, inplace=True)
```

---

# **9. Multi-Level Aggregations with MultiIndex**

### Total revenue by store

```python
df.groupby(level="store")["revenue"].sum()
```

### Total revenue by year & quarter

```python
df.groupby(level=["year","quarter"])["revenue"].sum()
```

---

# **📝 Exercises**

1. Set a MultiIndex using store, year, quarter.

2. Slice:

   * revenue for store A
   * all Q2 revenue across stores
   * all data for year 2022

3. Use `.xs()` to get:

   * all Laptop sales (product-level cross-section)
   * all Q3 rows

4. Reindex to include all stores and all quarters, filling missing revenue with 0.

5. Sort the index by:

   * store
   * quarter

6. Reset the index and turn it back into MultiIndex later.

7. Create a new column:

   * `"high_value"` if revenue > 100000

8. Group by MultiIndex levels and create:

   * total revenue per store
   * total revenue per quarter

---

# **🎯 Mini-Project for Lesson 9**

## **📌 Project:** **"Advanced Multi-Level Sales Dashboard"**

Students must:

### **Step 1 — Load & MultiIndex the data**

* index: store, year, quarter

### **Step 2 — Perform slicing**

* Store A → Q1–Q3 only
* All stores → Q2 only
* Year 2022 → All quarters

### **Step 3 — Create cross-sections**

* Quarter-wise revenue summary
* Store-wise revenue summary

### **Step 4 — Reindex**

* Add Q4 for Store C
* Add Q3 for Store A and B

Fill missing revenue with 0.

### **Step 5 — Create summary tables**

* total revenue per store
* total revenue per quarter
* best quarter per store
* average revenue per product category

### **Step 6 — Export dataset**

* `sales_multilevel.csv`
* `summary_store.csv`
* `summary_quarter.csv`
