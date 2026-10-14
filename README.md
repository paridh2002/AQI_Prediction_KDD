AQI Prediction Using Machine Learning and the KDD Process

A machine-learning project that analyzes historical air-quality data from India and estimates the Air Quality Index (AQI) using pollutant measurements. The notebook follows the Knowledge Discovery in Databases (KDD) workflow, from data selection and preprocessing to model evaluation and interpretation.

Project Objective
The goal is to explore air-quality data, train regression models to estimate AQI, compare their performance, and identify features that influence model predictions.

Prediction target: AQI
Dataset file: city_day.csv
Environment: Google Colab or a local Python/Jupyter environment

Task scope: The notebook estimates same-day AQI using same-day pollutant measurements. It is not a future-day AQI forecasting system.

KDD Workflow
Data selection: Load city_day.csv and identify the available city, date, pollutant, and AQI fields.
Data preprocessing: Standardize column names, parse dates, inspect missing values, handle duplicates, and prepare rows with valid AQI targets.
Data transformation: Derive calendar features, encode city information, and impute missing predictor values within the modeling pipeline.
Data mining: Train and compare a median baseline, Linear Regression, and Random Forest regression.
Evaluation: Evaluate predictions on a chronological holdout set using MAE, RMSE, and R².
Interpretation: Review visualizations, sample predictions, residual behavior, and feature importance.
Dataset
The notebook uses the city_day.csv file from the Kaggle dataset:

Source: Air Quality Data in India — Kaggle

The dataset may include city and date fields, pollutant measurements such as PM2.5, PM10, NO₂, NOx, NH₃, CO, SO₂ and O₃, and the AQI target. The notebook checks the actual columns available when the file is loaded.

The AQI_Bucket field is excluded from model features because it is derived from AQI and could leak target information.

Please review the dataset page's licence and terms before redistributing the CSV. This repository README links to the source rather than redistributing the dataset.

Machine-Learning Models
The notebook compares:

Median baseline: A simple reference model.
Linear Regression: A linear model for estimating AQI from the selected features.
Random Forest Regressor: An ensemble of decision trees that can model nonlinear relationships.
The best model is selected using the test-set RMSE calculated when the notebook is run.

Evaluation Metrics
MAE — Mean Absolute Error: Average absolute difference between actual and predicted AQI values. Lower is better.
RMSE — Root Mean Squared Error: Penalizes larger errors more heavily. Lower is better.
R² — Coefficient of Determination: Measures performance relative to a mean-prediction baseline. Values closer to 1 generally indicate better fit; negative values are possible.
The notebook generates the evaluation table, plots, sample predictions, and feature-importance results at runtime. No fixed performance scores are listed here because they depend on the dataset and execution.

Run in Google Colab
Download AQI_Prediction_KDD_Cleaned.ipynb from this repository.
Open Google Colab.
Choose File → Upload notebook and upload the notebook.
Download city_day.csv from the Kaggle dataset page.
Run the notebook cells from top to bottom.
When the notebook requests the dataset, upload city_day.csv.
Confirm that data-loading, preprocessing, charts, model evaluation, and predictions complete without errors.
Save or download the executed notebook if you want to preserve the generated outputs.
If you see a file-not-found error, confirm that the uploaded file is named city_day.csv and that the notebook's upload/loading cell completed successfully.

Run Locally
Recommended: Python 3.10 or later.

Download or clone the repository.

Install the dependencies:

pip install -r requirements.txt
Place city_day.csv in the location expected by the notebook, or update the notebook's data-loading path.

Open the notebook in Jupyter and run the cells in order.

Repository Structure
aqi-prediction-kdd/
├── AQI_Prediction_KDD_Cleaned.ipynb
├── README.md
├── requirements.txt
└── .gitignore
The CSV dataset is obtained separately from Kaggle and is not required to be committed to the repository.

Limitations
The notebook estimates same-day AQI from same-day pollutant measurements; it does not forecast future-day AQI.
Data quality, missing values, city differences, and temporal changes may affect model performance.
The chronological holdout tests later observations from cities represented in the dataset; it does not establish performance on entirely unseen cities.
Feature importance indicates model reliance on features and does not establish causation.
Results should not be used for health, regulatory, or other high-stakes decisions without further validation.
Future Improvements
Create a true future-day forecasting task using lagged pollutant values and a forward-shifted AQI target.
Evaluate performance across multiple time periods and unseen cities.
Compare additional regression models and tune their hyperparameters.
Add monitoring for data drift and changes in model performance.
References
Kaggle — Air Quality Data in India
Pandas documentation
scikit-learn documentation
