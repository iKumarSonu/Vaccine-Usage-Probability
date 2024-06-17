# Vaccine-Usage-Probability
Predict how likely individuals are to receive their xyz and seasonal flu vaccines.

This Python pipeline uses logistic regression models (model_xyz and model_seasonal) to predict vaccine uptake based on demographic and attitudinal features. Here’s a concise overview of its components and functionality:

Data Handling and Preparation:
The pipeline starts by loading training data (train_features.csv and training_set_labels.csv) and merging them to form train_df. Test data (test_features.csv) is also loaded for prediction.

Preprocessing:

Numerical Features: numeric_transformer uses SimpleImputer to handle missing values by replacing them with the median, followed by StandardScaler to standardize features.

Categorical Features: categorical_transformer fills missing values with the most frequent category using SimpleImputer and encodes categorical variables with OneHotEncoder for logistic regression.

ColumnTransformer: preprocessor combines numeric_transformer and categorical_transformer, ensuring consistent preprocessing across different feature types.

Model Definition and Training:

Logistic Regression Models: model_xyz and model_seasonal are constructed as Pipeline objects incorporating preprocessor and logistic regression classifiers (LogisticRegression). They are trained on X_train with respective target variables (y_train_xyz and y_train_seasonal).
Prediction and Submission:

Probability Prediction: Using predict_proba(), probabilities of vaccine acceptance are computed for the test set (X_test).

Submission Creation: Predicted probabilities (xyz_vaccine_probs and seasonal_vaccine_probs) are organized into submission_df, containing respondent_id, xyz_vaccine, and seasonal_vaccine probabilities.

CSV Export: Results are exported to vaccine_predictions.csv, facilitating further analysis and evaluation.

Conclusion:
This pipeline integrates robust preprocessing steps and logistic regression models to predict vaccine acceptance probabilities. It addresses data challenges through comprehensive handling of missing values and categorical encoding, ensuring models are trained on clean, standardized data. By leveraging logistic regression’s interpretability, the pipeline provides actionable insights into factors influencing vaccine uptake, supporting informed decision-making in public health strategies.
