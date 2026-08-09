# 🏠 House Price Prediction Using Linear Regression

> Build your first Machine Learning model by predicting house prices using Linear Regression and the California Housing Dataset.

This project is part of the **Machine Learning From Scratch** series, where we learn Machine Learning by combining theory with hands-on Python implementation.

---

# 🎯 Objective

The goal of this project is to predict house prices based on various housing-related features using the **Linear Regression** algorithm.

By the end of this project, you will understand how to:

- Load a real-world dataset
- Explore and understand the data
- Split the dataset into training and testing sets
- Train a Linear Regression model
- Make predictions
- Evaluate model performance
- Visualize the results

---

# 📚 What is Linear Regression?

Linear Regression is one of the simplest and most widely used Machine Learning algorithms.

It tries to find the **best-fit line** that describes the relationship between the input features (**X**) and the target value (**Y**).

The model learns this relationship from historical data and uses it to predict values for unseen data.

---

# 🌍 Real-World Applications

Linear Regression is commonly used for:

- 🏠 House Price Prediction
- 💰 Salary Prediction
- 📈 Sales Forecasting
- 🌡️ Temperature Forecasting
- ⚡ Energy Consumption Prediction
- 🚗 Used Car Price Estimation

---

# 📊 Dataset

This project uses the **California Housing Dataset** provided by **Scikit-learn**.

The dataset contains housing information collected from different districts in California.

### Features

| Feature | Description |
|----------|-------------|
| MedInc | Median income |
| HouseAge | Average house age |
| AveRooms | Average number of rooms |
| AveBedrms | Average bedrooms |
| Population | Population in the block |
| AveOccup | Average occupants |
| Latitude | Latitude |
| Longitude | Longitude |

### Target

The target variable is:

> **Median House Value**

---

# 🔄 Machine Learning Workflow

```
Load Dataset
      │
      ▼
Explore Data
      │
      ▼
Train-Test Split
      │
      ▼
Train Linear Regression Model
      │
      ▼
Predict House Prices
      │
      ▼
Evaluate Model
      │
      ▼
Visualize Results
```

---

# 📂 Project Structure

```
02_linear_regression/
│
├── README.md
├── main.py
├── notebook.ipynb
├── requirements.txt
│
├── output/
│   ├── actual_vs_predicted.png
│   └── model_metrics.txt
│
└── images/
```

---

# 🛠 Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn

---

# 🚀 Getting Started

Clone the repository

```bash
git clone https://github.com/build-with-shivam/machine-learning-from-scratch.git
```

Navigate to the project

```bash
cd machine-learning-from-scratch/day-02-linear-regression
```

Install dependencies

```bash
pip install -r requirements.txt
```

Run the project

```bash
python main.py
```

---

# 📈 Expected Output

The program will:

- Load the California Housing dataset
- Train a Linear Regression model
- Predict house prices
- Display evaluation metrics
- Generate a comparison graph between actual and predicted prices

---

# 📊 Model Evaluation

The following metrics will be used to evaluate the model:

## Mean Absolute Error (MAE)

Average absolute difference between actual and predicted values.

Lower is better.

---

## Mean Squared Error (MSE)

Average squared prediction error.

Penalizes larger errors more heavily.

Lower is better.

---

## Root Mean Squared Error (RMSE)

The square root of MSE.

Easy to interpret because it uses the same unit as the target variable.

Lower is better.

---

## R² Score (Coefficient of Determination)

Measures how well the model explains the variance in the data.

- **1.0** → Perfect prediction
- **0.0** → No predictive power

Higher is better.

---

# 📷 Output

The project generates:

```
output/
├── actual_vs_predicted.png
├── residual_plot.png
└── model_metrics.txt
```

---

# 🧠 What You'll Learn

After completing this project, you'll understand:

- Regression problems
- Feature variables
- Target variables
- Train/Test Split
- Model Training
- Predictions
- Evaluation Metrics
- Data Visualization

---

# 💼 FAQs

### Why do we split the dataset?

To evaluate how well the model performs on unseen data and avoid overfitting.

---

### Why use Linear Regression?

It is simple, interpretable, and works well when there is a linear relationship between the input features and the target variable.

---

### What is overfitting?

Overfitting occurs when a model memorizes the training data instead of learning general patterns, resulting in poor performance on new data.

---

### What is underfitting?

Underfitting happens when the model is too simple to capture the underlying relationship in the data.

---

# 📖 Next Lesson

➡️ **Logistic Regression — Predicting Spam Emails**

---

# 🤝 Contributing

Contributions are welcome!

If you'd like to improve this project:

- Fork the repository
- Create a new branch
- Submit a Pull Request

---

# ⭐ Support

If you found this project helpful:

⭐ Star this repository

🍴 Fork it

📢 Share it with others

---

## 📬 Connect

Follow my **Machine Learning From Scratch** series on LinkedIn for detailed explanations, visual guides, and hands-on Python implementations.

Happy Learning! 🚀