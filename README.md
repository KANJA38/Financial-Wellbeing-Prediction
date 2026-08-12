# Predicting Financial Wellbeing of Kenyans 🇰🇪

## 📌 Project Overview

This project uses **Machine Learning and Statistical Analysis** to predict the financial wellbeing status of Kenyans.

The project analyses financial inclusion and socioeconomic data to understand the factors associated with changes in financial wellbeing and develops classification models capable of predicting whether an individual's financial status has:

- **Improved**
- **Stayed the same**
- **Worsened**

The analysis combines **Exploratory Data Analysis (EDA), Hypothesis Testing, Data Preprocessing, and Machine Learning Classification**.

---

## 🎯 Project Objectives

The main objectives of this project are to:

1. Explore the financial and socioeconomic characteristics of the dataset.
2. Identify relationships between demographic/financial variables and financial wellbeing.
3. Perform statistical hypothesis testing.
4. Clean and preprocess the dataset for machine learning.
5. Train different classification algorithms.
6. Evaluate and compare the performance of the models.
7. Identify a suitable model for predicting financial wellbeing status.

---

## 📊 Dataset

The project uses the **FinAccess 2024** dataset loaded from:

`finaccess2024_datasprint.xlsx`

The dataset contains **20,871 observations and 28 variables** before the cleaning and preprocessing stages.

### Main Variables

The dataset contains demographic, financial inclusion, socioeconomic and financial wellbeing variables including:

| Variable | Description |
|---|---|
| `county` | County of the respondent |
| `location_type` | Location classification |
| `sex` | Sex of the respondent |
| `age` | Age group |
| `household_size` | Number of people in the household |
| `education_level` | Highest education level |
| `marital_status` | Marital status |
| `monthly_income` | Monthly income |
| `savings_formal` | Formal savings participation |
| `savings_informal` | Informal savings participation |
| `loan_formal` | Formal loan participation |
| `loan_informal` | Informal loan participation |
| `defaulted` | Loan/default status |
| `formal_service_use` | Use of formal financial services |
| `mobile_money_access` | Access to mobile money |
| `barriers_mobile_money` | Barriers to mobile money |
| `mobile_ownership_1` | Mobile phone ownership |
| `experienced_shock` | Whether the respondent experienced a financial/economic shock |
| `nfhi_11` | Financial wellbeing-related indicator |
| `nfhi_12` | Financial wellbeing-related indicator |
| `nfhi_13` | Financial wellbeing-related indicator |
| `accessto_13k_1month` | Ability to access KSh 13,000 within one month |
| `not_difficult` | Financial difficulty indicator |
| `financial_status` | **Target variable** |
| `fl_score` | Financial literacy-related score |
| `prodsum1` | Financial product count |
| `barriers_bank` | Barriers to accessing banking services |
| `has_disability` | Disability status |

---

# 🔎 Exploratory Data Analysis

The project begins with an examination of the structure and quality of the dataset.

The following checks were performed:

- Dataset shape
- Column names
- Data types
- Missing values
- Duplicate observations
- Numerical summary statistics
- Categorical variable distributions
- Category values
- Outlier detection

Boxplots were used to investigate potential outliers in numerical variables.

---

# 🧹 Data Cleaning

Several data cleaning operations were performed before modelling.

### 1. Standardising Column Names

Column names were converted to lowercase to make them easier to work with consistently.

### 2. Education Level Cleaning

Education categories were standardised.

For example:

- `Completed technical training after secondary school` → `Technical Training completed`
- `Some secondary` → `Secondary incomplete`
- `Some university` → `University incomplete`
- `University completed` → `University completed`

Invalid or non-informative responses such as:

- Refused to Answer
- Don't know
- Other
- `95`

were removed from the education variable.

### 3. Marital Status Cleaning

Marital status categories were standardised.

For example:

- `Married/Living with partner` → `Married`
- `Divorced/separated` → `Divorced`
- `Single/Never Married` → `Single`
- `Widowed` → `Windowed`

Non-informative responses such as "Don't know" and "Refused to Answer" were removed.

### 4. Mobile Money Barrier Cleaning

The value `0` in `barriers_mobile_money` was mapped to:

`None`

### 5. Duplicate Records

Duplicate observations were checked and removed.

### 6. Missing Values

Missing values were investigated across the dataset.

The main variable containing missing observations was:

`barriers_bank`

Approximately **27.48%** of observations were missing in this variable.

The mode of `barriers_bank` was identified as:

`Affordability`

Missing values were subsequently replaced using the mode.

---

# 📈 Exploratory Data Analysis

