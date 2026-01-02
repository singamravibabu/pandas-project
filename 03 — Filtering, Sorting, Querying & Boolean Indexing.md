# **3 — Filtering, Sorting, Querying & Boolean Indexing**

### **🎯 Objective**

Students will learn how to:

* Filter rows using conditions
* Apply multiple conditions using `&` and `|`
* Use `.query()` for complex filters
* Sort data (ascending & descending)
* Filter using string methods
* Work with boolean masks
* Filter based on numerical, string, and date data types

---

# **📊 Dataset: `sales_data.csv`**

A small but realistic dataset for filtering, sorting, and querying.

| sale_id | product      | category       | price | quantity | sale_date  | store |
| ------- | ------------ | -------------- | ----- | -------- | ---------- | ----- |
| 1       | Laptop       | electronics    | 55000 | 2        | 2023-01-12 | A     |
| 2       | Mobile Phone | electronics    | 18000 | 5        | 2023-01-15 | B     |
| 3       | T-Shirt      | clothing       | 800   | 10       | 2023-02-10 | A     |
| 4       | Shoes        | clothing       | 2500  | 3        | 2023-03-05 | C     |
| 5       | Blender      | home_appliance | 3200  | 1        | 2023-03-18 | B     |
| 6       | Laptop       | electronics    | 53000 | 1        | 2023-04-02 | C     |
| 7       | Jeans        | clothing       | 1500  | 4        | 2023-04-15 | A     |
| 8       | Microwave    | home_appliance | 7800  | 2        | 2023-05-01 | B     |
| 9       | T-Shirt      | clothing       | 900   | 15       | 2023-06-05 | C     |
| 10      | Earphones    | electronics    | 700   | 8        | 2023-06-20 | A     |

Covers:

* String columns
* Numeric columns
* Date column
* Category column
* Great for filtering, querying, sorting

---

# **📚 Topics Covered in Lesson 3**

---

## **1. Filtering Rows With One Condition**

```python
df[df["price"] > 5000]
```

---

## **2. Multiple Conditions**

```python
df[(df["category"] == "electronics") & (df["price"] > 20000)]
```

Use:

* `&` → AND
* `|` → OR
* `~` → NOT

---

## **3. Filtering Using `.query()`**

```python
df.query("category == 'clothing' and quantity > 5")
```

---

## **4. String-Based Filtering**

```python
df[df["product"].str.contains("shirt", case=False)]
```

---

## **5. Filtering by Dates**

```python
df["sale_date"] = pd.to_datetime(df["sale_date"])
df[df["sale_date"] >= "2023-03-01"]
```

---

## **6. Sorting Data**

### Sort by price:

```python
df.sort_values("price")
df.sort_values("price", ascending=False)
```

### Sort by multiple columns:

```python
df.sort_values(["category", "price"], ascending=[True, False])
```

---

## **7. Boolean Masks**

```python
mask = df["quantity"] > 5
df[mask]
```

---

## **8. Filter Unique Values**

```python
df["category"].unique()
df["category"].value_counts()
```

---

# **📝 Exercises**

1. Filter all rows where:

   * price > 10,000
   * category is "clothing"
   * quantity ≥ 5

2. Filter all electronics sold in stores A or C.

3. Show all sales between March and June 2023.

4. Sort:

   * by price descending
   * by quantity ascending
   * by category ascending and price descending

5. Find all products whose names contain:

   * `"shirt"`
   * `"lap"`

6. Use `query()` to find:

   * electronics with quantity > 2
   * clothing items under ₹1000

---

# **🎯 Mini-Project for Lesson 3**

### **Project:** **"Sales Analytics — Filtering & Reporting Tool"**

Students must:

1. Load the dataset

2. Create the following filtered views:

   * High-value sales (price > 20,000)
   * Clothing category with quantity ≥ 8
   * All home appliances sold in March → June 2023
   * Electronics sorted by price descending

3. Create a summary table:

   * total sales per category
   * average price per category
   * total quantity sold per store

4. Export each filtered dataset to:

   * `filter_high_value.csv`
   * `filter_clothing.csv`
   * `filter_electronics.csv`
