# VOIS Major Project

# 🌾 Seasonal Agriculture Performance Analysis

An Exploratory Data Analysis and Statistical Analysis project that investigates agricultural performance across **Kharif, Rabi, and Zaid seasons** using productivity, economic, environmental, resource-usage, and disease/pest-risk indicators.

---

## 📌 Project Overview

Agricultural performance can vary across seasons due to differences in environmental conditions, farming practices, resource usage, crop types, and production costs.

This project analyzes a **Seasonal Agriculture Performance Dataset** to identify patterns and differences in agricultural performance across **Kharif, Rabi, and Zaid** seasons.

The analysis focuses on:

* Crop yield and production
* Revenue, cost, and profit
* Profit margin and cost per tonne
* Rainfall, temperature, humidity, and soil conditions
* Water, fertilizer, pesticide, and seed quality
* Disease and pest risk
* Relationships between agricultural resources and outcomes
* Seasonal differences using statistical tests
* Outlier and correlation analysis

The overall goal is to transform raw agricultural data into meaningful, data-driven insights.

---

## 🎯 Objectives

The major objectives of this project are:

1. Understand the structure and quality of the agricultural dataset.
2. Clean and prepare the data for analysis.
3. Explore agricultural performance across different seasons.
4. Perform descriptive and statistical analysis.
5. Investigate relationships between environmental, resource, and performance variables.
6. Compare agricultural outcomes across seasons, crops, and locations.
7. Identify unusual observations and outliers.
8. Develop evidence-based insights and recommendations.

---

## 📊 Dataset

**Dataset:** Seasonal Agriculture Performance Dataset

**File:** `seasonal_agriculture_performance_dataset.csv`

The dataset contains farm-level agricultural records covering:

* Season
* Crop
* State and District
* Environmental conditions
* Farming practices
* Irrigation
* Fertilizer and pesticide usage
* Seed quality
* Nutrient variables
* Water usage
* Production
* Revenue
* Total cost
* Profit
* Disease/Pest risk
* Crop yield

The analysis considers **Kharif, Rabi, and Zaid** as the major seasonal categories.

---

## 🛠️ Technologies & Libraries

The project was developed using Python and the following libraries:

* **Python**
* **Pandas** – Data manipulation and analysis
* **NumPy** – Numerical computations
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical visualization
* **SciPy** – Statistical testing
* **Jupyter Notebook** – Development environment

### Import section used in the project

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from scipy import stats
from IPython.display import display
```

---

## 🔄 Project Workflow

```text
Raw Agricultural Dataset
          ↓
Data Understanding
          ↓
Data Quality Checking
          ↓
Missing Value & Duplicate Checking
          ↓
Data Cleaning
          ↓
Feature Engineering
          ↓
Descriptive Statistics
          ↓
Univariate Analysis
          ↓
Bivariate Analysis
          ↓
Multivariate Analysis
          ↓
Statistical Testing
          ↓
Seasonal Comparison
          ↓
Key Findings
          ↓
