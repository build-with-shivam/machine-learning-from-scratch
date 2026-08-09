# 📧 Logistic Regression — Spam Email Detection

This project is part of the **Machine Learning From Scratch** learning series.

The goal is to understand how **Logistic Regression** can be used for a real-world **classification problem** — detecting whether an email is **Spam** or **Not Spam (Ham)**.

Instead of only using a pre-built model, this project focuses on understanding the complete ML workflow:

```text
Raw Email
   ↓
Text Data
   ↓
TF-IDF
   ↓
Numerical Features
   ↓
Logistic Regression
   ↓
Prediction
   ↓
Confusion Matrix
   ↓
Classification Metrics
```

---

## 🎯 What Are We Building?

We are building a simple **Spam Email Classifier**.

Given an email such as:

> "Congratulations! You have won a $1,000 prize. Click here to claim."

The model should predict:

```text
Spam
```

While an email such as:

> "Hi Shivam, can we schedule a meeting tomorrow?"

should be classified as:

```text
Not Spam
```

This is a **binary classification** problem because there are only two possible classes:

```text
Spam
Not Spam
```

---

# 🧠 Concepts Covered

This project introduces several important Machine Learning concepts.

### 1. Classification

Classification is a supervised learning problem where the model predicts a **category/class**.

Examples:

| Problem           | Classes              |
| ----------------- | -------------------- |
| Spam Detection    | Spam / Not Spam      |
| Disease Detection | Disease / No Disease |
| Fraud Detection   | Fraud / Not Fraud    |
| Customer Churn    | Churn / No Churn     |

In this project:

```text
Input  → Email Text
Output → Spam or Not Spam
```

---

### 2. Logistic Regression

Despite its name, **Logistic Regression is primarily used for classification problems**.

It takes input features and calculates a probability.

For example:

```text
Email
  ↓
Model
  ↓
Probability = 0.93
  ↓
Spam
```

A common decision rule is:

```text
Probability >= 0.5 → Class 1
Probability <  0.5 → Class 0
```

So:

```text
0.93 → Spam
0.12 → Not Spam
```

The threshold can also be changed depending on the business requirement.

---

# 📝 Why Can't Logistic Regression Directly Read Text?

Machine Learning algorithms work with numerical values.

But an email is text:

```text
"Congratulations! You won a prize."
```

We therefore need to convert the text into numerical features.

For this project, we use:

## TF-IDF

**TF-IDF = Term Frequency — Inverse Document Frequency**

It converts text into numbers based on how important words are within a collection of documents.

For example:

```text
Email 1 → "free money click here"
Email 2 → "meeting scheduled tomorrow"
Email 3 → "free prize click now"
```

Words that are useful for distinguishing documents receive higher importance.

The result is a numerical feature matrix that Logistic Regression can understand.

```text
Email Text
    ↓
TF-IDF
    ↓
Numerical Matrix
    ↓
Logistic Regression
```

---

# 🔢 Dataset

The project uses a labeled email dataset containing examples of:

* Spam emails
* Legitimate emails

Each row contains:

```text
Email Text → Target Label
```

Conceptually:

| Email                                 | Label    |
| ------------------------------------- | -------- |
| "Win a free iPhone now!"              | Spam     |
| "Meeting at 10 AM tomorrow"           | Not Spam |
| "Claim your prize today"              | Spam     |
| "Please review the attached document" | Not Spam |

The model learns patterns from the training data and then predicts the class of previously unseen emails.

---

# 🔄 Machine Learning Workflow

The project follows the standard supervised learning workflow.

## 1. Load the Dataset

We first load the email dataset into Python.

```text
Dataset
   ↓
Pandas DataFrame
```

---

## 2. Separate Features and Target

We separate:

### X — Features

The email text that the model will use to make predictions.

```text
X = email text
```

### y — Target

The answer we want the model to learn.

```text
y = Spam / Not Spam
```

Conceptually:

```text
X                          y
--------------------      --------
"Win a free prize"   →    Spam
"Meeting tomorrow"   →    Not Spam
"Claim your reward"  →    Spam
```

---

## 3. Split the Data

The dataset is divided into training and testing data.

```text
Complete Dataset
       │
       ├───────────────┐
       ↓               ↓
 Training Data     Testing Data
       │               │
       ↓               ↓
   Learn patterns    Evaluate
```

The model learns from the training data.

The test data is kept separate so we can evaluate how well the model performs on unseen emails.

---

## 4. Convert Text Using TF-IDF

The raw email text cannot be directly given to Logistic Regression.

We transform it:

```text
Raw Text
   ↓
TF-IDF Vectorization
   ↓
Numerical Features
```

For example:

```text
"free prize now"
```

may become something conceptually similar to:

```text
[0.42, 0.00, 0.71, 0.35, ...]
```

The actual vector contains many dimensions because the vocabulary may contain thousands of words.

---

## 5. Train Logistic Regression

The numerical features are passed to Logistic Regression.

```text
TF-IDF Features
       ↓
Logistic Regression
       ↓
Learned Model
```

During training, the model learns which combinations of words/features are associated with spam.

---

## 6. Make Predictions

After training, we pass unseen test emails to the model.

```text
Test Email
    ↓
TF-IDF
    ↓
Logistic Regression
    ↓
Prediction
```

Example:

```text
"Congratulations! You won $10,000"

Prediction:
Spam
```

---

# 📊 Model Evaluation

A classification model should not be evaluated using regression metrics such as RMSE simply because we used a mathematical model.

The evaluation metric should depend on the **problem type and business objective**.

For spam detection, we use classification metrics.

---

## Confusion Matrix

A confusion matrix helps us understand what the model predicted versus what was actually true.

For binary classification:

