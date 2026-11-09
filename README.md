# Jamboree Education – Graduate Admission Prediction | Linear Regression

## Project Overview

Jamboree Education helps students prepare for higher education admissions, particularly for graduate programmes at international universities.

This project focuses on developing a predictive model to estimate a student's **Chance of Admit** based on academic performance and other application-related factors.

Using Exploratory Data Analysis, statistical analysis, feature engineering, and regression techniques, the project identifies the factors that influence admission probability and builds a model to predict admission chances.

The primary objective is to help students understand how their academic profiles relate to admission prospects and enable Jamboree to offer more data-driven guidance.

## Business Objectives

- Understand the factors influencing graduate admission chances.
- Analyse relationships between academic performance and admission probability.
- Identify the most influential features affecting admission chances.
- Investigate multicollinearity among independent variables.
- Build and compare Linear, Ridge, and Lasso Regression models.
- Evaluate model performance using appropriate regression metrics.
- Validate Linear Regression assumptions.
- Provide recommendations for improving the predictive model and its real-world application.

## Dataset Overview

The dataset contains **500 student records and 9 columns**, representing academic performance and application-related attributes.

| Feature | Description |
|---|---|
| Serial No. | Unique student identifier |
| GRE Score | Graduate Record Examination score |
| TOEFL Score | Test of English as a Foreign Language score |
| University Rating | Rating of the student's undergraduate university |
| SOP | Strength of Statement of Purpose |
| LOR | Strength of Letter of Recommendation |
| CGPA | Undergraduate cumulative grade point average |
| Research | Indicates whether the student has research experience |
| Chance of Admit | Estimated probability of admission |

**Data observations:**
- 500 records and 9 columns.
- No missing values identified.
- No duplicate records identified.
- Numerical and categorical variables are represented using integer and floating-point data types.
- The target variable is `Chance of Admit`.

## Tools & Technologies

- **Python**
- **Pandas & NumPy** – Data manipulation and numerical analysis
- **Matplotlib & Seaborn** – Data visualization
- **Scikit-learn** – Linear Regression, Ridge, Lasso, StandardScaler, and model evaluation
- **Statsmodels** – OLS regression and statistical analysis
- **SciPy** – Statistical testing
- **Jupyter Notebook** – Analysis and experimentation

## Project Workflow

### 1. Data Loading & Inspection

- Imported the required Python libraries.
- Loaded the Jamboree admission dataset.
- Examined dataset dimensions, data types, and statistical summaries.
- Checked for missing values and duplicate records.
- Removed the `Serial No.` column because it does not provide meaningful predictive information.

### 2. Exploratory Data Analysis (EDA)

**Univariate Analysis**
- Examined distributions of GRE Score, TOEFL Score, CGPA, and Chance of Admit.
- Analysed categorical variables such as University Rating, SOP, LOR, and Research.
- Used histograms, KDE plots, and boxplots to understand distributions and identify outliers.

**Bivariate Analysis**
- Examined relationships between academic scores and Chance of Admit.
- Compared admission chances across university ratings.
- Analysed the influence of SOP and LOR strength.
- Compared admission chances between students with and without research experience.

**Multivariate Analysis**
- Used pairplots and correlation heatmaps to identify relationships between independent variables.
- Examined correlations between academic performance indicators and the target variable.
- Identified potential multicollinearity among predictors.

### 3. Data Preprocessing

- Separated independent variables and the target variable.
- Applied StandardScaler to standardize numerical features.
- Split the dataset into training and testing sets.
- Used a 70:30 train-test split with `random_state=1`.

### 4. Model Building

Built and compared three regression models:

- Linear Regression
- Ridge Regression
- Lasso Regression

Also used Statsmodels OLS regression to examine model coefficients, statistical significance, and regression performance.

### 5. Model Evaluation

Evaluated model performance using:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R-squared
- Adjusted R-squared

### 6. Multicollinearity Analysis

Used **Variance Inflation Factor (VIF)** to identify multicollinearity among independent variables.

The analysis involved:
- Calculating VIF values for the predictors.
- Identifying variables contributing to multicollinearity.
- Iteratively removing selected features.
- Retaining CGPA and Research for a reduced-feature model.

The reduced-feature model was evaluated against the original model to understand the impact of feature selection on predictive performance.

### 7. Linear Regression Assumption Testing

Evaluated the key assumptions of Linear Regression:

**Linearity**
- Examined scatterplots, pairplots, and correlation relationships between predictors and the target variable.

**Normality of Residuals**
- Used residual histograms and Q-Q plots.
- Applied the Shapiro-Wilk test.

**Homoscedasticity**
- Examined residuals against predicted values.
- Applied the Goldfeld-Quandt test.

**Multicollinearity**
- Used VIF to assess correlations among independent variables.

**Mean of Residuals**
- Examined residual behaviour to assess prediction errors.

## Key Findings

### 1. Exploratory Data Analysis

