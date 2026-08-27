## Skin Disease Multiclass Classification

## Project Overview

This project builds a machine-learning model to classify six skin disease classes using clinical and histopathological features.

The project includes:

* Exploratory Data Analysis (EDA)
* Missing-value handling
* Train-test splitting with stratification
* SMOTE for class balancing
* Multiple machine-learning models
* Random Forest hyperparameter tuning
* Evaluation using Accuracy, Macro Precision, Macro Recall, Macro F1-score, Classification Report, and Confusion Matrix

**Important:** This project is intended as an educational machine-learning project and should not be used as a replacement for professional medical diagnosis.

## Problem Statement

The project addresses the following tasks:

1. Perform complete exploratory data analysis on the skin disorder dataset.
2. Build machine-learning models to classify different skin disease classes.
3. Provide recommendations for using the model as a clinical decision-support aid for early identification.

## Dataset Description 

the dataset belongs to the **health care domain** and contain dermatology dataset.

### Dataset Download

Download the dataset from:

https://d3ilbtxij3aepc.cloudfront.net/projects/CDS-Capstone-Projects/PRCP-1028-Skin-Disorder-Prediction-20220512T101734Z-001.zip

### Dataset Setup

After downloading the dataset:

1. Place the dataset inside the "data" folder.
2. Make sure the dataset file is named "dataset_35_dermatology.csv".

The dataset path should be:

"dataset_35_dermatology.csv"

## Dataset

**The dataset contains:**

- **366 observations**
- **35 columns**
- **34 predictor features**
- **1 target column: class**
- **6 skin disease classes**

The dataset contains clinical and histopathological features such as erythema, scaling, itching, scalp involvement, and other recorded variables.



## Project Workflow
```text
Data Collection
      ↓
Data Understanding
      ↓
Handling Missing Values
      ↓     
Exploratory Data Analysis
      ↓
Data Preprocessing
      ↓
Train-test-split
      ↓
Performing Scaling 
      ↓
Class Imbalance Analysis
      ↓
Model Building
      ↓
Model Evaluation
      ↓
Hyperparameter Tuning
      ↓
Comparing Accuracy Score
      ↓
Final Model Selection
      ↓
Project Conclusion
```

## Technologies Used

Python
NumPy
Pandas
Matplotlib
Seaborn
Scikit-learn
Imbalanced-learn
XGBoost
Jupyter Notebook


## Exploratory Data Analysis

The following analyses were performed:

* Dataset shape and structure analysis
* Data type inspection
* Statistical summary of numerical features
* Missing value analysis
* Duplicate value analysis
* Target class distribution analysis
* Univariate and Bivariate analysis
* Feature distribution analysis
* Correlation analysis
* Outlier exploration using boxplots



## Data Preprocessing

The preprocessing workflow includes:

* Replacing ? values with missing values.
* Converting the Age column to numeric format.
* Performing missing-value imputation.
* Splitting the data into training and testing sets using stratification.
* Applying feature scaling for models that require it.
* Applying SMOTE only to training data through imbalanced-learn pipelines.
* This based on this approach helps prevent data leakage from the test set.

## Building Machine Learning Models

The following models are used:

1. Logistic Regression
2. Random Forest
3. Decision Tree
4. Support Vector Classifier (SVC)
5. XGBoost Classifier

**Model performance was evaluated using:**

* Accuracy
* Macro Precision
* Macro Recall
* Macro F1-score
* Classification Report
* Confusion Matrix

Macro F1-score is used as the main comparison metric because it gives equal importance to every class.


## Hyperparameter Tuning

**RandomizedSearchCV** is used to tune on the **Random Forest model** using **Macro F1-score** as the cross-validation scoring metric.

Hyperparameter Tuning used on:
**Random Forest**


