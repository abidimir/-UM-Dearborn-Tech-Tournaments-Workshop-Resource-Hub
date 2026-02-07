# Datasets and Competitions

A curated list of beginner-friendly datasets and Kaggle competitions to practice your machine learning skills.

---

## Kaggle Getting Started Competitions

These competitions are always open, have tutorials, and are perfect for beginners.

| Competition | Type | Description | Link |
|-------------|------|-------------|------|
| **Titanic** | Classification | Predict passenger survival | [kaggle.com/c/titanic](https://www.kaggle.com/c/titanic) |
| **House Prices** | Regression | Predict house sale prices | [kaggle.com/c/house-prices-advanced-regression-techniques](https://www.kaggle.com/c/house-prices-advanced-regression-techniques) |
| **Digit Recognizer** | Classification | Classify handwritten digits (MNIST) | [kaggle.com/c/digit-recognizer](https://www.kaggle.com/c/digit-recognizer) |
| **Spaceship Titanic** | Classification | Predict passenger transport (modern Titanic) | [kaggle.com/c/spaceship-titanic](https://www.kaggle.com/c/spaceship-titanic) |

**Tip:** Start with Titanic or Spaceship Titanic for classification, House Prices for regression.

---

## Beginner-Friendly Kaggle Datasets

These datasets are well-documented and great for practice.

### Classification

| Dataset | Description | Size | Link |
|---------|-------------|------|------|
| **Iris** | Classic flower classification (3 classes) | 150 rows | [kaggle.com/datasets/uciml/iris](https://www.kaggle.com/datasets/uciml/iris) |
| **Heart Disease** | Predict heart disease presence | 303 rows | [kaggle.com/datasets/johnsmith88/heart-disease-dataset](https://www.kaggle.com/datasets/johnsmith88/heart-disease-dataset) |
| **Diabetes** | Predict diabetes diagnosis | 768 rows | [kaggle.com/datasets/uciml/pima-indians-diabetes-database](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database) |
| **Wine Quality** | Predict wine quality rating | 6,497 rows | [kaggle.com/datasets/uciml/red-wine-quality-cortez-et-al-2009](https://www.kaggle.com/datasets/uciml/red-wine-quality-cortez-et-al-2009) |
| **Mushroom Classification** | Edible vs poisonous mushrooms | 8,124 rows | [kaggle.com/datasets/uciml/mushroom-classification](https://www.kaggle.com/datasets/uciml/mushroom-classification) |
| **Breast Cancer Wisconsin** | Malignant vs benign tumors | 569 rows | [kaggle.com/datasets/uciml/breast-cancer-wisconsin-data](https://www.kaggle.com/datasets/uciml/breast-cancer-wisconsin-data) |

### Regression

| Dataset | Description | Size | Link |
|---------|-------------|------|------|
| **California Housing** | Predict house values | 20,640 rows | Built into sklearn |
| **Boston Housing** | Predict house prices | 506 rows | [kaggle.com/datasets/altavish/boston-housing-dataset](https://www.kaggle.com/datasets/altavish/boston-housing-dataset) |
| **Auto MPG** | Predict fuel efficiency | 398 rows | [kaggle.com/datasets/uciml/autompg-dataset](https://www.kaggle.com/datasets/uciml/autompg-dataset) |
| **Insurance Charges** | Predict medical costs | 1,338 rows | [kaggle.com/datasets/mirichoi0218/insurance](https://www.kaggle.com/datasets/mirichoi0218/insurance) |
| **Student Performance** | Predict exam scores | 1,000 rows | [kaggle.com/datasets/spscientist/students-performance-in-exams](https://www.kaggle.com/datasets/spscientist/students-performance-in-exams) |

### Larger Datasets (For More Challenge)

| Dataset | Description | Size | Link |
|---------|-------------|------|------|
| **Adult Income** | Predict income >$50K | 48,842 rows | [kaggle.com/datasets/uciml/adult-census-income](https://www.kaggle.com/datasets/uciml/adult-census-income) |
| **Credit Card Fraud** | Detect fraudulent transactions | 284,807 rows | [kaggle.com/datasets/mlg-ulb/creditcardfraud](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud) |
| **NYC Taxi** | Predict trip duration | 1.4M rows | [kaggle.com/c/nyc-taxi-trip-duration](https://www.kaggle.com/c/nyc-taxi-trip-duration) |

---

## Sklearn Built-in Datasets

These datasets are built into scikit-learn — no download needed!

```python
from sklearn.datasets import load_iris, load_wine, load_breast_cancer
from sklearn.datasets import fetch_california_housing
from sklearn.datasets import load_diabetes, load_digits

# Classification
iris = load_iris()
wine = load_wine()
cancer = load_breast_cancer()
digits = load_digits()

# Regression
housing = fetch_california_housing()
diabetes = load_diabetes()

# Convert to DataFrame
import pandas as pd
df = pd.DataFrame(iris.data, columns=iris.feature_names)
df['target'] = iris.target
```

| Dataset | Type | Samples | Features |
|---------|------|---------|----------|
| `load_iris()` | Classification (3 classes) | 150 | 4 |
| `load_wine()` | Classification (3 classes) | 178 | 13 |
| `load_breast_cancer()` | Classification (2 classes) | 569 | 30 |
| `load_digits()` | Classification (10 classes) | 1,797 | 64 |
| `fetch_california_housing()` | Regression | 20,640 | 8 |
| `load_diabetes()` | Regression | 442 | 10 |

---

## Other Dataset Sources

### General Purpose

| Source | Description | Link |
|--------|-------------|------|
| **UCI ML Repository** | Classic ML datasets | [archive.ics.uci.edu/ml](https://archive.ics.uci.edu/ml/) |
| **Kaggle Datasets** | 200,000+ datasets | [kaggle.com/datasets](https://www.kaggle.com/datasets) |
| **Google Dataset Search** | Search engine for datasets | [datasetsearch.research.google.com](https://datasetsearch.research.google.com/) |
| **Hugging Face Datasets** | NLP and ML datasets | [huggingface.co/datasets](https://huggingface.co/datasets) |
| **Data.gov** | US government open data | [data.gov](https://data.gov/) |

### Domain-Specific

| Domain | Source | Link |
|--------|--------|------|
| **Finance** | Yahoo Finance API | [yfinance on PyPI](https://pypi.org/project/yfinance/) |
| **Sports** | Sports Reference | [sports-reference.com](https://www.sports-reference.com/) |
| **Health** | CDC Data | [data.cdc.gov](https://data.cdc.gov/) |
| **Weather** | NOAA Climate Data | [ncdc.noaa.gov](https://www.ncdc.noaa.gov/cdo-web/) |
| **Images** | ImageNet | [image-net.org](https://www.image-net.org/) |

---

## Recommended Learning Path

### Week 1: Tiny Datasets
Start with these to learn the workflow without complexity:
1. Iris (150 rows, 4 features)
2. Wine (178 rows, 13 features)

### Week 2: Small Datasets
Add more complexity:
1. Heart Disease (303 rows)
2. Diabetes (768 rows)

### Week 3: Kaggle Getting Started
Apply your skills:
1. Titanic Competition
2. House Prices Competition

### Week 4: Real-World Datasets
Handle messier data:
1. Adult Income
2. Credit Card Fraud (imbalanced classes)

---

## Tips for Working with Datasets

### Before You Start

1. **Read the description** — Understand what each feature means
2. **Check the size** — Make sure your computer can handle it
3. **Look at examples** — See how others approached the same data

### Common Issues

| Issue | Solution |
|-------|----------|
| Missing values | Imputation or drop rows/columns |
| Categorical variables | One-hot encoding or label encoding |
| Imbalanced classes | Resampling, class weights, or different metrics |
| Large dataset | Sample for exploration, use full for final model |
| Text data | Tokenization, TF-IDF, or embeddings |

### Evaluation Metrics by Problem Type

| Problem | Common Metrics |
|---------|---------------|
| Binary Classification | Accuracy, Precision, Recall, F1, AUC-ROC |
| Multi-class Classification | Accuracy, Macro/Micro F1, Confusion Matrix |
| Regression | MAE, MSE, RMSE, R² |
| Imbalanced Classification | F1, Precision-Recall AUC, Cohen's Kappa |

---

## Quick Start Template

Here's a template to get started with any dataset:

```python
import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split, cross_val_score
from sklearn.ensemble import RandomForestClassifier  # or RandomForestRegressor
from sklearn.metrics import accuracy_score  # or appropriate metric

# 1. Load data
df = pd.read_csv('your_data.csv')

# 2. Quick exploration
print(df.shape)
print(df.head())
print(df.info())
print(df.describe())
print(df.isna().sum())

# 3. Prepare features and target
X = df.drop('target_column', axis=1)
y = df['target_column']

# 4. Handle missing values
X = X.fillna(X.median())  # Simple approach

# 5. Split data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# 6. Train and evaluate
model = RandomForestClassifier(random_state=42)
scores = cross_val_score(model, X_train, y_train, cv=5)
print(f"CV Score: {scores.mean():.4f} (+/- {scores.std():.4f})")

# 7. Final evaluation
model.fit(X_train, y_train)
print(f"Test Score: {model.score(X_test, y_test):.4f}")
```

---

## Resources for Finding More Datasets

- [Awesome Public Datasets](https://github.com/awesomedata/awesome-public-datasets) — Curated list on GitHub
- [Papers With Code Datasets](https://paperswithcode.com/datasets) — Datasets from research papers
- [r/datasets](https://www.reddit.com/r/datasets/) — Reddit community for dataset sharing
