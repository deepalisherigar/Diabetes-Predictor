# Diabetes Predictor

A machine learning system that predicts diabetes risk from basic clinical health data, deployed as an interactive Flask web application. Users enter patient attributes like glucose level, BMI, and age, and get an instant prediction with a probability score.

## Overview

This was built as a mini project for Data Science and Machine Learning (AM1602-1) at NMAM Institute of Technology, under the Department of Artificial Intelligence and Machine Learning.

**Submitted by:**
- Deepali Sherigar
- Depatment of AIML
- NMAM Institute of Technology

## Problem Statement

Build a machine learning system to predict diabetes risk from basic health data, enabling early and easy detection for users and doctors.

## Objectives

- Build an ML-based system to predict diabetes using preprocessing and a Random Forest classifier; evaluate and save the model for reliable results.
- Use supervised learning on real health data with feature selection and validation, and analyze performance metrics.
- Create a Flask app for real-time diabetes prediction that takes user input, shows results, and logs prediction history.

## Dataset

The project uses the publicly available [Pima Indians Diabetes dataset](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database), which includes clinical features such as:

- Pregnancies
- Glucose
- Blood Pressure
- Skin Thickness
- Insulin
- BMI
- Diabetes Pedigree Function (DPF)
- Age
- Outcome (diabetic / non-diabetic — the target variable)

## Methodology

1. **Data Collection** — Load the Pima Indians Diabetes dataset and check for formatting/data errors.
2. **Feature Selection & Preprocessing** — Drop the target column from features, scale numeric features with `StandardScaler`, and split into train/test sets (80:20) stratified on the outcome.
3. **Model Development** — Train a `RandomForestClassifier` (200 estimators, max depth 10) on the scaled training data.
4. **Model Evaluation & Validation** — Assess performance using accuracy, a confusion matrix, and a classification report on the held-out test set.
5. **Web Application Deployment** — Serve the trained model through a Flask app that accepts patient inputs, preprocesses them, and returns a prediction with probability.
6. **Prediction Logging & History Analysis** — Append each prediction and its inputs to a CSV file for later review.
7. **Extensibility & Future Improvements** — Codebase structured to support swapping in more advanced models (e.g., gradient boosting, neural networks) and additional features.

## Tech Stack

- **Python** — core language
- **pandas / NumPy** — data loading and manipulation
- **scikit-learn** — `StandardScaler`, `train_test_split`, `RandomForestClassifier`, evaluation metrics
- **pickle** — saving/loading the trained model and scaler
- **Flask** — web application framework for real-time predictions

## Project Structure

```
diabetes-predictor/
├── diabetes.csv              # Pima Indians Diabetes dataset
├── train_model.py            # Data loading, preprocessing, training, evaluation, saving
├── app.py                    # Flask application (routes, prediction logic)
├── templates/
│   └── index.html            # Web UI for entering patient data and viewing results
├── model.pkl                 # Saved trained Random Forest model
├── scaler.pkl                # Saved StandardScaler
└── predictions_history.csv   # Auto-generated log of past predictions
```

## Getting Started

### Prerequisites

- Python 3.x
- Install dependencies:

```bash
pip install numpy pandas scikit-learn flask
```

### 1. Train the Model

Place `diabetes.csv` in the project folder, then run:

```bash
python train_model.py
```

This preprocesses the data, trains the Random Forest classifier, prints evaluation metrics (accuracy, confusion matrix, classification report), and saves `model.pkl` and `scaler.pkl`.

### 2. Run the Web App

```bash
python app.py
```

Then open your browser to `http://127.0.0.1:5000/`.

## Usage

1. On the home page, enter patient details: Pregnancies, Glucose, Blood Pressure, Skin Thickness, Insulin, BMI, Diabetes Pedigree Function, and Age.
2. Click **Predict**.
3. View the result — **Diabetic** or **Not Diabetic** — along with the predicted probability and a summary of the entered inputs.
4. Each prediction is automatically appended to `predictions_history.csv` for later review.

## Results

- The Random Forest classifier achieved prediction accuracy often exceeding 80–91%, depending on preprocessing and feature selection.
- Glucose, BMI, and age emerged as the top predictor variables, aligning with known clinical risk factors.
- Cross-validation and train/test evaluation confirmed stable generalization to unseen data, with balanced sensitivity and specificity.
- Prediction logging enabled consistent tracking of outcomes and probabilities across multiple sessions.

### Known Limitations

- Predictive performance depends on dataset quality, diversity, and missing values in certain fields (e.g., skin thickness, insulin).
- Broader applicability would benefit from additional clinical features, more advanced algorithms, or better-balanced training data.

## Future Enhancements

- Integrate more advanced models such as gradient boosting or neural networks.
- Expand the feature set and incorporate larger, more diverse datasets.
- Improve UI/UX and add richer visualizations of prediction history.

## References

1. [Pima Indians Diabetes Dataset (Kaggle)](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database)
2. [scikit-learn Documentation](https://scikit-learn.org/stable/documentation.html)
3. [NumPy Documentation](https://numpy.org/doc/)
4. [pandas Documentation](https://pandas.pydata.org/docs/)
5. [Flask Documentation](https://flask.palletsprojects.com/en/3.0.x/)
6. [Python Documentation](https://www.python.org/doc/)

## Disclaimer

This tool is built for educational purposes as part of an academic mini project. It is not a substitute for professional medical diagnosis — predictions should not be used for actual clinical decision-making without validation by qualified healthcare professionals.
