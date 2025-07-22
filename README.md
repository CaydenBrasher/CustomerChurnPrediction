#Customer Churn Prediction

This project demonstrates how to predict customer churn using a trained machine learning model, handling categorical variables via saved encoders.

#Overview

The pipeline takes customer data as input, processes categorical features using pre-trained label encoders, and predicts whether the customer is likely to churn using a saved classification model.

#How It Works

Input Data: New customer data is collected in a dictionary format, then converted to a pandas DataFrame. Load Encoders: Previously trained LabelEncoder objects for categorical columns are loaded from encoders.pkl. These encoders transform string categorical data into numerical labels that the model can understand. Encode Input: The script iterates over all categorical columns in the input DataFrame and applies the corresponding encoder to transform each column from strings (e.g., 'Female', 'Yes', 'No') into numeric values. Load Model: A pre-trained machine learning model (e.g., Random Forest) is loaded (typically with pickle or joblib). Prediction: The fully numeric and encoded input data is fed into the loaded model to generate churn predictions and associated probabilities. Output: The prediction and prediction probability are printed, indicating whether the customer is predicted to churn. Important Notes

All categorical columns must have matching encoders saved during training. If a column is missing an encoder, its values will remain strings and cause errors during prediction. Input values for categorical columns must be within the known categories seen during training. Otherwise, encoding will fail. This example uses Label Encoding for categorical variables. For more robustness, consider using pipelines with OneHotEncoder(handle_unknown='ignore'). Best practice is to save and load an entire scikit-learn pipeline that encapsulates both preprocessing and the model. How to Use

Prepare input data as a dictionary with all required columns. Run the prediction script to: Load encoders and model from disk (encoders.pkl and model file). Encode categorical input features. Predict churn. Review printed prediction and probability. Example Input

input_data = { 'gender': 'Female', 'SeniorCitizen': 0, 'Partner': 'Yes', 'Dependents': 'No', 'tenure': 1, 'PhoneService': 'No', 'MultipleLines': 'No phone service', 'InternetService': 'DSL', 'OnlineSecurity': 'No', 'OnlineBackup': 'Yes', 'DeviceProtection': 'No', 'TechSupport': 'No', 'StreamingTV': 'No', 'StreamingMovies': 'No', 'Contract': 'Month-to-month', 'PaperlessBilling': 'Yes', 'PaymentMethod': 'Electronic check', 'MonthlyCharges': 29.85, 'TotalCharges': 29.85 } Requirements

Python 3.x pandas scikit-learn pickle (built-in) Install packages via:

pip install pandas scikit-learn
