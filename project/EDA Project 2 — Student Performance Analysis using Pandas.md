## **EDA Project 2 — Student Performance Analysis using Pandas**

### **Project Title**

🎓 **Exploratory Data Analysis of Student Academic Performance**

---

### **Objective**

To analyze student data and understand:

* Factors affecting academic performance
* Relationship between study time and scores
* Gender-wise and subject-wise performance
* Impact of attendance and parental background

---

### **Dataset**

**Name:** Student Performance Dataset
**Format:** CSV

**Typical Columns:**

* `StudentID`
* `Gender`
* `Age`
* `MathScore`
* `ReadingScore`
* `WritingScore`
* `StudyHours`
* `Attendance`
* `ParentalEducation`
* `FinalResult`

You can use:

* Kaggle: *Students Performance in Exams*
* Or generate dummy data for practice

---

### **Key Questions (EDA Goals)**

1. What is the average score per subject?
2. Do students with higher study hours perform better?
3. Is attendance correlated with performance?
4. Are there gender-based differences?
5. Which factors most influence final results?

---

### **Step 1: Load Libraries & Data**

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv("student_performance.csv")
df.head()
```

---

### **Step 2: Initial Exploration**

```python
df.info()
df.describe()
df.isnull().sum()
```

---

### **Step 3: Data Cleaning**

```python
df.dropna(inplace=True)

df['AverageScore'] = (
    df['MathScore'] +
    df['ReadingScore'] +
    df['WritingScore']
) / 3
```

---

### **Step 4: Subject-wise Performance**

```python
df[['MathScore','ReadingScore','WritingScore']].mean()
```

---

### **Step 5: Gender-wise Analysis**

```python
df.groupby('Gender')['AverageScore'].mean()
```

```python
sns.boxplot(x='Gender', y='AverageScore', data=df)
plt.title("Gender vs Average Score")
plt.show()
```

---

### **Step 6: Study Hours vs Performance**

```python
sns.scatterplot(x='StudyHours', y='AverageScore', data=df)
plt.title("Study Hours vs Performance")
plt.show()
```

---

### **Step 7: Attendance Impact**

```python
sns.regplot(x='Attendance', y='AverageScore', data=df)
plt.title("Attendance vs Performance")
plt.show()
```

---

### **Step 8: Parental Education Effect**

```python
df.groupby('ParentalEducation')['AverageScore'].mean().sort_values()
```

---

### **Insights You Can Derive**

* Strong positive correlation between study hours and scores
* Attendance directly affects academic outcomes
* Socio-educational background matters
* Performance gaps across subjects

---

### **Skills Demonstrated**

✅ Data aggregation
✅ Feature engineering
✅ Correlation analysis
✅ Educational insights
✅ Visualization with Seaborn

---