- Most GRE scores fall between 310 and 320.
- Most TOEFL scores fall between 105 and 110.
- CGPA values are concentrated between 8.5 and 9.
- Most students have a Chance of Admit between 70% and 75%.
- University Rating 3 is the most frequently observed rating.
- SOP strength 4 and LOR strength 3 are common among applicants.
- Most students in the dataset have research experience.

### 2. Factors Influencing Admission Chances

- CGPA has a very strong positive relationship with Chance of Admit.
- GRE and TOEFL scores also show strong positive correlations with admission chances.
- Higher University Ratings are associated with higher admission chances.
- Students with research experience generally have higher admission chances.
- Higher SOP and LOR ratings are associated with better admission prospects.

### 3. Multicollinearity

- Multicollinearity was identified among several independent variables.
- VIF analysis was used to examine and reduce the issue.
- The reduced model retained CGPA and Research as predictors.
- The reduced model maintained comparable test-set R-squared performance.

### 4. Model Performance

The three regression models achieved similar performance on the original feature set.

| Model | Test MAE | Test RMSE | Test R² | Adjusted R² |
|---|---:|---:|---:|---:|
| Linear Regression | 0.04 | 0.06 | 0.82 | 0.81 |
| Ridge Regression | 0.04 | 0.06 | 0.82 | 0.81 |
| Lasso Regression | 0.04 | 0.06 | 0.82 | 0.81 |

**Key observations:**
- Linear Regression and Ridge Regression achieved comparable performance.
- Lasso Regression produced a zero coefficient for SOP in the original model.
- The models demonstrated similar training and testing performance.

### 5. Reduced-Feature Model

After VIF-based feature selection, the model was retrained using only CGPA and Research.

| Metric | Test Performance |
|---|---:|
| MAE | 0.05 |
| RMSE | 0.07 |
| R² | 0.81 |
| Adjusted R² | 0.81 |

The reduced-feature model achieved an R² of 0.81 compared with 0.82 for the original model, indicating comparable predictive performance with fewer predictors.

### 6. Regression Assumption Testing

- The EDA and regression analysis indicated approximately linear relationships between important predictors and the target.
- Residual histograms and Q-Q plots were used to examine normality.
- The Shapiro-Wilk statistic was approximately 0.89.
- The residual-versus-predicted plot did not show a clear funnel pattern.
- The Goldfeld-Quandt test returned an F-statistic of approximately 1.143 and a p-value of 0.193.

These results did not provide strong evidence of heteroscedasticity at the 5% significance level.

## Business Recommendations

Based on the analysis, the following recommendations were identified:

1. **Focus on Academic Performance:** Encourage students to improve their CGPA, which emerged as the strongest predictor in the regression analysis.

2. **Promote Research Experience:** Encourage students to participate in research projects and academic activities to strengthen their applications.

3. **Improve Admission Guidance:** Use the predictive model as a supporting tool to help students understand how their academic profiles relate to admission prospects.

4. **Enhance Predictive Features:** Explore additional variables such as work experience, extracurricular activities, internships, demographic information, and programme preferences.

5. **Improve Model Reliability:** Validate the model using larger and more diverse datasets to improve its generalizability.

6. **Integrate the Model into Jamboree's Platform:** Consider developing an admission prediction tool that allows students to estimate their admission chances using their academic profiles.

7. **Continuous Model Monitoring:** Regularly evaluate and update the model as admission trends and university selection criteria evolve.

## Key Learnings

Through this project, I strengthened my understanding of:

- Exploratory Data Analysis and feature relationships.
- Data preprocessing and feature standardization.
- Linear Regression and its underlying assumptions.
- Ridge and Lasso regularization.
- Multicollinearity and Variance Inflation Factor (VIF).
- OLS regression and statistical significance.
- Model evaluation using MAE, RMSE, R², and Adjusted R².
- Residual analysis and regression diagnostics.
- Feature selection and model simplification.
- Applying predictive analytics to real-world business problems.

## Repository Structure

```text
Jamboree-Education-Case-Study/
│
├── Case_Study_Jamboree_Education_Linear_Regression.ipynb
├── Jamboree_Admission.csv
└── README.md
```

*Note: Include the dataset in the repository only if its distribution is permitted.*

## Conclusion

This project demonstrates how Linear Regression and statistical analysis can be used to understand and predict graduate admission chances.

The analysis identified CGPA, GRE Score, and TOEFL Score as important predictors of admission probability. It also highlighted multicollinearity among independent variables and demonstrated how VIF-based feature selection can simplify a model while maintaining comparable predictive performance.

The final reduced-feature model achieved an R² of 0.81 using only CGPA and Research, providing a simpler alternative to the original model.

The project highlights the practical application of predictive analytics in helping students make more informed decisions about their higher education journey.

---

## Author

**Umar Reyaz**

Data Analyst | Data Science & AI/ML Enthusiast

- **LinkedIn:** https://www.linkedin.com/in/umar-reyaz-55a164272
- **GitHub:** https://github.com/umar16257-design
- **Email:** umar16257@gmail.com