Several visual analyses were performed to understand the dataset.

### Financial Status

The distribution of the target variable `financial_status` was examined.

The three financial wellbeing categories were:

- Improved
- Stayed the same
- Worsened

### Formal Savings by Location

Formal savings participation was compared between:

- Rural areas
- Urban areas

### Education and Disability

The education levels of respondents with disabilities were investigated.

### Household Size and Location

Household size was analysed according to location type using:

- Bar plots
- Boxplots

---

# 🧪 Hypothesis Testing

Statistical hypothesis testing was performed to investigate whether different variables were associated with financial wellbeing.

## Chi-Square Test of Independence

The **Chi-Square Test of Independence** was used to investigate relationships between categorical variables and `financial_status`.

The significance level was:

**α = 0.05**

The analysis rejected the null hypothesis for the categorical variables tested, including:

- County
- Location type
- Sex
- Age
- Education level
- Marital status
- Formal savings
- Informal savings
- Formal loans
- Informal loans
- Default status
- Formal financial service use
- Mobile money access
- Mobile money barriers
- Mobile ownership
- Experienced shocks
- NFHI indicators
- Access to KSh 13,000 within one month
- Financial difficulty
- Financial literacy score
- Banking barriers
- Disability status

This suggests statistically significant associations between these variables and financial status within the analysis.

---

## Kruskal-Wallis Test

The **Kruskal-Wallis test** was used to examine differences in numerical variables across the financial status groups.

The analysis found statistically significant differences in the distributions of:

- `household_size`
- `monthly_income`
- `prodsum1`

across the financial status categories.

---

## Correlation Analysis

Spearman correlation was used to examine relationships between numerical variables.

The main correlations observed were:

| Variables | Spearman Correlation |
|---|---:|
| Household size ↔ Monthly income | -0.116 |
| Household size ↔ Product count | -0.157 |
| Monthly income ↔ Product count | 0.433 |

The strongest relationship among these variables was between **monthly income and financial product count**, with a correlation of approximately **0.433**.

---

# ⚙️ Machine Learning Pipeline

The machine learning workflow followed these main steps:

```text
Raw Dataset
     ↓
Data Exploration
     ↓
Data Cleaning
     ↓
Exploratory Data Analysis
     ↓
Hypothesis Testing
     ↓
Feature / Target Separation
     ↓
Train-Test Split
     ↓
Encoding
     ↓
Scaling
     ↓
Model Training
     ↓
Model Evaluation
     ↓
Model Comparison
```

---

# 🎯 Target Variable

The target variable is:

```text
financial_status
```

The target contains three classes:

```text
Improved
Stayed the same
Worsened
```

The data was divided into:

- **80% training data**
- **20% testing data**

A `random_state` of **42** was used and stratification was applied to preserve the target class distribution.

The test set contained **4,171 observations**.

---

# 🔄 Data Preprocessing

## Target Encoding

`LabelEncoder` was used to convert the categorical target variable into numerical labels.

## Age Encoding

Age was treated as an ordinal variable using the following order:

```text
16-17
18-25
26-35
36-45
46-55
Above 55
```

An `OrdinalEncoder` was used to encode these categories.

## Categorical Encoding

Other categorical variables were converted into numerical variables using:

```python
pd.get_dummies()
```

with `drop_first=True`.

## Numerical Scaling

Numerical variables were scaled using:

```python
RobustScaler()
```

Robust scaling was selected to reduce the influence of extreme values.

---

# 🤖 Machine Learning Models

Several classification algorithms were trained and evaluated.

The models included:

1. Logistic Regression
2. Decision Tree
3. K-Nearest Neighbours (KNN)
4. Random Forest
5. Gradient Boosting
6. XGBoost
7. Support Vector Machine (SVM)

---

# 📊 Model Performance

The models were evaluated using:

- Precision
- Recall
- F1-score
- Accuracy

## Model Accuracy Comparison

| Model | Accuracy |
|---|---:|
| Logistic Regression | **58%** |
| XGBoost | **57%** |
| Gradient Boosting | **56%** |
| SVM | **56%** |
| Decision Tree | **54%** |
| Random Forest | **53%** |
| KNN – Manhattan | **52%** |
| KNN – Euclidean | **51%** |
| KNN – Minkowski | **51%** |

Based on the notebook results, **Logistic Regression achieved the highest test accuracy at approximately 58%**.

---

# 🏆 Best Performing Model

## Logistic Regression

The Logistic Regression model achieved:

- **Accuracy:** 58%
- **Macro F1-score:** 0.47
- **Weighted F1-score:** 0.54

