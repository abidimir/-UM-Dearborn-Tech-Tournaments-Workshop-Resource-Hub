# Machine Learning Cheatsheet

A quick reference for core ML concepts, metrics, and common pitfalls.

---

## Key Terminology

| Term | Definition |
|------|------------|
| **Features (X)** | Input variables used to make predictions (also called predictors, independent variables) |
| **Target (y)** | The variable you're trying to predict (also called label, dependent variable) |
| **Training set** | Data used to train the model |
| **Validation set** | Data used to tune the model and select hyperparameters |
| **Test set** | Data used for final evaluation (never used during training) |
| **Model** | The algorithm that learns patterns from data |
| **Hyperparameters** | Settings you choose before training (e.g., tree depth, learning rate) |
| **Overfitting** | Model performs well on training data but poorly on new data |
| **Underfitting** | Model is too simple to capture patterns in the data |

---

## The ML Workflow

```python
# 1. Load data
import pandas as pd
df = pd.read_csv('data.csv')

# 2. Explore data
df.head()
df.info()
df.describe()

# 3. Prepare features and target
X = df.drop('target_column', axis=1)
y = df['target_column']

# 4. Split data
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# 5. Train model
from sklearn.linear_model import LinearRegression
model = LinearRegression()
model.fit(X_train, y_train)

# 6. Make predictions
y_pred = model.predict(X_test)

# 7. Evaluate
from sklearn.metrics import mean_squared_error
mse = mean_squared_error(y_test, y_pred)
```

---

## Common Algorithms

### Regression (Predicting Numbers)

| Algorithm | When to use | Sklearn |
|-----------|-------------|---------|
| **Linear Regression** | Simple, interpretable baseline | `LinearRegression()` |
| **Ridge / Lasso** | When you have many features | `Ridge()`, `Lasso()` |
| **Random Forest** | Non-linear relationships | `RandomForestRegressor()` |
| **Gradient Boosting** | Best performance (often) | `GradientBoostingRegressor()` |

### Classification (Predicting Categories)

| Algorithm | When to use | Sklearn |
|-----------|-------------|---------|
| **Logistic Regression** | Simple, interpretable baseline | `LogisticRegression()` |
| **Decision Tree** | Interpretable, handles non-linear | `DecisionTreeClassifier()` |
| **Random Forest** | Robust, less overfitting | `RandomForestClassifier()` |
| **Gradient Boosting** | Best performance (often) | `GradientBoostingClassifier()` |
| **K-Nearest Neighbors** | Simple, no training needed | `KNeighborsClassifier()` |

---

## Evaluation Metrics

### Regression Metrics

| Metric | What it measures | Formula intuition | Good values |
|--------|------------------|-------------------|-------------|
| **MAE** (Mean Absolute Error) | Average absolute difference | "On average, predictions are off by X" | Lower is better |
| **MSE** (Mean Squared Error) | Average squared difference | Penalizes large errors more | Lower is better |
| **RMSE** (Root MSE) | Square root of MSE | Same units as target | Lower is better |
| **R²** (R-squared) | Proportion of variance explained | "Model explains X% of variation" | Closer to 1 is better |

```python
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score
import numpy as np

mae = mean_absolute_error(y_test, y_pred)
mse = mean_squared_error(y_test, y_pred)
rmse = np.sqrt(mse)
r2 = r2_score(y_test, y_pred)
```

### Classification Metrics

| Metric | What it measures | When to use |
|--------|------------------|-------------|
| **Accuracy** | % of correct predictions | Balanced classes |
| **Precision** | Of predicted positives, % actually positive | When false positives are costly |
| **Recall** | Of actual positives, % correctly predicted | When false negatives are costly |
| **F1 Score** | Balance of precision and recall | Imbalanced classes |
| **AUC-ROC** | Model's ability to distinguish classes | Comparing models |

```python
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score

accuracy = accuracy_score(y_test, y_pred)
precision = precision_score(y_test, y_pred)
recall = recall_score(y_test, y_pred)
f1 = f1_score(y_test, y_pred)
```

### Confusion Matrix

```
                  Predicted
                  Neg    Pos
Actual  Neg       TN     FP
        Pos       FN     TP

TN = True Negative  (correctly predicted negative)
FP = False Positive (incorrectly predicted positive) - Type I Error
FN = False Negative (incorrectly predicted negative) - Type II Error
TP = True Positive  (correctly predicted positive)
```

```python
from sklearn.metrics import confusion_matrix
cm = confusion_matrix(y_test, y_pred)
```

---

## Data Splitting

### Simple Train/Test Split

```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    X, y, 
    test_size=0.2,      # 20% for testing
    random_state=42     # For reproducibility
)
```

### Train/Validation/Test Split

