# 🚗 Used Cars Price Prediction App  

##  Overview  

This project aims to **predict the prices of used cars** based on their specifications such as engine size, mileage, power, and brand using **machine learning regression models**.  
The workflow includes **data cleaning**, **feature engineering**, **EDA**, **model building**, **optimization**, and **deployment preparation**.

---

##  Tech Stack  

| Category | Libraries |
|-----------|------------|
| **Data Handling** | `pandas`, `numpy` |
| **Visualization** | `matplotlib`, `seaborn` |
| **Machine Learning** | `scikit-learn`, `category_encoders` |
| **Model Saving** | `pickle` |
| **Warnings Control** | `warnings` |

---

## 📂 Dataset  

**File Used:** `train-data.csv`

| Feature | Description |
|----------|--------------|
| `Name` | Full name of the car (Brand + Model) |
| `Year` | Year of manufacture |
| `Kilometers_Driven` | Distance driven in kilometers |
| `Fuel_Type` | Type of fuel used (Petrol/Diesel/CNG) |
| `Transmission` | Type of transmission (Manual/Automatic) |
| `Owner_Type` | Number of previous owners |
| `Mileage`, `Engine`, `Power`, `Seats` | Car specifications |
| `Price` | Selling price of the car (Target variable) |

---

##  Data Cleaning  

1. **Removed unnecessary columns:** `Unnamed: 0`, `New_Price`  
2. **Feature Engineering:**
   - Extracted `Brand` and `Model` from `Name`
   - Created new feature: `Age = 2020 - Year`
3. **Data Type Fixing:**
   - Converted `Power`, `Engine`, `Mileage` to numeric  
   - Standardized units (`km/kg` → converted to `kmpl`)
4. **Handling Missing Values:**
   - Numerical: median imputation  
   - Categorical: mode imputation  
5. **Removed Duplicates and Invalid Records**
   - Dropped rows with `Seats == 0` or unrealistic `Kilometers_Driven`  
6. **Outlier Treatment:**
   - Applied **IQR method** to cap extreme values  

---

##  Exploratory Data Analysis (EDA)  

### 🔹 Univariate Analysis  
- KDE plots for numerical variables  
- Count plots for categorical variables (Fuel Type, Transmission, Owner Type)

### 🔹 Bivariate Analysis  
- Scatter plots showing relationships between features and `Price`  
- Correlation heatmap to detect multicollinearity

### 🔹 Key Insights  

| Observation | Insight |
|--------------|----------|
| Older cars have lower prices | Age inversely correlates with price |
| Higher engine power increases price | Positive correlation between power and price |
| Transmission impacts price | Automatics are generally priced higher |
| Mileage affects depreciation | More mileage → lower price |

---

##  Data Preprocessing  

Pipelines were built for each feature type using **ColumnTransformer**.

| Type | Method |
|------|--------|
| **Numeric** | Median Imputation → StandardScaler |
| **Ordinal** | Mode Imputation → OrdinalEncoder |
| **Nominal** | Mode Imputation → OneHotEncoder |
| **High Cardinality (Model)** | Mode Imputation → BinaryEncoder |

---

##  Model Building  

Tested Models:
- **Linear Regression**
- **Ridge Regression**
- **Lasso Regression**

###  Evaluation Metrics  

| Model | R² Score | MSE |
|--------|-----------|-----|
| Linear Regression | 0.84 | 0.032 |
| Ridge Regression | 0.86 | 0.028 |
| Lasso Regression | 0.83 | 0.035 |

---

## 🔍 Model Optimization  

Performed **GridSearchCV** with **PolynomialFeatures** and **Ridge Regularization**.  

**Best Parameters:**


##Key Takeaways

Proper feature engineering drastically improves performance.

Polynomial + Ridge regularization yielded the best balance between bias and variance.

Handling outliers and transforming skewed target (log(Price)) stabilized model training.

Binary encoding was effective for high-cardinality features like Model.


# Future Enhancements

Develop a Streamlit/Flask web app for interactive price prediction

Integrate SHAP or LIME for model explainability

Deploy model on AWS, Azure, or Hugging Face Spaces

Add feature selection or PCA for dimensionality reduction

## 👨‍💻 Author

Developed by: [Rahma Saber Abbas]
 Date: October 31, 2025
 File: Used_Car_Price_Prediction.py