```text
                    Actual
                 Spam    Not Spam
              ┌────────┬─────────┐
Predicted     │        │         │
Spam          │   TP   │   FP    │
              ├────────┼─────────┤
Not Spam      │   FN   │   TN    │
              └────────┴─────────┘
```

### TP — True Positive

The model predicted Spam and the email was actually Spam.

```text
Predicted → Spam
Actual    → Spam
```

### TN — True Negative

The model predicted Not Spam and the email was actually Not Spam.

```text
Predicted → Not Spam
Actual    → Not Spam
```

### FP — False Positive

The model predicted Spam, but the email was actually legitimate.

```text
Predicted → Spam
Actual    → Not Spam
```

This could be a problem because a legitimate email may incorrectly end up in the spam folder.

### FN — False Negative

The model predicted Not Spam, but the email was actually Spam.

```text
Predicted → Not Spam
Actual    → Spam
```

This could allow unwanted emails into the user's inbox.

---

# 📐 Classification Metrics

## Accuracy

Accuracy tells us the percentage of predictions that were correct.

```text
Accuracy =
(TP + TN) / (TP + TN + FP + FN)
```

It can be useful when the classes are reasonably balanced.

However, accuracy alone may not always be enough.

---

## Precision

Precision answers:

> "Of all the emails the model predicted as Spam, how many were actually Spam?"

```text
Precision =
TP / (TP + FP)
```

High precision means fewer legitimate emails are incorrectly marked as spam.

---

## Recall

Recall answers:

> "Of all the actual Spam emails, how many did the model successfully detect?"

```text
Recall =
TP / (TP + FN)
```

High recall means fewer spam emails are missed.

---

## F1 Score

F1 Score combines Precision and Recall.

```text
F1 =
2 × (Precision × Recall)
------------------------
   Precision + Recall
```

It is useful when we want a balance between precision and recall.

---

# 🎯 Why Metrics Matter

Consider two spam detection models.

### Model A

```text
Precision = 98%
Recall    = 60%
```

This model rarely marks legitimate emails as spam, but it misses many spam emails.

### Model B

```text
Precision = 85%
Recall    = 95%
```

This model catches most spam but incorrectly marks more legitimate emails as spam.

Which model is better?

There is no universal answer.

It depends on the **business objective**.

This is an important Machine Learning lesson:

> **The best metric depends on the problem, not simply on the algorithm.**

---

# 🏗️ Project Structure

```text
03_logistic_regression/
│
├── README.md
├── main.py
├── notebook.ipynb
├── requirements.txt
│
├── data/
│   └── ...
│
└── output/
    └── ...
```

### `main.py`

The command-line implementation of the complete ML workflow.

It covers:

```text
Load Data
   ↓
Prepare Data
   ↓
Train/Test Split
   ↓
TF-IDF
   ↓
Logistic Regression
   ↓
Predictions
   ↓
Evaluation
```

### `notebook.ipynb`

The interactive learning version.

The notebook explains each step using Markdown and Python code.

### `data/`

Contains the dataset used for spam detection.

### `output/`

Contains generated outputs such as evaluation results.

### `requirements.txt`

Contains the Python dependencies required to run the project.

---

# 🚀 How to Run

## 1. Clone the Repository

```bash
git clone https://github.com/build-with-shivam/machine-learning-from-scratch.git
```

Navigate to the project:

```bash
cd machine-learning-from-scratch/03_logistic_regression
```

---

## 2. Create a Virtual Environment

```bash
python -m venv .venv
```

Activate it.

### macOS / Linux

```bash
source .venv/bin/activate
```

### Windows

```powershell
.venv\Scripts\activate
```

---

## 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## 4. Run the Project

```bash
python main.py
```

---

## 5. Run the Notebook

Start Jupyter:

```bash
jupyter notebook
```

Then open:

```text
notebook.ipynb
```

---

# 🧩 Key Learning

This project demonstrates an important distinction in Machine Learning.

### Algorithm

```text
Logistic Regression
```

### Problem Type

```text
Classification
```

### Input

```text
Email Text
```

### Feature Engineering

```text
TF-IDF
```

### Output

```text
Spam / Not Spam
```

### Evaluation

```text
Confusion Matrix
Accuracy
Precision
Recall
F1 Score
```

These concepts are related, but they are **not interchangeable**.

For example:

```text
RMSE
↓
Regression evaluation metric

Confusion Matrix
↓
Classification evaluation tool

Logistic Regression
↓
Classification algorithm
```

The metric we choose depends primarily on **what problem we are solving and what type of mistakes matter**.

---

# 🧠 What I Learned From This Project

By completing this project, we should understand:

* What classification means
* What binary classification means
* Why Logistic Regression can be used for classification
* Why text needs to be converted into numerical features
* What TF-IDF does
* What training and testing data mean
* How a classification model makes predictions
* What a confusion matrix represents
* Difference between TP, TN, FP and FN
* Accuracy vs Precision vs Recall
* What F1 Score represents
* Why evaluation metrics depend on the problem

---

# 🔜 What's Next?

The next project in the series is:

## 🌳 04 — Decision Trees

We will move from a linear classification model to a **tree-based model** and understand how a Decision Tree makes decisions.

The learning path continues:

```text
Linear Regression
      ↓
Logistic Regression
      ↓
Decision Trees
      ↓
Random Forest
      ↓
Choosing the Right ML Algorithm
```

---

# 📚 Machine Learning From Scratch

This project is part of the **Machine Learning From Scratch** series, where the goal is to learn Machine Learning progressively through:

```text
Concepts
   ↓
Python
   ↓
Experiments
   ↓
Mini Projects
   ↓
ML Engineering
   ↓
MLOps
   ↓
GenAI
```

Repository:

https://github.com/build-with-shivam/machine-learning-from-scratch.git