Recommendations
```

---

## 🧹 Data Preparation

The project begins with dataset loading and exploratory inspection.

The following checks were performed:

* Dataset shape
* Column names
* Data types
* First and last records
* Categorical values
* Missing values
* Duplicate records
* Invalid values
* Numerical statistics

The cleaned dataset is stored in the analysis dataframe:

```python
clean_df
```

---

## ⚙️ Feature Engineering

Two additional variables were created to provide better measures of economic performance.

### 1. Profit Margin

Profit margin was calculated as:

```text
Profit Margin (%) =
(Profit / Revenue) × 100
```

Python implementation:

```python
clean_df["Profit_Margin_pct"] = np.where(
    clean_df["Revenue_INR"] != 0,
    (clean_df["Profit_INR"] / clean_df["Revenue_INR"]) * 100,
    np.nan
)
```

### 2. Cost per Tonne

Cost efficiency was measured using:

```text
Cost per Tonne =
Total Cost / Production
```

Python implementation:

```python
clean_df["Cost_per_Tonne_INR"] = np.where(
    clean_df["Production_Tonnes"] != 0,
    clean_df["Total_Cost_INR"] /
    clean_df["Production_Tonnes"],
    np.nan
)
```

These engineered variables were subsequently used in the statistical and exploratory analysis.

---

## 📈 Exploratory Data Analysis

### 1. Univariate Analysis

Individual variables were examined using:

* Descriptive statistics
* Mean and median comparison
* Range
* IQR
* Distribution analysis
* Box plots

### 2. Bivariate Analysis

Relationships between important variables were explored using scatter plots.

Examples include:

* Rainfall vs Crop Yield
* Fertilizer Usage vs Crop Yield
* Production vs Profit
* Water Usage vs Crop Yield
* Cost per Tonne vs Profit

These analyses help identify associations between resources, production, and economic outcomes.

### 3. Multivariate Analysis

Multiple variables were considered together to investigate:

* Season, crop, and yield
* Crop and seasonal performance
* Environmental variables and agricultural outcomes
* Resource usage and performance
* State and seasonal profitability

---

## 📊 Statistical Analysis

Statistical testing was performed to compare agricultural performance across seasons.

### ANOVA

One-way ANOVA was applied to:

* Yield
* Profit

```python
anova_yield = stats.f_oneway(*groups_yield)
anova_profit = stats.f_oneway(*groups_profit)
```

### Kruskal-Wallis Test

The non-parametric Kruskal-Wallis test was also applied to:

* Yield
* Profit

```python
kw_yield = stats.kruskal(*groups_yield)
kw_profit = stats.kruskal(*groups_profit)
```

The project uses:

```text
p < 0.05
```

as the criterion for evidence of an overall statistically significant difference among seasons.

A statistically significant result indicates a difference among groups; it does **not** by itself establish causation or identify which specific pairs of seasons differ.

---

## 🔎 Outlier Analysis

Outliers were investigated using the **Interquartile Range (IQR)** method.

The method uses:

```text
IQR = Q3 − Q1

Lower Limit = Q1 − 1.5 × IQR

