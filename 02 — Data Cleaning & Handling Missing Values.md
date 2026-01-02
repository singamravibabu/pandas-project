# **2 — Data Cleaning & Handling Missing Values**

### **🎯 Objective**

* Identify missing values
* Replace missing values
* Drop missing values
* Handle inconsistent data (strings, numbers, booleans)
* Work with different data types
* Clean a messy dataset step-by-step

---

# **📊 Dataset: `employees_raw.csv`**

This dataset intentionally contains:

* Missing values
* Inconsistent formatting
* Mixed data types
* Extra spaces
* Incorrect capitalization

Students can create this:

| emp_id | name       | department | age | salary  | join_date  |
| ------ | ---------- | ---------- | --- | ------- | ---------- |
| 101    | Ravi Kumar | sales      | 28  | 45000   | 2021-05-10 |
| 102    | priya devi | HR         |     | 52000   | 2020/03/15 |
| 103    | ANIL       | sales      | 32  | NaN     | 2021-07-01 |
| 104    | Sunita Rao | IT         | 25  | 48000   | 2022-01-20 |
| 105    | Rohan      | it         | 29  | 51000.0 | 20-06-2021 |
| 106    |            | Sales      | NaN | 47000   | 2021-08-12 |

Data issues present:

* Missing names
* Missing ages
* Missing salaries
* Capitalization differences (`sales`, `Sales`, `SALES`)
* Inconsistent date formats
* Extra spaces
* String numbers (`"51000.0"`)
* Mixed data types

Perfect dataset to teach cleaning.

---

# **📚 Topics Covered in Lesson 2**

---

## **1. Detecting Missing Values**

```python
df.isna()
df.isna().sum()
```

---

## **2. Filling Missing Values**

### Fill numeric values

```python
df["age"].fillna(df["age"].mean(), inplace=True)
df["salary"].fillna(df["salary"].median(), inplace=True)
```

### Fill strings

```python
df["name"].fillna("Unknown", inplace=True)
```

---

## **3. Dropping Rows with Missing Values**

```python
df.dropna(subset=["name", "department"], inplace=True)
```

---

## **4. Fixing Inconsistent Text Data**

```python
df["department"] = df["department"].str.strip().str.lower()
```

---

## **5. Cleaning Name Column**

```python
df["name"] = df["name"].str.strip().str.title()
```

---

## **6. Fixing Data Types**

### Convert salary to numeric

```python
df["salary"] = pd.to_numeric(df["salary"], errors="coerce")
```

### Convert dates to datetime

```python
df["join_date"] = pd.to_datetime(df["join_date"], errors="coerce")
```

### Convert department to category

```python
df["department"] = df["department"].astype("category")
```

---

## **7. Detecting Outliers (Simple)**

```python
df["salary"].describe()
```

---

# **📝 Exercises**

1. Load the CSV and print all missing values.
2. Replace missing ages with the **median age**.
3. Replace missing names with `"No Name"`.
4. Convert all department values to lowercase without spaces.
5. Convert salary column to numeric.
6. Convert join_date to datetime.
7. Drop rows where **salary** is still NaN after conversions.
8. Print summary statistics after cleaning.

---

# **🎯 Mini-Project for Lesson 2**

### **Project:** **"Clean Employee Master Dataset"**

Students must:

1. Load the raw dataset
2. Clean ALL the issues:

   * Missing data
   * Inconsistent capitalization
   * Wrong date formats
   * String numbers
   * Extra spaces
3. Add a new calculated column:

   * `experience_years = current_year - join_year`
4. Save the cleaned dataset as:

   * `employees_clean.csv`
