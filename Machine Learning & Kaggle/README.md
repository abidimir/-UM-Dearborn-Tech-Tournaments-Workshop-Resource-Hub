# Machine Learning and Kaggle

This section introduces the fundamentals of machine learning (ML) and how to participate in Kaggle competitions. You'll learn how to build, evaluate, and improve predictive models.

---

## Learning Objectives

By the end of this section, you will be able to:

- Understand what machine learning is and when to use it
- Load, explore, and preprocess data for ML
- Train and evaluate a supervised learning model
- Avoid common pitfalls like data leakage and overfitting
- Submit predictions to a Kaggle competition

---

## Contents

| File | Description |
|------|-------------|
| [ML_CHEATSHEET.md](./ML_CHEATSHEET.md) | Quick reference for ML concepts, metrics, and common pitfalls |
| [basic_ml_model.ipynb](./basic_ml_model.ipynb) | Train your first supervised learning model |
| [validation_and_leakage.ipynb](./validation_and_leakage.ipynb) | Proper validation techniques and avoiding data leakage |
| [kaggle_submission.ipynb](./kaggle_submission.ipynb) | Step-by-step guide to submitting on Kaggle |
| [DATASETS.md](./DATASETS.md) | Links to beginner-friendly datasets and competitions |

---

## Prerequisites

Before starting, make sure you have:

- [ ] Python 3.10+ installed
- [ ] Jupyter Notebook or JupyterLab (or VS Code with Jupyter extension)
- [ ] A Kaggle account ([kaggle.com](https://www.kaggle.com))
- [ ] Basic Python knowledge (variables, loops, functions)

### Install Required Libraries

```bash
pip install pandas numpy matplotlib scikit-learn seaborn
```

Or create a virtual environment first:

```bash
python -m venv venv
source venv/bin/activate  # macOS/Linux
venv\Scripts\activate     # Windows
pip install pandas numpy matplotlib scikit-learn seaborn
```

---

## What is Machine Learning?

**Machine learning** is teaching computers to learn patterns from data, rather than explicitly programming rules.

### Traditional Programming vs. Machine Learning

| Traditional Programming | Machine Learning |
|------------------------|------------------|
| Input: Data + Rules | Input: Data + Answers |
| Output: Answers | Output: Rules (a model) |

**Example:** Spam detection
- **Traditional:** Write rules like "if email contains 'FREE MONEY', mark as spam"
- **ML:** Show the computer thousands of spam and non-spam emails, let it learn the patterns

### Types of Machine Learning

| Type | What it does | Example |
|------|--------------|---------|
| **Supervised Learning** | Learn from labeled data (inputs → known outputs) | Predict house prices, classify emails |
| **Unsupervised Learning** | Find patterns in unlabeled data | Customer segmentation, anomaly detection |
| **Reinforcement Learning** | Learn by trial and error with rewards | Game AI, robotics |

This section focuses on **supervised learning**, the most common type in practice.

---

## The ML Workflow

Every ML project follows a similar workflow:

```
1. Define the Problem
        ↓
2. Collect & Explore Data (EDA)
        ↓
3. Prepare Data (Cleaning, Feature Engineering)
        ↓
4. Split Data (Train / Validation / Test)
        ↓
5. Train Model
        ↓
6. Evaluate Model
        ↓
7. Improve (iterate on steps 3-6)
        ↓
8. Deploy / Submit Predictions
```

The labs in this section walk through each step.

---

## Supervised Learning: Regression vs. Classification

| Task | Output Type | Example | Metrics |
|------|-------------|---------|---------|
| **Regression** | Continuous number | Predict house price ($350,000) | MAE, RMSE, R² |
| **Classification** | Category/class | Is this email spam? (Yes/No) | Accuracy, Precision, Recall, F1 |

---

## Suggested Learning Path

1. **Read the ML Cheatsheet** — Understand key concepts and terminology
2. **Complete Basic ML Model Lab** — Build your first model end-to-end
3. **Complete Validation & Leakage Lab** — Learn proper evaluation techniques
4. **Complete Kaggle Submission Lab** — Enter your first competition
5. **Explore Datasets** — Practice on more datasets

---

## External Resources

### Beginner-Friendly

- [Kaggle Learn: Intro to Machine Learning](https://www.kaggle.com/learn/intro-to-machine-learning) — Free interactive course
- [StatQuest: Machine Learning Fundamentals](https://www.youtube.com/playlist?list=PLblh5JKOoLUICTaGLRoHQDuF_7q2GfuJF) — Excellent video explanations
- [Google's ML Crash Course](https://developers.google.com/machine-learning/crash-course) — Comprehensive free course
- [Scikit-learn User Guide](https://scikit-learn.org/stable/user_guide.html) — Official documentation

### Going Deeper

- [Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow](https://www.oreilly.com/library/view/hands-on-machine-learning/9781492032632/) — Popular book
- [Fast.ai Practical Deep Learning](https://course.fast.ai/) — Free deep learning course
- [3Blue1Brown: Neural Networks](https://www.youtube.com/playlist?list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi) — Visual explanations

### Kaggle

- [Kaggle Competitions](https://www.kaggle.com/competitions) — Browse active competitions
- [Kaggle Notebooks](https://www.kaggle.com/code) — Learn from others' code
- [Kaggle Datasets](https://www.kaggle.com/datasets) — Find datasets to practice on

---

## Common Questions

**Q: Do I need to know math to do ML?**

For using ML (what we cover here): basic statistics helps, but you can start without deep math knowledge. The libraries handle the math for you. For understanding ML deeply: linear algebra, calculus, and probability become important.

**Q: How much data do I need?**

It depends on the problem complexity. For simple problems, a few hundred rows can work. For complex problems, you may need thousands or millions. Start with what you have and see if the model learns anything useful.

**Q: Which algorithm should I use?**

Start simple. For regression, try Linear Regression first. For classification, try Logistic Regression or Random Forest. If those don't work well enough, try more complex models. The best algorithm depends on your data.

---