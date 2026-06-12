Titanic Survival Prediction using Machine Learning

Project Overview

This project predicts whether a passenger survived the Titanic disaster using Machine Learning. The goal was not only to build a predictive model but also to understand the complete Machine Learning workflow, including data preprocessing, model evaluation, feature scaling, cross-validation, hyperparameter tuning, model persistence, and prediction on new data.

The project was developed using Python and Scikit-learn, with Logistic Regression as the primary classification algorithm.

---

Problem Statement

Given passenger information such as:

- Passenger Class (Pclass)
- Gender (Sex)
- Age
- Number of Siblings/Spouses (SibSp)
- Number of Parents/Children (Parch)
- Fare
- Embarkation Port

predict whether the passenger survived the Titanic disaster.

Target Variable:

- 0 → Did Not Survive
- 1 → Survived

---

Dataset

The project uses the Titanic Dataset containing passenger information and survival status.

Features used:

Feature| Description
Pclass| Passenger Class
Sex| Gender
Age| Passenger Age
SibSp| Number of Siblings/Spouses
Parch| Number of Parents/Children
Fare| Ticket Fare
C| Embarked at Cherbourg
Q| Embarked at Queenstown
S| Embarked at Southampton

Target:

- Survived

---

Project Workflow

1. Data Loading

The dataset was loaded using Pandas and inspected for understanding its structure.

2. Data Preprocessing

The following preprocessing steps were performed:

- Handling missing values
- Encoding categorical features
- One-hot encoding for embarkation ports
- Preparing features and target variable

3. Train-Test Split

The dataset was divided into:

- Training Data (80%)
- Testing Data (20%)

This ensures that model performance is evaluated on unseen data.

4. Logistic Regression Model

A Logistic Regression classifier was trained on the training dataset.

5. Model Evaluation

The model was evaluated using multiple metrics:

Accuracy

Measures overall correctness of predictions.

Accuracy achieved:

- ~80%

Confusion Matrix

Used to analyze:

- True Positives (TP)
- True Negatives (TN)
- False Positives (FP)
- False Negatives (FN)

Precision

Measures how many positive predictions were actually correct.

Recall

Measures how many actual positive cases were correctly identified.

F1 Score

Provides a balance between Precision and Recall.

---

Feature Importance Analysis

Logistic Regression coefficients were analyzed to understand feature influence on survival prediction.

Observations:

- Gender showed strong influence on survival.
- Passenger class also contributed significantly.
- Some features had relatively smaller impact.

---

Feature Scaling

StandardScaler was applied to normalize feature values.

Benefits:

- Faster optimization
- Better convergence
- Comparable feature scales
- More stable model training

---

Cross Validation

5-Fold Cross Validation was used to evaluate model stability.

Purpose:

- Verify that model performance is not dependent on a single train-test split.
- Check whether the model generalizes consistently.

Average Cross Validation Score:

- ~79%

---

Hyperparameter Tuning

GridSearchCV was used to search for the best Logistic Regression hyperparameters.

Parameters tested:

- C = [0.01, 0.1, 1, 10]
- max_iter = [100, 500, 1000]

Best Parameters:

{
    'C': 0.01,
    'max_iter': 100
}

Best Cross Validation Score:

80.05%

---

Final Model Training

The final Logistic Regression model was trained using the best hyperparameters discovered through GridSearchCV.

Final Test Accuracy:

79.89%

The close relationship between Cross Validation score and Test Accuracy indicates good generalization with minimal overfitting.

---

Model Persistence

The trained model and scaler were saved using Joblib.

Files generated:

titanic_model.pkl
scaler.pkl

Why save both?

- The model was trained on scaled data.
- New input data must be transformed using the same scaler before prediction.

---

Loading Saved Model

The saved model and scaler were loaded using:

joblib.load()

This allows predictions without retraining the model.

---

Prediction on New Passenger Data

A new passenger record was created and passed through:

New Passenger Data
        ↓
StandardScaler
        ↓
Logistic Regression Model
        ↓
Prediction

Example Output:

array([0])

Meaning:

Passenger Predicted: Did Not Survive

---

Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Joblib
- Jupyter Notebook

---

Key Concepts Demonstrated

- Data Preprocessing
- Feature Engineering
- Logistic Regression
- Classification Metrics
- Confusion Matrix
- Precision, Recall, F1 Score
- Feature Scaling
- Cross Validation
- Hyperparameter Tuning
- Model Serialization
- Machine Learning Pipeline

---

Future Improvements

Potential enhancements include:

- Decision Tree Classifier
- Random Forest Classifier
- XGBoost
- Model Deployment using Flask or FastAPI
- Web-based Prediction Interface
- Cloud Deployment

---

Conclusion

This project demonstrates a complete end-to-end Machine Learning workflow for binary classification. Starting from raw Titanic passenger data, the project covers preprocessing, model training, evaluation, optimization, model saving, and prediction on unseen data. The final Logistic Regression model achieved approximately 80% accuracy while maintaining good generalization across unseen data.