# 📈 Stock Price Prediction Using Machine Learning

## 📄 Assignment Context

This project is developed as part of the **Futures First Internship Assignment**.  
All steps, assumptions, and methodologies strictly follow the problem statement and guidelines provided in the assignment PDF.

---

## 📌 Problem Statement

You are provided with two datasets:

- **Data Dataset** – Independent variable  
- **StockPrice Dataset** – Dependent variable (stock prices)

The task is to build a **Python-based machine learning model** to predict stock prices using values from the Data dataset.

---

## 🧠 Key Assumptions (As Given in PDF)

1. **Primary Influence**  
   Stock price movement is primarily influenced by the **change in data from the previous day**.

2. **Other Factors Ignored**  
   Although many real-world variables influence stock prices, **all other factors are ignored** for the purpose of this assignment.

These assumptions were strictly respected throughout the project.

---

## 🎯 Project Objectives

- Load and preprocess the given datasets
- Engineer features capturing **day-over-day changes**
- Normalize features where required
- Train machine learning models to predict stock prices
- Evaluate model performance using suitable metrics
- Interpret results using visualizations
- Compare linear and non-linear models
- Provide reusable prediction functions

---

## 🧠 Overall Workflow

The project follows a complete **end-to-end machine learning pipeline**:

1. Data loading  
2. Date handling and merging  
3. Missing value analysis  
4. Feature engineering  
5. Feature scaling  
6. Exploratory data analysis (EDA)  
7. Train-test split  
8. Model training  
9. Model evaluation  
10. Visualization  
11. Prediction on new data  
12. Model comparison  

---

## 🧹 Data Preprocessing

### 1️⃣ Data Loading
- Loaded datasets using **Pandas**
- Files used:
  - `Data1.csv`
  - `StockPrice.csv`

### 2️⃣ Date Handling
- Converted `Date` columns to `datetime` format
- Ensured consistent date alignment

### 3️⃣ Data Merging
- Merged datasets using an **inner join on Date**
- Ensured only common dates were retained
- Sorted merged dataset chronologically

### 4️⃣ Missing Value Check
- Checked missing values using `isnull().sum()`
- No missing values were found except those introduced during feature engineering

---

## 🏗 Feature Engineering

### Core Feature (Based on Assignment Assumption)


- Captures **day-over-day change**
- Directly reflects the assignment’s assumption
- First value filled with `0` to handle missing value from differencing

### Final Features Used
- `Data`
- `Data_Change`

---

## ⚖ Feature Scaling

- Applied **StandardScaler**
- Transformed features to:
  - Mean ≈ 0
  - Standard deviation ≈ 1
- Scaling ensures:
  - Faster convergence
  - Balanced feature contribution
  - Improved numerical stability

---

## 📊 Exploratory Data Analysis (EDA)

### Feature Distributions (Before Scaling)
- Histogram + KDE plots for:
  - `Data`
  - `Data_Change`
- Revealed scale imbalance between features

### Feature Distributions (After Scaling)
- Confirmed normalization
- Both features centered around zero
- Comparable spread across features

---

## 🔀 Train-Test Split

- Data split into:
  - **80% Training**
  - **20% Testing**
- Used `random_state=42` for reproducibility
- Ensured fair evaluation on unseen data

---

## 🤖 Machine Learning Models

### 🔹 Model 1: Linear Regression (Baseline)

- Simple and interpretable
- Assumes linear relationship between features and stock price
- Used as a benchmark model

#### Evaluation Metrics
- Mean Squared Error (MSE)
- R-squared (R²)

---

### 🔹 Model 2: RandomForestRegressor (Advanced Model)

- Ensemble-based model using multiple decision trees
- Captures **non-linear relationships**
- More robust to volatility and noise

#### Why Random Forest?
- Financial data is often non-linear
- Handles interactions automatically
- Reduces overfitting via averaging

---

## 📊 Model Evaluation

### Metrics Used
- **Mean Squared Error (MSE)**
- **R-squared (R²)**

### Results
- Linear Regression provided a strong baseline
- **Random Forest achieved lower MSE and higher R²**
- Indicates superior predictive capability

---

## 📈 Visualization & Interpretation

### 1️⃣ Time-Series Plots
- Actual vs Predicted prices for:
  - Linear Regression
  - Random Forest
- Used to observe trend-following behavior

### 2️⃣ Scatter Plots
- Actual vs Predicted (with perfect prediction line)
- Used to:
  - Detect bias
  - Analyze error spread

### 3️⃣ Combined Model Comparison Plot
- Actual prices vs:
  - Linear Regression predictions
  - Random Forest predictions
- Clearly shows Random Forest tracks actual prices more closely

---

## 🔮 Prediction & Deployment

### Prediction Functions Implemented

#### Linear Regression
```python
predict_stock_price(data, data_change)
