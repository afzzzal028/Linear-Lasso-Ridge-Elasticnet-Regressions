# Student Performance Prediction

A machine learning regression project that predicts student exam scores using study habits, attendance, parental involvement, access to resources, and other academic factors.

## Problem Statement
The aim of this project is to predict a student's `Exam_Score` based on academic, social, and lifestyle-related factors. This is a regression problem because the target variable is continuous.

## Dataset
This project uses the `StudentPerformanceFactors.csv` dataset.

The dataset contains 20 columns, including:
- `Hours_Studied`
- `Attendance`
- `Parental_Involvement`
- `Access_to_Resources`
- `Extracurricular_Activities`
- `Sleep_Hours`
- `Previous_Scores`
- `Motivation_Level`
- `Internet_Access`
- `Tutoring_Sessions`
- `Family_Income`
- `Teacher_Quality`
- `School_Type`
- `Peer_Influence`
- `Physical_Activity`
- `Learning_Disabilities`
- `Parental_Education_Level`
- `Distance_from_Home`
- `Gender`
- `Exam_Score`

Target column:
- `Exam_Score`

## What Was Done in the Notebook
### 1. Data Loading and Inspection
- Loaded the dataset using pandas
- Checked structure with `df.info()`
- Generated summary statistics with `df.describe()`
- Viewed sample rows with `df.head()`
- Checked missing values using `df.isnull().sum()`

### 2. Missing Value Handling
- Filled missing values in:
  - `Distance_from_Home` with `Near`
  - `Parental_Education_Level` with `None`
  - `Teacher_Quality` with `Medium`

### 3. Exploratory Data Analysis
- Calculated mean of `Exam_Score`
- Visualized `Exam_Score` distribution using seaborn KDE plot

### 4. Encoding Selected Features
Mapped categorical columns manually:
- `Gender`: Male = 1, Female = 0
- `Internet_Access`: Yes = 1, No = 0
- `Access_to_Resources`: High = 2, Medium = 1, Low = 0
- `Parental_Involvement`: High = 2, Medium = 1, Low = 0

### 5. Feature Selection
Used the following features in the final training step:
- `Parental_Involvement`
- `Internet_Access`
- `Attendance`
- `Hours_Studied`
- `Access_to_Resources`
- `Sleep_Hours`
- `Tutoring_Sessions`

Target variable:
- `Exam_Score`

### 6. Train-Test Split and Scaling
- Split the data into training and testing sets
- Applied `StandardScaler` to the feature set

### 7. Models Used
#### Linear Regression
- Trained a `LinearRegression` model
- Predicted exam scores
- Evaluated using:
  - MAE
  - MSE
  - RMSE
  - R² score
  - train score
  - test score

#### Ridge Regression
- Initialized a `Ridge` model
- Used `GridSearchCV` to search for the best `alpha`
- Best estimator shown in the notebook: `Ridge(alpha=1)`

## Results
### Linear Regression
- **MAE:** 1.1107
- **MSE:** 4.3986
- **RMSE:** 2.0973
- **R² Score:** 0.6799
- **Train Score:** 0.6142
- **Test Score:** 0.6799

### Cross Validation
- Used 5-fold cross-validation with `neg_mean_squared_error`
- Mean CV score shown: **-5.5753**

### Ridge Regression
- Ridge with GridSearchCV was started and tuned
- Best estimator shown in notebook: **Ridge(alpha=1)**
- However, the notebook does not clearly present the final Ridge metrics in a clean summary

## What Can Be Improved
This notebook has a solid base, but to make it portfolio-worthy, these improvements are needed:

1. **Clean notebook flow**
   - remove repeated or unnecessary cells
   - keep the notebook in a clear sequence: load → clean → analyze → model → compare → conclude

2. **Use more of the dataset properly**
   - many useful categorical columns are not used in the final model
   - use one-hot encoding for more features instead of manual encoding only a few columns

3. **Make model comparison clearer**
   - present Linear Regression vs Ridge Regression in a final results table
   - include Ridge MAE, RMSE, and R² clearly

4. **Add interpretation**
   - explain which features matter most
   - interpret model coefficients for Linear Regression

5. **Improve presentation quality**
   - add markdown headings throughout notebook
   - remove unnecessary long HTML estimator outputs
   - explain each step briefly

## Conclusion
This project demonstrates a beginner-to-intermediate machine learning workflow for predicting student exam scores.

The notebook shows:
- data inspection
- missing value handling
- feature encoding
- regression modeling
- evaluation metrics
- basic regularization with Ridge Regression

With better notebook organization, clearer model comparison, and stronger feature handling, this project can become a strong GitHub portfolio project.

## Project Structure
```text
student_records/
├── .gitignore
├── NOTES.md
├── README.md
├── requirements.txt
├── StudentPerformanceFactors.csv
└── student_performance.ipynb
```

## How to Run
1. Keep `StudentPerformanceFactors.csv` in the same folder as the notebook.
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Open `student_performance.ipynb` in Jupyter Notebook or VS Code.
4. Run the cells in order.

## GitHub Repository Description
Student performance prediction using Linear Regression and Ridge Regression with data preprocessing, feature encoding, scaling, and model evaluation in Python.