```python
# First split: separate test set
X_temp, X_test, y_temp, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Second split: separate validation from training
X_train, X_val, y_train, y_val = train_test_split(X_temp, y_temp, test_size=0.25, random_state=42)

# Result: 60% train, 20% validation, 20% test
```

### Cross-Validation

More robust than a single split—uses all data for both training and validation.

```python
from sklearn.model_selection import cross_val_score

scores = cross_val_score(model, X, y, cv=5)  # 5-fold CV
print(f"Mean: {scores.mean():.3f}, Std: {scores.std():.3f}")
```

---

## Feature Engineering

### Handling Missing Values

```python
# Check for missing values
df.isna().sum()

# Option 1: Drop rows with missing values
df_clean = df.dropna()

# Option 2: Fill with a value
df['column'] = df['column'].fillna(df['column'].median())

# Option 3: Use sklearn Imputer
from sklearn.impute import SimpleImputer
imputer = SimpleImputer(strategy='median')
X_imputed = imputer.fit_transform(X)
```

### Encoding Categorical Variables

```python
# Option 1: One-hot encoding (for nominal categories)
df_encoded = pd.get_dummies(df, columns=['category_column'])

# Option 2: Label encoding (for ordinal categories)
from sklearn.preprocessing import LabelEncoder
le = LabelEncoder()
df['category_encoded'] = le.fit_transform(df['category_column'])
```

### Scaling Features

```python
from sklearn.preprocessing import StandardScaler, MinMaxScaler

# Standardization (mean=0, std=1) - use for most algorithms
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

# Min-Max scaling (0 to 1) - use when you need bounded values
scaler = MinMaxScaler()
X_scaled = scaler.fit_transform(X)
```

**Important:** Fit the scaler on training data only, then transform both train and test.

```python
scaler.fit(X_train)
X_train_scaled = scaler.transform(X_train)
X_test_scaled = scaler.transform(X_test)
```

---

## Common Pitfalls

### 1. Data Leakage

**What:** Information from the test set "leaks" into training, giving unrealistically good results.

**Examples:**
- Scaling/encoding using the entire dataset before splitting
- Including features that wouldn't be available at prediction time
- Target leakage: features derived from the target

**How to avoid:**
- Always split data FIRST
- Fit preprocessors on training data only
- Think: "Would I have this information when making a real prediction?"

### 2. Overfitting

**What:** Model memorizes training data instead of learning general patterns.

**Signs:**
- Training score is much higher than validation score
- Model is very complex

**How to avoid:**
- Use cross-validation
- Use simpler models
- Regularization (Ridge, Lasso)
- Get more training data

### 3. Underfitting

**What:** Model is too simple to capture patterns.

**Signs:**
- Both training and validation scores are low
- Model doesn't improve with more data

**How to avoid:**
- Use more complex models
- Add more features
- Reduce regularization

### 4. Not Setting Random State

**What:** Results change every time you run the code.

**Fix:** Set `random_state` in functions that have randomness:

```python
train_test_split(X, y, random_state=42)
RandomForestClassifier(random_state=42)
```

### 5. Ignoring Class Imbalance

**What:** When one class is much more common (e.g., 95% negative, 5% positive).

**Problem:** Model can get 95% accuracy by always predicting the majority class.

**Fixes:**
- Use metrics like F1, precision, recall instead of accuracy
- Use `class_weight='balanced'` in sklearn models
- Oversample minority class or undersample majority class

---

## Quick Debugging

| Problem | Possible Causes |
|---------|-----------------|
| Very high training score, low test score | Overfitting |
| Both scores are low | Underfitting, bad features, bug in code |
| Results change each run | Missing random_state |
| Perfect or near-perfect score | Data leakage |
| Model always predicts same class | Class imbalance, bug in preprocessing |

---

## Sklearn Import Reference

```python
# Data splitting
from sklearn.model_selection import train_test_split, cross_val_score

# Preprocessing
from sklearn.preprocessing import StandardScaler, MinMaxScaler, LabelEncoder
from sklearn.impute import SimpleImputer

# Regression models
from sklearn.linear_model import LinearRegression, Ridge, Lasso
from sklearn.ensemble import RandomForestRegressor, GradientBoostingRegressor

# Classification models
from sklearn.linear_model import LogisticRegression
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier, GradientBoostingClassifier
from sklearn.neighbors import KNeighborsClassifier

# Metrics - Regression
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score

# Metrics - Classification
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score
from sklearn.metrics import confusion_matrix, classification_report
```

---

## Tips for Success

1. **Start simple** — Linear/Logistic Regression first, then try complex models
2. **Understand your data** — EDA before modeling
3. **Validate properly** — Cross-validation > single split
4. **Watch for leakage** — Split first, preprocess second
5. **Iterate** — ML is experimental; try things and see what works
6. **Read error messages** — They usually tell you what's wrong
7. **Check baselines** — How well does a simple model do? Can you beat it?