# 🧠 Stroke Data Analysis and Visualization

## 📌 Project Overview

**Stroke Data Analysis and Visualization** is a Python-based data analysis project developed as a college mini project. The main purpose of this project is to analyze a healthcare dataset and understand the relationship between different demographic, medical, and lifestyle factors and the occurrence of stroke.

The project uses **Python, Pandas, NumPy, and Matplotlib** to perform data loading, data cleaning, exploratory data analysis (EDA), statistical analysis, filtering, grouping, and data visualization.

The dataset contains **5,110 records and 12 columns** related to patient information such as age, gender, hypertension, heart disease, average glucose level, BMI, smoking status, work type, residence type, and stroke status.

> **Note:** This project is an educational data-analysis project. It does not provide medical diagnosis or clinical predictions.

---

## 🎯 Objectives

The main objectives of this project are:

* To understand and analyze a healthcare dataset.
* To inspect the structure and characteristics of the dataset.
* To identify missing values and handle them appropriately.
* To check for duplicate records.
* To perform descriptive statistical analysis.
* To study demographic characteristics such as age and gender.
* To analyze health-related factors such as hypertension and heart disease.
* To study average glucose levels and BMI.
* To analyze smoking status and residence type.
* To compare characteristics of patients with and without stroke.
* To filter and sort data according to different conditions.
* To represent important findings using data visualizations.
* To gain practical experience with Python-based data analysis.

---

## 🛠️ Technologies Used

| Technology       | Purpose                                        |
| ---------------- | ---------------------------------------------- |
| Python           | Main programming language                      |
| Pandas           | Data loading, cleaning, filtering and analysis |
| NumPy            | Numerical operations                           |
| Matplotlib       | Data visualization                             |
| Jupyter Notebook | Development and execution environment          |
| GitHub           | Project hosting and version control            |

---

## 📂 Project Structure

```text
Stroke-Data-Analysis/
│
├── stroke-analysis.ipynb
├── health.csv
├── README.md
```

### File Description

**`stroke-analysis.ipynb`**
Contains the complete Python code, analysis, calculations, filtering operations, and visualizations.

**`health.csv`**
Contains the healthcare dataset used for the analysis.

**`README.md`**
Provides project documentation, objectives, methodology, results, and instructions.

---

# 📊 Dataset Description

The dataset used in this project contains **5,110 rows and 12 columns**.

### Dataset Columns

| Column              | Description                                       |
| ------------------- | ------------------------------------------------- |
| `id`                | Unique identifier for each record                 |
| `gender`            | Gender of the individual                          |
| `age`               | Age of the individual                             |
| `hypertension`      | Indicates whether hypertension is present         |
| `heart_disease`     | Indicates whether heart disease is present        |
| `ever_married`      | Indicates whether the individual has been married |
| `work_type`         | Type of employment/work                           |
| `Residence_type`    | Urban or Rural residence                          |
| `avg_glucose_level` | Average glucose level                             |
| `bmi`               | Body Mass Index                                   |
| `smoking_status`    | Smoking category                                  |
| `stroke`            | Stroke outcome indicator                          |

The notebook shows that the dataset contains **5,110 records**, with `bmi` being the only column containing missing values initially, with **201 missing entries**.

---

# 🔍 Data Analysis Process

The project follows a basic data-analysis workflow.

### 1. Importing Libraries

The project imports:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

These libraries are used for data manipulation, numerical operations, and visualization.

---

### 2. Loading the Dataset

The dataset is loaded using Pandas:

```python
df = pd.read_csv("health.csv")
```

---

### 3. Understanding the Dataset

The project examines:

* First few records
* Last few records
* Number of rows and columns
* Column names
* Data types
* Statistical summary

The dataset shape is:

```text
5110 rows × 12 columns
```

The notebook also uses:

```python
df.head()
df.tail()
df.shape
df.columns
df.dtypes
df.info()
df.describe()
```

---

# 🧹 Data Cleaning

Data cleaning is an important part of this project.

## Missing Values

The notebook checks missing values using:

```python
df.isnull().sum()
```

The result shows **201 missing values in the BMI column**.

The missing BMI values are handled using the median:

