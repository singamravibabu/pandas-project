# **📘 PANDAS PRACTICAL TRAINING — PROJECT BOOKLET & ASSIGNMENT SHEET**

### *10 Lessons + 10 Datasets + 10 Mini-Projects*

**Course Level:** Beginner → Advanced
**Tools Required:** Python, Pandas, Jupyter Notebook / VS Code
**Datasets Provided:** 13 CSV files (10 main + helper files)

---

# **📖 TABLE OF CONTENTS**

1. **Lesson 1 – Introduction to Pandas**
2. **Lesson 2 – Data Cleaning & Missing Values**
3. **Lesson 3 – Filtering, Sorting & Querying**
4. **Lesson 4 – GroupBy, Aggregations & Pivot Tables**
5. **Lesson 5 – Joining, Merging & Concatenation**
6. **Lesson 6 – Datetime Handling & Time-Series**
7. **Lesson 7 – Apply, Lambda, Map, Replace**
8. **Lesson 8 – Reshaping (Melt, Pivot, Crosstab)**
9. **Lesson 9 – MultiIndex & Hierarchical Indexing**
10. **Lesson 10 – Window Functions & Rolling Analytics**

Each lesson includes:

✅ Dataset
✅ Learning Outcomes
✅ Tasks / Questions
✅ Mini-Project

---

# **📚 LESSON 1 — Introduction to Pandas**

### **Dataset:** `students_basic.csv`

### **Learning Outcomes**

* Load CSV files
* Understand DataFrame & Series
* Inspect data using `head`, `info`, `describe`
* Select rows & columns

### **Tasks**

1. Load the dataset and print first/last 5 rows.
2. Show data types and summary statistics.
3. Select only the columns: name, grade.
4. Filter students who passed.

### **Mini-Project 1 — Student Performance Viewer**

* Compute average grade
* Count passed vs failed
* Export top 3 students to `top_students.csv`

---

# **📚 LESSON 2 — Data Cleaning & Missing Values**

### **Dataset:** `employees_raw.csv`

### **Learning Outcomes**

* Identify missing values
* Clean messy strings
* Fix dates, numeric types
* Handle inconsistent data

### **Tasks**

1. Detect missing names, ages, salaries.
2. Clean department names (lowercase & trim).
3. Convert salary to numeric.
4. Convert join_date to datetime.

### **Mini-Project 2 — Clean Employee Master Dataset**

* Clean all columns
* Add `experience_years`
* Export cleaned data to `employees_clean.csv`

---

# **📚 LESSON 3 — Filtering, Sorting & Querying**

### **Dataset:** `sales_data.csv`

### **Learning Outcomes**

* Boolean indexing
* String-based filters
* Date filtering
* Sorting

### **Tasks**

1. Filter rows where price > 10,000.
2. Show all electronics sold in store A or C.
3. Filter sales between March–June 2023.
4. Find products containing “shirt”.

### **Mini-Project 3 — Sales Filtering & Reporting**

Create filtered datasets for:

* high-value sales
* clothing with quantity ≥ 8
* electronics sorted by price

Export to CSV.

---

# **📚 LESSON 4 — GroupBy, Aggregations & Pivot Tables**

### **Dataset:** `orders_l4.csv`

### **Learning Outcomes**

* GroupBy: sum, mean, max
* Multi-column grouping
* Pivot tables
* Monthly summaries

### **Tasks**

1. Compute total revenue per category.
2. Group by customer: total revenue.
3. Pivot: revenue by city & category.
4. Group monthly revenue.

### **Mini-Project 4 — City & Category Sales Report**

Generate and export:

* `summary_category.csv`
* `summary_city.csv`
* `pivot_revenue_city_category.csv`

---

# **📚 LESSON 5 — Merging, Joining & Concatenation**

### **Datasets:**

* `customers_l5.csv`
* `orders_l5.csv`
* `returns_l5.csv`

### **Learning Outcomes**

* Inner/left/right/outer join
* Multi-table relationships
* Detect unmatched rows

### **Tasks**

1. Perform all 4 join types.
2. Identify invalid customer IDs.
3. Merge returns with orders.

### **Mini-Project 5 — Customer–Order–Returns Master File**

Produce:

* master_dataset.csv
* customer_summary.csv
* returns_summary.csv

---

# **📚 LESSON 6 — Datetime Handling & Time-Series**

### **Dataset:** `website_traffic.csv`

### **Learning Outcomes**

* Convert to datetime
* Extract year/month/day
* Resampling (weekly/monthly)
* Moving averages

### **Tasks**

1. Extract weekday, month, year.
2. Weekly and monthly summaries.
3. 3-day & 7-day rolling averages.

### **Mini-Project 6 — Website Time-Series Dashboard**

Export:

* weekly_summary.csv
* monthly_summary.csv
* weekday_summary.csv

---

# **📚 LESSON 7 — Apply, Lambda, Map & Replace**

### **Dataset:** `products.csv`

### **Learning Outcomes**

* Apply & lambda for row/column operations
* Map & replace
* String operations
* Custom row-based functions

### **Tasks**

1. Create discount_price.
2. Create rating_label.
3. Map category → short code.
4. Extract brand names.

### **Mini-Project 7 — Product Intelligence System**

Produce at least **10 new engineered columns** and export:

* products_transformed.csv

---

# **📚 LESSON 8 — Melt, Pivot, Stack & Crosstab**

### **Datasets:**

* `sales_quarter.csv`
* `customer_city_product.csv`

### **Learning Outcomes**

* Wide ↔ Long transformations
* Pivot and unstack
* Crosstabs

### **Tasks**

1. Melt Q1–Q4 to long format.
2. Pivot back to wide format.
3. Crosstab of city vs product.

### **Mini-Project 8 — Quarterly Sales Reshaping Dashboard**

Export:

* sales_long.csv
* sales_wide.csv
* sales_crosstab.csv

---

# **📚 LESSON 9 — MultiIndex & Hierarchical Indexing**

### **Dataset:** `sales_store.csv`

### **Learning Outcomes**

* Create MultiIndex
* Slice using loc and xs
* Reindex
* Sort MultiIndex

### **Tasks**

1. Set MultiIndex (store, year, quarter).
2. Slice store A, Q1–Q3.
3. Extract cross-section for Q2.

### **Mini-Project 9 — Multi-Level Sales Dashboard**

Export:

* sales_multilevel.csv
* summary_store.csv
* summary_quarter.csv

---

# **📚 LESSON 10 — Window Functions & Rolling Analytics**

### **Dataset:** `company_sales.csv`

### **Learning Outcomes**

* Cumulative sums, max, min
* Rolling averages
* Expanding windows
* Ranking
* Lag/lead analysis

### **Tasks**

1. Calculate cumulative revenue.
2. 3-month moving average.
3. MoM growth and percent growth.
4. Ranking revenue by store.

### **Mini-Project 10 — Executive Financial Dashboard**

Export:

* financial_window_analysis.csv
* growth_analysis.csv
* store_summary.csv

---

# **📘 FINAL CAPSTONE PROJECT (Optional)**

*(Tell me if you want this!)*

A full project integrating:
✔ joins
✔ aggregations
✔ time-series
✔ pivoting
✔ MultiIndex
✔ window analytics
