# 🎓 Student Performance Analysis

A machine learning web application that predicts a student's **math score** based on demographic and academic factors. The project follows a modular, production-ready ML pipeline architecture with data ingestion, transformation, model training, and a Flask-based prediction interface.

---

## 📌 Problem Statement

Student academic outcomes are influenced by a variety of socio-demographic and preparation factors. This project builds a regression model to predict math scores using features such as gender, race/ethnicity, parental education, lunch type, test preparation course completion, reading score, and writing score.

---

## 🗂️ Project Structure

```
Student_Performance_Analysis/
│
├── app.py                        # Flask web application
├── setup.py                      # Package setup
├── requirements.txt              # Project dependencies
│
├── artifacts/                    # Saved model and preprocessor artifacts
│   ├── model.pkl
│   ├── preprocessor.pkl
│   ├── train.csv
│   └── test.csv
│
├── notebook/                     # Exploratory Data Analysis notebooks
│
├── src/
│   ├── components/
│   │   ├── data_ingestion.py       # Data loading and train/test split
│   │   ├── data_transformation.py  # Feature engineering and preprocessing
│   │   └── model_trainer.py        # Model selection and training
│   │
│   ├── pipeline/
│   │   └── predict_pipline.py      # Prediction pipeline
│   │
│   ├── exception.py              # Custom exception handling
│   ├── logger.py                 # Logging configuration
│   └── utils.py                  # Utility functions
│
└── templates/                    # HTML templates for Flask UI
    ├── index.html
    └── home.html
```

---

## ✨ Features

- **End-to-end ML pipeline**: Covers data ingestion → transformation → model training → prediction
- **Multi-model evaluation**: Trains and compares 7 regression algorithms with hyperparameter tuning
- **Automated best model selection**: Selects the model with highest R² score (threshold ≥ 0.6)
- **Interactive web UI**: Flask-based form to input student data and get math score predictions
- **Modular codebase**: Clean separation of components with custom logging and exception handling
- **Artifact persistence**: Trained model and preprocessor saved as `.pkl` files for reuse

---

## 🤖 Models Evaluated

| Model | Hyperparameter Tuning |
|---|---|
| Linear Regression | — |
| Decision Tree Regressor | `criterion` |
| Random Forest Regressor | `n_estimators` |
| Gradient Boosting Regressor | `learning_rate`, `subsample`, `n_estimators` |
| XGBoost Regressor | `learning_rate`, `n_estimators` |
| CatBoost Regressor | `depth`, `learning_rate`, `iterations` |
| AdaBoost Regressor | `learning_rate`, `n_estimators` |

The best-performing model is automatically selected via **GridSearchCV** and evaluated using the **R² score**.

---

## 📊 Input Features

| Feature | Type | Description |
|---|---|---|
| `gender` | Categorical | Student gender |
| `race_ethnicity` | Categorical | Race/ethnicity group |
| `parental_level_of_education` | Categorical | Highest parental education level |
| `lunch` | Categorical | Standard or free/reduced lunch |
| `test_preparation_course` | Categorical | Completed or none |
| `reading_score` | Numerical | Score in reading (0–100) |
| `writing_score` | Numerical | Score in writing (0–100) |

**Target variable:** `math_score` (continuous, 0–100)

---

## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- pip

### Installation

```bash
# Clone the repository
git clone https://github.com/Somesh-Salunkhe/Student_Performance_Analysis.git
cd Student_Performance_Analysis

# Create and activate a virtual environment (optional but recommended)
python -m venv venv
source venv/bin/activate   # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Train the Pipeline

Run the data ingestion component to trigger the full training pipeline:

```bash
python src/components/data_ingestion.py
```

This will:
1. Load and split the dataset into train/test sets
2. Apply preprocessing (imputation, one-hot encoding, scaling)
3. Train and evaluate all models
4. Save the best model and preprocessor to `artifacts/`

### Launch the Web App

```bash
python app.py
```

Open your browser and navigate to `http://127.0.0.1:5000/`. Fill in the student details on the form and click **Predict** to get the estimated math score.

---

## 🛠️ Tech Stack

- **Python** — Core language
- **scikit-learn** — ML models, preprocessing pipelines, GridSearchCV
- **XGBoost** — Gradient boosted trees
- **CatBoost** — Categorical feature-friendly boosting
- **Flask** — Web application framework
- **Pandas / NumPy** — Data manipulation
- **Seaborn** — Exploratory data analysis and visualization
- **Dill** — Object serialization for pipeline artifacts

---

## 📁 Artifacts

After training, the following files are saved in the `artifacts/` directory:

- `model.pkl` — Best trained regression model
- `preprocessor.pkl` — Fitted preprocessing pipeline (imputer + encoder + scaler)
- `train.csv` / `test.csv` — Processed train/test data splits

---

## 👤 Author

**Somesh Salunkhe**  
