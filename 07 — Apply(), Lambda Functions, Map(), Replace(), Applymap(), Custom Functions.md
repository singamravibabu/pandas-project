# **7 — Apply(), Lambda Functions, Map(), Replace(), Applymap(), Custom Functions**

### **🎯 Objective**

* Use `apply()` for row-wise & column-wise operations
* Use `lambda` functions for custom transformations
* Use `map()` on Series
* Use `replace()` to substitute values
* Use `applymap()` on entire DataFrames
* Write user-defined functions and apply them
* Handle strings, numbers, booleans, categories, and dates through functions

---

# **📊 Dataset: `products.csv`**

This dataset includes mixed data types ideal for transformations.

| product_id | product_name  | category       | price | quantity | rating | launch_date |
| ---------- | ------------- | -------------- | ----- | -------- | ------ | ----------- |
| 1          | Laptop        | Electronics    | 55000 | 5        | 4.5    | 2023-02-10  |
| 2          | Mobile Phone  | Electronics    | 18000 | 10       | 4.2    | 2023-01-15  |
| 3          | T-Shirt       | Clothing       | 900   | 50       | 3.9    | 2023-03-05  |
| 4          | Shoes         | Clothing       | 2500  | 20       | 4.1    | 2023-02-28  |
| 5          | Microwave     | Home Appliance | 7800  | 8        | 4.3    | 2023-04-01  |
| 6          | Mixer Grinder | Home Appliance | 3500  | 12       | 3.8    | 2023-04-15  |

Includes:

* numeric: price, quantity, rating
* string: product_name, category
* datetime: launch_date

---

# **📚 Topics Covered in Lesson 7**

---

# **1. Using apply() on columns**

### Create a discount price

```python
df["discount_price"] = df["price"].apply(lambda x: x * 0.9)
```

---

# **2. Row-wise apply()**

### Classify product as “High/Medium/Low price”

```python
def classify(row):
    if row["price"] > 20000:
        return "High"
    elif row["price"] > 5000:
        return "Medium"
    else:
        return "Low"

df["price_category"] = df.apply(classify, axis=1)
```

---

# **3. Using map() for single-column mapping**

### Convert category names

```python
mapping = {
    "Electronics": "ELEC",
    "Clothing": "CLOTH",
    "Home Appliance": "HOME"
}

df["category_short"] = df["category"].map(mapping)
```

---

# **4. Using replace()**

### Replace ratings

```python
df["rating"] = df["rating"].replace({3.8: 4.0})
```

### Replace multiple values

```python
df["category"] = df["category"].replace({"Clothing": "Fashion"})
```

---

# **5. applymap() for entire DataFrame**

Only for element-wise operations.

```python
df_numeric = df[["price", "quantity"]]
df_numeric = df_numeric.applymap(lambda x: x * 2)
```

---

# **6. String operations with lambda**

### Make product names uppercase

```python
df["product_name_upper"] = df["product_name"].apply(lambda x: x.upper())
```

### Extract brand or first word

```python
df["first_word"] = df["product_name"].apply(lambda x: x.split()[0])
```

---

# **7. Apply on datetime column**

Convert to month name:

```python
df["launch_date"] = pd.to_datetime(df["launch_date"])
df["launch_month"] = df["launch_date"].apply(lambda d: d.strftime("%B"))
```

---

# **8. Apply with multiple conditions**

### Label rating

```python
df["rating_label"] = df["rating"].apply(
    lambda r: "Excellent" if r >= 4.3 else ("Good" if r >= 4.0 else "Average")
)
```

---

# **📝 Exercises**

1. Use `apply()` to create:

   * 15% discount price
   * price category (High, Medium, Low based on your own logic)

2. Use `map()` to shorten category names:

   * Electronics → ELEC
   * Clothing → CLO
   * Home Appliance → HOME

3. Replace:

   * rating 3.8 → 4.0
   * category “Clothing” → “Apparel”

4. Create a column:

   * product_name lowercase
   * extract last word from the product name

5. Convert launch_date to:

   * month number
   * weekday name

6. Create a custom function for:

   * demand level based on quantity
     (quantity > 30 → High, >10 → Medium, else Low)

7. Use `applymap()` to scale:

   * price
   * quantity
     by factor of 1.1

---

# **🎯 Mini-Project for Lesson 7**

## **📌 Project:** **"Product Intelligence Transformation System"**

Students must:

### **Step 1 — Load and clean dataset**

* convert date to datetime
* strip strings, fix formatting

### **Step 2 — Feature engineering using apply/map/lambda**

Create at least **10 new columns**, such as:

* discount price
* price category
* rating label
* launch month
* brand/first word
* quantity demand
* category short
* product_name_upper
* age_in_days = today - launch_date

### **Step 3 — Create a final transformed dataset**

### **Step 4 — Export**

* `products_transformed.csv`