```python
df['bmi'] = df['bmi'].fillna(df['bmi'].median())
```

This allows the analysis to continue without removing the records containing missing BMI values.

---

## Duplicate Records

Duplicate records are checked using:

```python
df.duplicated().sum()
```

The notebook shows **0 duplicate records**.

---

# 📈 Exploratory Data Analysis

Several analytical operations are performed in the project.

### Gender Analysis

The gender distribution is analyzed using:

```python
df['gender'].value_counts()
```

The dataset contains:

* Female: 2,994
* Male: 2,115
* Other: 1

---

### Smoking Status Analysis

Smoking categories are analyzed using:

```python
df['smoking_status'].value_counts()
```

The dataset contains:

* Never smoked: 1,892
* Unknown: 1,544
* Formerly smoked: 885
* Smokes: 789

---

### Age Analysis

The project calculates the average age:

```python
df['age'].mean()
```

The average age is approximately **43.23 years**.

The minimum age is approximately **0.08 years**, while the maximum age is **82 years**.

---

### Average Glucose Level

The average glucose level is calculated using:

```python
df['avg_glucose_level'].mean()
```

The average is approximately **106.15**.

---

### Heart Disease Analysis

Heart disease records are analyzed using:

```python
df['heart_disease'].value_counts()
```

The dataset contains:

* No heart disease: 4,834
* Heart disease: 276

---

# 🧠 Stroke Analysis

The project analyzes the relationship between stroke and different variables.

### Average Age by Stroke Status

```python
df.groupby('stroke')['age'].mean()
```

The analysis shows:

| Stroke | Average Age |
| ------ | ----------: |
| 0      |       41.97 |
| 1      |       67.73 |

This indicates that the average age in the records with `stroke = 1` is higher than in records with `stroke = 0`.

---

### Average Glucose Level by Stroke Status

```python
df.groupby('stroke')['avg_glucose_level'].mean()
```

| Stroke | Average Glucose Level |
| ------ | --------------------: |
| 0      |                104.80 |
| 1      |                132.54 |

The analysis shows a higher average glucose level among records where the stroke indicator is 1.

---

### Stroke Records

Stroke cases can be filtered using:

```python
df[df['stroke'] == 1]
```

The notebook shows **249 records with `stroke = 1`**.

---

# 🔎 Data Filtering

The project performs filtering using different conditions.

### People Above 50 Years

```python
df[df['age'] > 50]
```

This produces **2,127 records**.

### Stroke Cases

```python
df[df['stroke'] == 1]
```

### People with Hypertension

```python
df[df['hypertension'] == 1]
```

This produces **498 records**.

### People with High Average Glucose Level

```python
df[df['avg_glucose_level'] > 150]
```

This produces **730 records**.

---

# 📊 Sorting and Grouping

The project uses sorting and grouping operations to understand patterns in the data.

### Sorting by Age

```python
df.sort_values('age', ascending=False)
```

### Residence Type

```python
df['Residence_type'].value_counts()
```

The dataset contains:

* Urban: 2,596
* Rural: 2,514

### Marital Status

```python
df['ever_married'].value_counts()
```

The dataset contains:

* Yes: 3,353
* No: 1,757

---

# 📉 Data Visualization

Matplotlib is used to visually represent the results of the analysis.

The project includes graphical analysis such as:

* Bar charts
* Distribution/count visualizations
* Comparisons between groups
* Graphs based on gender and age
* Graphical representation of analytical results

For example, the notebook creates a bar chart showing **Average Age by Gender** using grouped data.

Example:

```python
age_data = df.groupby("gender")["age"].mean().sort_values(ascending=False)

plt.figure(figsize=(10,6))

age_data.plot(
    kind="bar",
    color=["navy", "orange", "green"]
)

plt.title("Average Age by Gender")
plt.xlabel("Gender")
plt.ylabel("Average Age")

plt.show()
```

---

# 📌 Key Findings

Based on the analysis performed in the notebook:

