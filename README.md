# Calories Burn Prediction — EDA & Machine Learning

<p align="center">
  <b>Exploratory Data Analysis • Data Preprocessing • Visualization • XGBoost Regression</b>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white">
  <img src="https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=for-the-badge&logo=pandas&logoColor=white">
  <img src="https://img.shields.io/badge/Seaborn-Visualization-0B5A6F?style=for-the-badge">
  <img src="https://img.shields.io/badge/Scikit--learn-ML-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white">
  <img src="https://img.shields.io/badge/XGBoost-Regression-189F3B?style=for-the-badge">
</p>

##  Overview📌

This project analyzes exercise-related data and builds a **machine learning regression model to predict calories burned** during exercise.

The workflow covers the complete pipeline:

**Data Collection → Data Merging → Data Cleaning → EDA → Outlier Handling → Encoding → Correlation Analysis → Scaling → Model Training → Evaluation**

The analysis uses two datasets, `exercise.csv` and `calories.csv`, which are merged using `User_ID`.

##  Dataset📂

### Exercise Dataset
Contains **15,000 records and 8 columns**:

| Feature | Description |
|---|---|
| `User_ID` | Unique user identifier |
| `Gender` | User gender |
| `Age` | User age |
| `Height` | Height |
| `Weight` | Weight |
| `Duration` | Exercise duration |
| `Heart_Rate` | Heart rate during exercise |
| `Body_Temp` | Body temperature |

### Calories Dataset

Contains **15,000 records and 2 columns**:

| Feature | Description |
|---|---|
| `User_ID` | Unique user identifier |
| `Calories` | Calories burned |

The two datasets are combined using an **inner merge on `User_ID`**, producing a dataset of **15,000 rows and 9 columns**.

##  Data Quality & Preprocessing🔍

The dataset contains:

- **15,000 observations**
- **9 columns after merging**
- No missing values
- No duplicate rows
- Numerical and categorical features

`User_ID` is removed after merging because it is an identifier rather than a predictive feature.

Categorical encoding is performed using one-hot encoding, resulting in the `Gender_male` feature.

##  Exploratory Data Analysis📊

### Univariate Analysis

The project explores the individual distributions of:

- Gender
- Age
- Height
- Weight
- Exercise Duration
- Heart Rate
- Body Temperature

Histograms with KDE and categorical count plots are used to understand feature distributions.

### Outlier Analysis

Boxplots are used to inspect numerical variables, followed by an IQR-based outlier-removal procedure.

The numerical variables considered include:

`Age`, `Height`, `Weight`, `Duration`, `Heart_Rate`, and `Body_Temp`.

### Bivariate Analysis

Relationships with the target variable are visualized using scatter plots:

- Duration vs Calories
- Heart Rate vs Calories
- Body Temperature vs Calories

### Multivariate Analysis

The project uses:

- One-hot encoding
- Correlation matrix
- Correlation heatmap

to examine relationships among the model features and target.

## Machine Learning

### Target

```text
Calories
```

### Features

```text
Age
Height
Weight
Duration
Heart_Rate
Body_Temp
Gender_male
```

### Train-Test Split

The data is split into:

- **80% training data**
- **20% testing data**
- `random_state=22`

### Feature Scaling

`StandardScaler` is applied to the feature data before model training.

### Model

The project uses:

**XGBoost Regressor (`XGBRegressor`)**

```python
from xgboost import XGBRegressor

xgb = XGBRegressor()
xgb.fit(x_train_scaled, y_train)
```

## Model Performance📈

The trained XGBoost regression model achieved:

| Metric | Score |
|---|---:|
| **MAE** | **5.30** |
| **R² Score** | **0.9744** |

An R² score of approximately **0.974** indicates that the trained model explains a large proportion of the variation in the target values within the evaluated test set.

## Tech Stack🛠️ 

- **Python**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **Seaborn**
- **Scikit-learn**
- **XGBoost**
- **Jupyter Notebook**

## Project Structure📁 

```text
Calories-Prediction/
│
├── exercise.csv
├── calories.csv
├── Calories_pred.ipynb
└── README.md
```


## Workflow

```text
exercise.csv ─────┐
                  ├──► Merge on User_ID
calories.csv ─────┘
                         │
                         ▼
                  Data Quality Check
                         │
                         ▼
                    Remove User_ID
                         │
                         ▼
                         EDA
                         │
          ┌──────────────┼──────────────┐
          ▼              ▼              ▼
      Univariate     Outlier        Bivariate
       Analysis      Analysis        Analysis
          └──────────────┼──────────────┘
                         ▼
                  One-Hot Encoding
                         │
                         ▼
                  Correlation Analysis
                         │
                         ▼
                  Train / Test Split
                         │
                         ▼
                    StandardScaler
                         │
                         ▼
                   XGBRegressor
                         │
                         ▼
                  Model Evaluation
                         │
                  ┌──────┴──────┐
                  ▼             ▼
                 MAE           R²
                5.30         0.9744
```

## Key Takeaways

- The exercise and calories datasets can be integrated through `User_ID`.
- The merged dataset contains 15,000 observations with no missing or duplicate rows.
- Exercise-related variables are explored through multiple visualization techniques.
- Outlier analysis is performed using the IQR method.
- Categorical data is transformed using one-hot encoding.
- XGBoost is used as the final regression model.
- The evaluated model achieves an **MAE of 5.30** and an **R² score of 0.9744**.

## Future Improvements

- Add hyperparameter tuning for XGBoost.
- Compare XGBoost with Linear Regression, Random Forest, and other regression models.
- Add feature importance analysis.
- Build an interactive Streamlit prediction application.
- Save the trained model and scaler for deployment.
- Add prediction visualizations and a dedicated model evaluation dashboard.

##  Author

**Madhu Shrivastava**

If this project helped you, consider giving the repository a ⭐.
