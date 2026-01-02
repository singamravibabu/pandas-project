# **4 — GroupBy, Aggregations, Pivot Tables & Summaries**

### **🎯 Objective**

* Use `groupby()` effectively
* Apply multiple aggregations (`sum`, `mean`, `count`, `max`, etc.)
* Group by multiple columns
* Create pivot tables
* Generate summary reports
* Work with numeric, string, and date-based aggregations

---

# **📊 Dataset: `orders.csv`**

A medium-sized dataset perfect for grouping & summaries.

| order_id | customer | product       | category       | price | quantity | order_date | city      |
| -------- | -------- | ------------- | -------------- | ----- | -------- | ---------- | --------- |
| 1        | Ravi     | Laptop        | electronics    | 55000 | 1        | 2023-01-05 | Hyderabad |
| 2        | Akshay   | Mobile Phone  | electronics    | 18000 | 2        | 2023-01-12 | Mumbai    |
| 3        | Priya    | Mixer Grinder | home_appliance | 3200  | 1        | 2023-02-10 | Chennai   |
| 4        | Sunita   | Shoes         | clothing       | 2500  | 3        | 2023-02-15 | Hyderabad |
| 5        | Manoj    | Jeans         | clothing       | 1500  | 2        | 2023-03-01 | Delhi     |
| 6        | Kiran    | Laptop        | electronics    | 57000 | 1        | 2023-03-05 | Mumbai    |
| 7        | Ravi     | Microwave     | home_appliance | 7800  | 1        | 2023-03-20 | Hyderabad |
| 8        | Priya    | T-Shirt       | clothing       | 900   | 4        | 2023-04-01 | Chennai   |
| 9        | Akshay   | Earphones     | electronics    | 700   | 3        | 2023-04-15 | Delhi     |
| 10       | Sunita   | Mixer Grinder | home_appliance | 3500  | 1        | 2023-05-10 | Hyderabad |

Covers:

* numeric fields
* categories
* dates
* customer dimension
* city dimension

---

# **📚 Topics Covered in Lesson 4**

---

## **1. Basic GroupBy**

### Total revenue per category

```python
df.groupby("category")["price"].sum()
```

---

## **2. Multiple Aggregations**

```python
df.groupby("category").agg({
    "price": ["sum", "mean", "max"],
    "quantity": "sum"
})
```

---

## **3. Grouping by Multiple Columns**

```python
df.groupby(["city", "category"])["price"].sum()
```

---

## **4. Adding Calculated Columns Before Grouping**

Add revenue column:

```python
df["revenue"] = df["price"] * df["quantity"]
```

Then:

```python
df.groupby("customer")["revenue"].sum()
```

---

## **5. Using `size()` and `count()`**

### Number of orders per category:

```python
df.groupby("category").size()
```

### Count non-null customer entries:

```python
df.groupby("city")["customer"].count()
```

---

## **6. Pivot Tables (Excel-style)**

### Total revenue by city and category:

```python
df.pivot_table(
    values="revenue",
    index="city",
    columns="category",
    aggfunc="sum",
    fill_value=0
)
```

---

## **7. Pivot Table With Multiple Aggregations**

```python
df.pivot_table(
    values="price",
    index="category",
    columns="city",
    aggfunc=["mean", "max", "count"],
    fill_value=0
)
```

---

## **8. GroupBy on Dates (Monthly Sales)**

Convert date column:

```python
df["order_date"] = pd.to_datetime(df["order_date"])
df["month"] = df["order_date"].dt.to_period("M")
```

Monthly revenue:

```python
df.groupby("month")["revenue"].sum()
```

---

# **📝 Exercises**

1. Group by category and find:

   * total revenue
   * average price
   * total quantity sold

2. Group by customer and find:

   * total spending
   * number of orders

3. Create a revenue column and group by city.

4. Create a pivot table:

   * index → city
   * columns → category
   * values → quantity
   * aggfunc → sum

5. Find monthly revenue using:

   * `groupby()`
   * `pivot_table()`

6. Group by category and city (multi-index) to find:

   * sum of revenue
   * count of orders

---

# **🎯 Mini-Project for Lesson 4**

### **Project:** **"City & Category Sales Report"**

Students must:

1. Load the dataset
2. Create `revenue`, `month`, and `year` fields
3. Generate the following reports:

---

### **Report 1: Category Summary**

* Total revenue
* Average price
* Total quantity
* Number of orders

---

### **Report 2: City Summary**

* Total revenue
* Most sold category
* Average order value

---

### **Report 3: Pivot Dashboard**

Pivot Table 1:

* Revenue by city (index) vs category (columns)

Pivot Table 2:

* Quantity by category (index) vs customer (columns)

---

### **Report 4: Monthly Revenue Trend**

Use groupby or pivot.

---

### **Final Output Files**

* `summary_category.csv`
* `summary_city.csv`
* `pivot_revenue_city_category.csv`
* `monthly_revenue.csv`