1. The dataset contains **5,110 records and 12 columns**.
2. There were **201 missing BMI values**, which were handled using the BMI median.
3. No duplicate records were found.
4. Female records are more numerous than male records in the dataset.
5. `never smoked` is the largest known smoking-status category.
6. The average age of the dataset is approximately **43.23 years**.
7. The average glucose level is approximately **106.15**.
8. Records with `stroke = 1` have a higher average age than records with `stroke = 0`.
9. Records with `stroke = 1` also have a higher average glucose level in this dataset.
10. The dataset contains **249 stroke-positive records** according to the filtering operation.

> These findings describe patterns in this dataset only and should not be interpreted as medical conclusions.

---

# ⚙️ Methodology

The project follows these steps:

```text
Dataset
   ↓
Data Loading
   ↓
Data Understanding
   ↓
Data Cleaning
   ↓
Missing Value Handling
   ↓
Duplicate Checking
   ↓
Descriptive Statistics
   ↓
Data Filtering
   ↓
Grouping & Sorting
   ↓
Exploratory Data Analysis
   ↓
Data Visualization
   ↓
Findings & Conclusions
```

---

# 💻 Installation and Setup

## Step 1: Install Python

Install Python 3.x on your computer.

## Step 2: Install Required Libraries

Open Command Prompt or Terminal and run:

```bash
pip install pandas numpy matplotlib jupyter
```

## Step 3: Clone the Repository

```bash
git clone https://github.com/your-username/your-repository-name.git
```

## Step 4: Open the Project Folder

```bash
cd your-repository-name
```

## Step 5: Start Jupyter Notebook

```bash
jupyter notebook
```

## Step 6: Open the Notebook

Open:

```text
stroke-analysis.ipynb
```

Make sure `health.csv` is present in the same folder as the notebook.

---

# ▶️ How to Run the Project

1. Download or clone the repository.
2. Make sure Python is installed.
3. Install the required libraries.
4. Keep `health.csv` in the project directory.
5. Open `stroke-analysis.ipynb` in Jupyter Notebook.
6. Run the cells from top to bottom.
7. Observe the analysis outputs and visualizations.

---

# 🎓 College Project Information

### Project Title

**Stroke Data Analysis and Visualization**

### Project Type

**College Mini Project**

### Tools

**Jupyter Notebook and GitHub**

### Libraries

**Pandas, NumPy, Matplotlib**

### Main Concepts

* Data Analysis
* Data Cleaning
* Exploratory Data Analysis
* Statistical Analysis
* Data Filtering
* Data Grouping
* Data Sorting
* Data Visualization

---

# 📚 Learning Outcomes

Through this project, the following skills are developed:

* Understanding real-world datasets
* Working with CSV files
* Using Pandas DataFrames
* Handling missing data
* Checking duplicate records
* Performing statistical analysis
* Applying filtering conditions
* Using `groupby()`
* Sorting DataFrames
* Creating charts using Matplotlib
* Interpreting analytical results
* Documenting a data-analysis project
* Managing a project using GitHub

---

# 🏆 Conclusion

This project demonstrates how Python can be used to analyze healthcare data and discover useful patterns through data cleaning, statistical analysis, filtering, grouping, and visualization.

The analysis shows differences in variables such as **age and average glucose level** between records with and without a stroke indicator. The project also demonstrates practical techniques for handling missing values, checking duplicates, exploring categorical variables, and presenting results graphically.

Overall, the project provides practical experience in the complete basic workflow of **data analysis using Python** and can serve as a foundation for more advanced healthcare analytics and machine-learning projects.

---

# 👨‍💻 Project Author

**Name:** Ayush Chavan

**Project:** Stroke Data Analysis and Visualization

**Academic Project:** College Mini Project

---

# 📜 Disclaimer

This project is created for **educational and academic purposes only**.

The analysis presented in this repository is based on the provided dataset and should not be considered medical advice, diagnosis, or a clinical decision-making system.

---

# ⭐ Acknowledgement

I would like to thank my faculty members and institution for providing guidance and support during the development of this project.

I also acknowledge the use of Python and its open-source data-analysis libraries, which made the analysis and visualization possible.

---

## 📎 Project Files

* `stroke-analysis.ipynb` — Main Jupyter Notebook
* `health.csv` — Dataset
* `README.md` — Project documentation

---

## ⭐ If You Find This Project Useful

If this project helped you understand data analysis, you can **star ⭐ the repository** on GitHub.
