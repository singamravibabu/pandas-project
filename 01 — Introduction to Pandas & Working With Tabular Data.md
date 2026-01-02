# **1 — Introduction to Pandas & Working With Tabular Data**

### **🎯 Objective**

* Install pandas and import it
* Load data into DataFrames
* Understand Series vs DataFrame
* Explore data (head, tail, info, describe)
* Handle different data types (numeric, object/string, boolean)

---

# **📊 Dataset: `students_basic.csv`**

Students can create this as a CSV:

| student_id | name    | age | grade | passed |
| ---------- | ------- | --- | ----- | ------ |
| 1          | Ravi    | 15  | 88    | True   |
| 2          | Priya   | 16  | 92    | True   |
| 3          | Karthik | 15  | 76    | False  |
| 4          | Ananya  | 17  | 85    | True   |
| 5          | Suresh  | 16  | 67    | False  |

Data Types:

* `student_id`: integer
* `name`: string
* `age`: integer
* `grade`: numeric
* `passed`: boolean

Perfect for beginners to learn the basics.

---

# **📚 Topics Covered in Lesson 1**

### 1. Installing and Importing Pandas

```python
import pandas as pd
```

---

### 2. Loading the Dataset

```python
df = pd.read_csv("students_basic.csv")
```

---

### 3. Viewing Data

```python
df.head()
df.tail()
```

---

### 4. Checking Structure

```python
df.info()
df.dtypes
```

---

### 5. Basic Statistics

```python
df.describe()
```

---

### 6. Selecting Columns

```python
df["name"]
df[["name", "grade"]]
```

---

### 7. Selecting Rows (loc & iloc)

```python
df.loc[0]
df.iloc[0:3]
```

---

# **📝 Exercises**

1. Load the dataset and display:

   * First 3 rows
   * Last 2 rows

2. Print:

   * Only names
   * Only passed students

3. Show:

   * Data types
   * Summary statistics

4. Create a new column:

   * `status` → "Excellent" if grade ≥ 90 else "Normal"

---

# **🎯 Mini-Project for Lesson 1**

**Project:** *"Student Performance Viewer"*

Students must write a script that:

1. Loads the CSV
2. Prints:

   * Total students
   * Average grade
   * Count of passed vs failed
3. Shows the top 3 scoring students
4. Saves them into a new CSV: `top_students.csv`
