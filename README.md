# 🌸 Machine_learning_EDA_iris

This repository contains an exploratory data analysis (EDA) and basic preprocessing workflow on the **Iris dataset** — a classic dataset widely used in data science and machine learning education.  
The notebook `iris_raw.ipynb` demonstrates step-by-step data handling, cleaning, visualization, and interpretation of relationships among Iris flower features.

---

## 📘 Project Overview

The main goal of this notebook is to:
- Explore the **structure and quality** of the Iris dataset.
- Perform **data cleaning** (null handling and outlier checks).
- Visualize **feature distributions** and **relationships**.
- Derive **statistical insights** from numerical summaries and plots.

---

## 🧾 Dataset Summary

- **Dataset Name:** `iris_raw.csv`  
- **Rows (observations):** 120  
- **Columns (features):** 5  
  - Four numeric features (float type)
  - One categorical feature (string type, species/class)

| Feature | Description |
|----------|--------------|
| SepalLength | Length of the sepal (cm) |
| SepalWidth  | Width of the sepal (cm) |
| PetalLength | Length of the petal (cm) |
| PetalWidth  | Width of the petal (cm) |
| Species     | Class label (`setosa`, `versicolor`, `virginica`) |

---

## 🧹 Data Cleaning Steps

1. **Checking null values** using:
   ```python
   df.isna().sum()
   ```
2. **Identifying null rows**
   Missing values were found in `SepalWidth` column (indices `[2, 13, 33, 44, 59, 71, 76, 95]`).

3. **Handling missing data**  
   Instead of dropping rows, the mean of `SepalWidth` was used for imputation:
   ```python
   df['SepalWidth'] = df['SepalWidth'].fillna(df['SepalWidth'].mean())
   ```
   **Reason:** the column is continuous and of type float.

4. **Confirming missing values handled:**
   ```python
   df.isna().sum()
   ```

---

## 📊 Exploratory Data Analysis (EDA)

### 1. Feature Distributions
Histograms were plotted for each numeric feature to check data spread, skewness, and variation:
```python
sns.histplot(df[col], kde=True, alpha=0.3, color='skyblue')
```
**Observations:**
- `PetalWidth` shows more relative variation (high coefficient of variation).
- `SepalLength` and `SepalWidth` are more clustered around the mean.
- All features show near-zero skewness → fairly symmetric distributions.

### 2. Species Distribution
- `Virginica` species has the highest count.
- `Setosa` and `Versicolor` appear in roughly equal proportions.

### 3. Outlier Detection
- Checked visually using histograms.
- No significant outliers were detected in the dataset.

### 4. Correlation Analysis
Used `df.corr()` to check relationships among features.

**Key insights:**
- `PetalLength` and `PetalWidth` are strongly positively correlated (linear relation).
- `SepalWidth` and `PetalLength` show slight negative correlation.
- Larger flower size tends to correspond with longer petals and sepals.

---

## 📈 Summary of Insights

| Aspect | Insight |
|--------|----------|
| Data Quality | Clean, minimal missing data handled using mean imputation |
| Skewness | All features roughly symmetric (no heavy skew) |
| Correlation | Strong positive correlation between PetalLength & PetalWidth |
| Outliers | None significant |
| Class Balance | Slightly higher count for Virginica |

---

## 📂 Project File Structure

```
Machine_learning_EDA_iris/
│
├── iris_raw.ipynb         # Main notebook for data cleaning & EDA
├── iris_raw.csv           # Dataset file used in notebook
├── disribution <feature>.png  # Saved plots for each numeric column
└── README.md              # Project documentation
```

---

## 🧠 Learning Notes

This notebook is excellent for beginners to understand:
- How to inspect and clean real datasets.
- When and how to handle missing data.
- The importance of understanding data variation and correlation before modeling.

**You can extend this project by:**
- Adding pairplots, boxplots, and correlation heatmaps.
- Applying PCA or clustering to observe separability.
- Building simple classification models (Logistic Regression, KNN, Decision Tree).

---

## 👤 Author
**Created by:** Anuj Kumar Thakur

---

## 🪪 License
This project is open for educational use and learning reference.