Performance by class:

| Financial Status | Precision | Recall | F1-score |
|---|---:|---:|---:|
| Improved | 0.48 | 0.31 | 0.38 |
| Stayed the same | 0.48 | 0.24 | 0.32 |
| Worsened | 0.61 | 0.86 | 0.71 |

The model performed considerably better at identifying the **Worsened** class than the other two classes.

---

# ⚠️ Model Performance Considerations

Although Logistic Regression produced the highest accuracy among the tested models, the results show that the model has difficulty distinguishing between the **Improved** and **Stayed the same** categories.

The dataset also contains an imbalance in the target classes. The test set contained:

- Improved: **856**
- Stayed the same: **1,121**
- Worsened: **2,194**

Therefore, accuracy alone should not be used to judge the effectiveness of the models.

Precision, recall and F1-score are particularly important when evaluating this classification problem.

The Random Forest model, for example, failed to correctly identify any observations in the **Improved** class in the notebook results.

---

# 🛠️ Technologies Used

The project was developed using Python and the following libraries:

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- SciPy
- Scikit-learn
- XGBoost
- Jupyter Notebook

### Machine Learning Algorithms

```text
Logistic Regression
Decision Tree
K-Nearest Neighbours
Random Forest
Gradient Boosting
XGBoost
Support Vector Machine
```

---

# 📁 Recommended Repository Structure

```text
financial-wellbeing-kenyans/
│
├── data_raw/
│   └── finaccess2024_datasprint.xlsx
│
├── notebooks/
│   └── ml.ipynb
│
├── README.md
│
└── requirements.txt
```

> The raw dataset should only be included in the repository if its licensing and data-sharing permissions allow redistribution.

---

# 🚀 How to Run the Project

## 1. Clone the Repository

```bash
git clone https://github.com/YOUR-USERNAME/financial-wellbeing-kenyans.git
```

```bash
cd financial-wellbeing-kenyans
```

## 2. Create a Virtual Environment

Windows:

```bash
python -m venv fin_env
```

Activate it:

```bash
.\fin_env\Scripts\Activate.ps1
```

Linux/macOS:

```bash
python -m venv fin_env
source fin_env/bin/activate
```

## 3. Install Dependencies

```bash
pip install pandas numpy matplotlib seaborn scipy scikit-learn xgboost openpyxl jupyter
```

## 4. Launch Jupyter Notebook

```bash
jupyter notebook
```

Open:

```text
ml.ipynb
```

and run the cells sequentially.

---

# 📌 Key Findings

The analysis demonstrates that financial wellbeing is associated with a broad range of demographic, socioeconomic and financial inclusion variables.

The statistical analysis found significant relationships between financial status and the categorical variables tested.

The numerical analysis also found statistically significant differences in:

- Household size
- Monthly income
- Number of financial products

across financial wellbeing groups.

Among the machine learning algorithms tested, **Logistic Regression achieved the highest classification accuracy at 58%**.

However, the relatively modest performance and differences in class-level recall indicate that there is room for further model improvement.

---

# 🔮 Possible Improvements

Future versions of the project could investigate:

- Handling class imbalance using techniques such as SMOTE or class weighting.
- Hyperparameter tuning using GridSearchCV or RandomizedSearchCV.
- Feature selection.
- Cross-validation.
- Additional ensemble methods.
- Confusion matrices for all models.
- ROC-AUC and Precision-Recall analysis.
- Feature importance analysis.
- SHAP explainability.
- More extensive model comparison.
- Improved treatment of categorical variables.
- Further investigation of the financial status class imbalance.

These improvements could potentially increase the model's ability to distinguish between **Improved**, **Stayed the same**, and **Worsened** financial wellbeing.

---

# 📚 Project Purpose

The broader purpose of this project is to demonstrate how **data science and machine learning can be applied to financial inclusion data in Kenya**.

By analysing factors related to income, savings, loans, financial service access, demographics and financial resilience, machine learning can provide a framework for understanding and predicting changes in financial wellbeing.

---

# 👨‍💻 Author

**Martin Ndung'u Karanja**

Data Science & Machine Learning Project

---

## ⭐ Acknowledgements

This project uses data from the **FinAccess 2024** dataset and applies statistical analysis and machine learning techniques to investigate financial wellbeing among Kenyans.

---

## 📄 License

This project is intended for educational and analytical purposes.

Please verify the licensing and data-use conditions of the original FinAccess dataset before redistributing the raw data.#   F i n a n c i a l - W e l l b e i n g - P r e d i c t i o n  
 