Upper Limit = Q3 + 1.5 × IQR
```

Outlier analysis was performed for important variables such as:

* Yield
* Production
* Profit
* Cost per Tonne
* Profit Margin

Outliers were treated as observations requiring investigation rather than being automatically removed, since extreme agricultural values may represent genuine observations.

---

## 🔥 Correlation Analysis

A correlation matrix was created to examine associations between environmental/resource variables and agricultural outcomes.

Variables included:

* Rainfall
* Temperature
* Humidity
* Soil conditions
* Nitrogen
* Phosphorus
* Potassium
* Fertilizer
* Pesticide
* Seed quality
* Water usage
* Disease/Pest risk
* Yield
* Production
* Revenue
* Profit

```python
corr = clean_df[
    env_cols + outcome_cols
].corr(numeric_only=True)
```

A heatmap was then used to visualize these correlations.

> **Note:** Correlation indicates association between variables and should not be interpreted as proof of a causal relationship.

---

## 🌱 Seasonal Comparison

The project compares the three agricultural seasons using multiple dimensions.

### Productivity

* Average Yield
* Average Production
* Water Efficiency

### Economic Performance

* Average Revenue
* Average Cost
* Average Profit

### Environmental & Risk Factors

* Average Rainfall
* Average Temperature
* Disease/Pest Risk

This multi-dimensional comparison avoids relying on a single performance indicator.

---

## 📊 Key Visualizations

The project contains several visualizations, including:

* 📊 Average Crop Yield by Season
* 💰 Average Profit by Season
* 🌧️ Rainfall vs Crop Yield
* 🌱 Fertilizer Usage vs Crop Yield
* 💧 Water Usage vs Crop Yield
* 📈 Production vs Farm Profit
* 💵 Cost per Tonne vs Profit
* 📦 Crop Yield Box Plot
* 📦 Farm Profit Box Plot
* 🔥 Correlation Heatmap
* 🌾 Crop–Season Yield Comparison
* 🌡️ Environmental and Performance Comparisons
* ⚠️ Disease/Pest Risk by Season

---

## 💡 Key Findings

The analysis indicates that agricultural performance differs across **Kharif, Rabi, and Zaid**.

The notebook dynamically identifies:

* Season with the highest average yield
* Season with the highest average profit
* Season with the highest average water efficiency
* Season with the highest average disease/pest risk

The analysis also shows that **crop type is an important factor when interpreting seasonal performance**, since different crops can have substantially different yield scales.

In the overall analysis, **Kharif shows the strongest performance profile**, while **Zaid requires closer investigation**, particularly from the perspective of yield, water efficiency, and economic performance.

These findings should be interpreted as associations within the dataset rather than as causal conclusions.

---

## 💼 Data-Driven Recommendations

Based on the findings, the project proposes:

### 1. Season-Specific Planning

Resource allocation and agricultural planning should consider seasonal performance rather than applying the same strategy across all seasons.

### 2. Investigate Zaid Performance

The lower performance observed for Zaid should be examined through factors such as yield, costs, water efficiency, and other available variables.

### 3. Improve Resource Efficiency

Water and fertilizer usage should be evaluated together with both productivity and profitability.

### 4. Crop-Specific Decision Making

Crops should be compared separately because their production and yield scales can vary substantially.

### 5. Disease and Pest Monitoring

Higher-risk seasons or regions can be prioritized for monitoring and preventive planning.

These recommendations are intended as data-driven areas for further investigation rather than direct causal prescriptions.

---

## ⚠️ Limitations

The analysis has several limitations:

* Seasonal comparisons can be influenced by the crop composition of each season.
* Correlation does not establish causation.
* Statistical tests indicate group differences but do not automatically explain their underlying causes.
* Outliers may represent genuine agricultural observations.
* The dataset may not contain all farm-level factors that influence agricultural performance.
* Additional real-world and longitudinal data would be useful for stronger conclusions.

Therefore, the results should be considered as **dataset-level analytical insights** rather than universal agricultural conclusions.

---

## 🚀 Future Scope

A future version of this project could extend the analysis into predictive analytics.

Potential directions include:

### Machine Learning for Yield Prediction

Predict:

```text
Yield = f(
    Season,
    Crop,
    Rainfall,
    Temperature,
    Soil Conditions,
    Water Usage,
    Fertilizer,
    Irrigation,
    Seed Quality,
    Disease/Pest Risk
)
```

### Profit Prediction

A regression model could also be developed to estimate farm profitability using production, resource usage, environmental conditions, and crop characteristics.

### Possible Future Models

* Linear Regression
* Decision Tree Regression
* Random Forest Regression
* Gradient Boosting
* Other suitable regression/ML techniques

---

## 📁 Project Structure

A suggested GitHub repository structure is:

```text
Seasonal-Agriculture-Performance-Analysis/
│
├── data/
│   └── seasonal_agriculture_performance_dataset.csv
│
├── notebooks/
│   └── Seasonal_Agriculture_Performance_Analysis.ipynb
│
├── images/
│   ├── yield_by_season.png
│   ├── profit_by_season.png
│   ├── correlation_heatmap.png
│   └── project_workflow.png
│
├── README.md
└── requirements.txt
```

If the dataset is too large or has redistribution restrictions, it can be omitted from the GitHub repository and the README can instead describe how to place the dataset locally.

---

## ▶️ How to Run the Project

### 1. Clone the repository

```bash
git clone <https://github.com/Coder-Pinku/VOIS_Major_Project_Seasonal_Agriculture_Performance_Analysis>
```

### 2. Open the project directory

```bash
cd Seasonal-Agriculture-Performance-Analysis
```

### 3. Install the required libraries

```bash
pip install pandas numpy matplotlib seaborn scipy jupyter
```

### 4. Start Jupyter Notebook

```bash
jupyter notebook
```

### 5. Open the analysis notebook

Open the `.ipynb` file and run the cells sequentially.

Make sure the dataset is available at the path expected by the notebook:

```text
seasonal_agriculture_performance_dataset.csv
```

---

## 📚 Main Analytical Concepts Used

This project demonstrates practical application of:

* Exploratory Data Analysis
* Data Cleaning
* Feature Engineering
* Descriptive Statistics
* GroupBy Analysis
* Data Visualization
* Correlation Analysis
* Outlier Detection
* ANOVA
* Kruskal-Wallis Test
* Seasonal Comparison
* Data-driven Recommendation

---

## 👩‍💻 Author

**Priyanka Dutta**

Master of Science, Data Science

This project was developed as an academic data analysis project to apply Python-based exploratory data analysis and statistical techniques to an agricultural dataset.

---

## ⭐ Project Takeaway

> **Agricultural performance should not be evaluated using yield alone. A more useful analysis considers productivity, profitability, resource efficiency, environmental conditions, crop characteristics, and agricultural risk together.**

---

## 📌 Disclaimer

This project is intended for **academic and analytical purposes**. The findings represent patterns observed within the analyzed dataset and should not be treated as direct agricultural, financial, or policy advice without additional validation using real-world data.

