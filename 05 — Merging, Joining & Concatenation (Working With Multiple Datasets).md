# **5 — Merging, Joining & Concatenation (Working With Multiple Datasets)**

### **🎯 Objective**

* Combine datasets using `merge()`
* Perform **inner, left, right, and outer joins**
* Use `concat()` for stacking datasets
* Join on single & multiple keys
* Handle unmatched rows
* Clean up duplicates after merging
* Work with realistic multi-table structures (fact + dimensions)

---

# **📊 Datasets: For This Lesson, You Will Use Three CSV Files**

These datasets are intentionally designed for real-world merging tasks.

---

## **1️⃣ `customers.csv`**

| customer_id | customer_name | city      |
| ----------- | ------------- | --------- |
| 1           | Ravi Kumar    | Hyderabad |
| 2           | Priya Devi    | Chennai   |
| 3           | Akshay        | Mumbai    |
| 4           | Sunita        | Hyderabad |
| 5           | Kiran         | Delhi     |

---

## **2️⃣ `orders.csv`**

| order_id | customer_id | product      | category       | price | quantity |
| -------- | ----------- | ------------ | -------------- | ----- | -------- |
| 101      | 1           | Laptop       | electronics    | 55000 | 1        |
| 102      | 2           | Jeans        | clothing       | 1500  | 2        |
| 103      | 3           | Mobile Phone | electronics    | 18000 | 1        |
| 104      | 3           | Shoes        | clothing       | 2500  | 1        |
| 105      | 5           | Microwave    | home_appliance | 7800  | 1        |
| 106      | 6           | T-Shirt      | clothing       | 900   | 3        |

Note:

* `customer_id = 6` does **not** exist in customers → good for join practice

---

## **3️⃣ `returns.csv`**

| order_id | return_reason  |
| -------- | -------------- |
| 104      | Defective item |
| 105      | Size issue     |

---

# **📚 Topics Covered in Lesson 5**

---

## **1. Basic Merge (Join customers + orders)**

```python
df = orders.merge(customers, on="customer_id", how="inner")
```

---

## **2. Types of Joins**

### **Inner Join**

```python
orders.merge(customers, on="customer_id", how="inner")
```

### **Left Join** (keep all orders)

```python
orders.merge(customers, on="customer_id", how="left")
```

### **Right Join** (keep all customers)

```python
orders.merge(customers, on="customer_id", how="right")
```

### **Outer Join** (keep everything)

```python
orders.merge(customers, on="customer_id", how="outer")
```

---

## **3. Adding Return Data (Join on Different Keys)**

```python
orders.merge(returns, on="order_id", how="left")
```

---

## **4. Multi-Key Merge**

You can join on multiple columns (not needed here, but important):

```python
df1.merge(df2, on=["customer_id", "product_id"])
```

---

## **5. Handling Unmatched Rows**

```python
merged = orders.merge(customers, on="customer_id", how="left")
merged[merged["customer_name"].isna()]
```

Useful for detecting:

* orphan orders
* missing customer data
* invalid keys

---

## **6. Concatenation (Stacking Datasets)**

### Row-wise (vertical)

```python
df_all_orders = pd.concat([orders_jan, orders_feb, orders_mar])
```

### Column-wise (horizontal)

```python
df_wide = pd.concat([df1, df2], axis=1)
```

---

## **7. Removing Duplicate Rows After Merge**

```python
df.drop_duplicates(inplace=True)
```

---

# **📝 Exercises**

1. Perform an **inner**, **left**, **right**, and **outer** join between customers & orders.

2. Identify invalid customer IDs in orders (those who don’t exist in customers).

3. Merge orders with returns to show which orders were returned.

4. Find:

   * which customer has returned items
   * total returned orders per customer

5. Perform a left join and then:

   * Create a column `is_returned = True/False`
   * Fill missing values with `"Not Returned"`

6. Concatenate:

   * Create 2 small order datasets and stack them using `concat()`

---

# **🎯 Mini-Project for Lesson 5**

## **📌 Project:** **"Customer–Order–Returns Master Dataset"**

Students must:

### **Step 1 — Load all three datasets**

### **Step 2 — Merge them**

* Join customers + orders (left join)
* Join returns afterwards (left join)

### **Step 3 — Add new fields**

* `revenue = price * quantity`
* `is_returned` (boolean)

### **Step 4 — Analysis**

1. Total revenue per customer
2. Number of orders per customer
3. Number of returned orders per customer
4. Identify customers with:

   * highest spending
   * highest return rate

### **Step 5 — Export Outputs**

* `master_dataset.csv`
* `customer_summary.csv`
* `returns_summary.csv`