## Model Performance
```text
| Model                  | Accuracy | Marco Precision | Marco Recall | Marco F1 Score | 
| ---------------------: | -------: | --------------: | -----------: | -------------: |
|  Tuned Random Forest   |   0.9730 |      0.9528     |    0.9694    |     0.9588     |
|  Logistic Regression   |   0.9595 |      0.9615     |    0.9611    |     0.9574     | 
|  SVC                   |   0.9595 |      0.9545     |    0.9556    |     0.9545     |     
|  Random Forest         |   0.9459 |      0.9197     |    0.9417    |     0.9274     |   
|  Decision Tree         |   0.9324 |      0.9045     |    0.9306    |     0.9137     |     
|  XGBoost               |   0.9189 |      0.9150     |    0.9167    |     0.9104     |  
```

## Best Model

**Tuned Random Forest** was selected as the final model based on its overall performance.

The model achieved:
- **Accuracy**:0.9730
- **Marco F1 score**:0.9588
- **Marco Precision**:0.9528
- **Marco Recall**:0.9694

Although Logistic Regression has slightly higher Macro Precision (96.15%), but Tuned Random Forest has:

* Highest Accuracy → 97.30%
* Highest Macro Recall → 96.94%
* Highest Macro F1 Score → 95.88%

Since The dataset is a multiclass and imbalanced skin disease dataset, Macro F1 Score is an important metric because it gives equal importance to all disease classes.

## How to Run the Project

1. Clone or download the repository
2. Create a virtual environment (optional but recommended)
python -m venv venv

Activate it on Windows:

venv\Scripts\activate

3. Install the required libraries

pip install -r requirements.txt

4. Add the dataset

Place the CSV file at:

data/dataset_35_dermatology.csv

5. Run the notebook

Open:

Skin_Disorder_Corrected.ipynb

Run all cells from top to bottom.

## Project Structure

```text
Skin-Disorder-Classification/
│
├── Skin_Disorder_Corrected.ipynb
├── README.md
├── requirements.txt
│
└── data/
```    └── dataset_35_dermatology.csv

## Conclusion:

* The skin disease classification model successfully classified six different disease classes using machine learning techniques. 
* After hyperparameter tuning, the Random Forest model achieved a test **accuracy of 97.30%** and a cross-validation **Macro F1-score of 95.88%**. 
* The Tuned Random Forest model was selected as the best-performing model for skin disease prediction.
* It achieved the highest accuracy of 97.30% and the highest Macro F1-score of 95.81%, demonstrating better overall and balanced performance across all disease classes.

**Suggestions to Doctors for Early Identification:**

This machine-learning model should be treated as a **clinical decision-support tool**, not as a replacement for a dermatologist's diagnosis.

1. **Collect the clinical features early:** Record the patient's observed symptoms and clinical/histopathological findings represented by the dataset, such as erythema, scaling, itching, definite borders, scalp involvement and other recorded features.
2. **Use the model as an early screening aid:** Enter the patient's available feature values into the trained model to obtain a predicted disease class and use the result to support further clinical assessment.
3. **Pay attention to uncertain or borderline cases:** If the model's predicted probabilities are close across multiple classes, the case should receive additional clinical examination rather than relying on the top prediction alone.
4. **Do not ignore rare classes:** Class 6 has only 20 records in the dataset, compared with 112 records for Class 1. Doctors should therefore be particularly cautious when the model predicts a less-represented class and should confirm it clinically.
5. **Use confusion-matrix results to identify commonly confused classes:** The model evaluation should be reviewed to determine which disease classes are most frequently confused and where additional clinical checks may be useful.
6. **Confirm the prediction clinically:** A dermatologist should combine the model output with patient history, physical examination and appropriate diagnostic tests before making a final diagnosis or treatment decision.
7. **Monitor model performance over time:** If this system is deployed, performance should be periodically re-evaluated on new, clinically representative data.

## Disclaimer:

The model is an educational decision-support project. Predictions should not be treated as a final medical diagnosis. Clinical decisions should be made by qualified healthcare professionals using appropriate medical examination and diagnostic procedures.