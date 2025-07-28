 Student Grades Analysis using Python

A beginner-friendly data analysis project in Python that explores student performance across subjects using the Kaggle dataset. This project was developed using Google Colab and covers loading, cleaning, analyzing, and visualizing educational data.

---
 Dataset Information

- *Source*: [Kaggle - Students Performance in Exams](https://www.kaggle.com/datasets/spscientist/students-performance-in-exams)
- *File Used*: StudentsPerformance.csv
- The dataset contains 1000 records of students with features like gender, parental education, lunch type, test preparation, and scores in Math, Reading, and Writing.

---

 Tools & Libraries

| Tool | Description |
|------|-------------|
| Google Colab | Cloud-based Python IDE |
| Pandas | Data manipulation |
| Matplotlib | Data visualization |
| Seaborn | (Optional) Advanced visualization |
| SQLite + Colab SQL Magic | (Optional) SQL-based queries |

---

 Project Workflow

 ### 1. Load Dataset
```python
import pandas as pd
df = pd.read_csv('/content/StudentsPerformance.csv')
df.head()

### 2.
print(df.shape)
df.info()
df.describe()

### 3.
df.columns = [col.strip().lower().replace(' ', '_') for col in df.columns]
df.head()

### 4.
import matplotlib.pyplot as plt

df['math_score'].hist(bins=10)
plt.title('Math Score Distribution')
plt.xlabel('Score')
plt.ylabel('Number of Students')
plt.grid(True)
plt.show()


### 5.
df['total_score'] = df['math_score'] + df['reading_score'] + df['writing_score']

top_student = df[df['total_score'] == df['total_score'].max()]
high_achievers = df[
    (df['math_score'] > 90) & 
    (df['reading_score'] > 90) & 
    (df['writing_score'] > 90)
]
