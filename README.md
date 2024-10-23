# Stroke Prediction Dataset Analysis and Machine Learning Modelling Introduction

Stroke is one of the leading causes of death and disability worldwide. Predicting stroke occurrence based on various risk factors can help in early intervention and treatment. This report details the steps involved in Exploratory Data Analysis (EDA), data preprocessing, visualization, and machine learning modeling using the stroke prediction dataset.

## Dataset Overview:

The dataset includes various features such as demographic information, health conditions, lifestyle factors, and a target variable (stroke) indicating whether a person had a stroke (1) or not (0).

## 1. Features:

    • Numerical: age, avg_glucose_level, bmi
    • Categorical: gender, hypertension, heart_disease, ever_married, work_type, Residenc
    e_type, smoking_status, stroke

## 2. Data Preprocessing:

    * Several preprocessing steps were performed:

    • Handling Missing Values: The bmi column had missing values, which were imputed
    with the median value.
    • Removing Duplicates: The duplicate records were removed to ensure data integrity.
    • Outlier Transformation: bmi and avg_glucose_level were transformed using log
    normalization (log(x+1)) to handle skewness and normalize the distributions.

## 3. Exploratory Data Analysis and Visualization

    * Numerical Feature Visualization:

    • Kernel Density Estimate (KDE) and Box Plots were used to visualize the
    distributions and outliers of numerical features (age, bmi, avg_glucose_level),
    comparing stroke and non-stroke groups.
    • Scatter Plots were drawn to assess the relationship between these numerical
    features and the target variable stroke.

    * Categorical Feature Visualization:

    • Count Plots for categorical variables like gender hypertension, heart_disease,
    ever_married, work_type and smoking_status were generated to understand the distribution of the data and how these factors influence the occurrence of strokes.

    * Target Distribution:

    • A Pie Chart was used to illustrate the imbalanced nature of the dataset, with a
    significant majority of the samples belonging to the stroke=0 class (people who did not have a stroke).
     
## 4. Data Encoding and Scaling:

    * To prepare the data for modeling:

    • Label Encoding: Categorical variables were converted to numerical values using LabelEncoder.
    • Feature Scaling: MinMaxScaler was applied to ensure that all features are on the same scale, which is especially important for distance-based algorithms like K-Nearest Neighbors (KNN).

## 5. Machine Learning Modeling:

    * Decision Tree Classifier (Before Handling Imbalance):

    A Decision Tree Classifier was trained using a 75-25 train-test split. The model provided an accuracy score of 95%. However, due to the highly imbalanced dataset, the recall for the minority class (stroke=1) was zero, indicating that the model struggled to identify stroke cases accurately.

## 6. Imbalanced Data Handling

    To address the class imbalance,Synthetic Minority Over-sampling Technique (SMOTE) was applied, balancing the dataset by generating synthetic samples for the minority class (stroke=1). This ensures that the model can better learn the patterns associated with stroke cases.

    * After applying SMOTE:

    • Class Distribution: A bar plot was used to visualize the distribution of the stroke class
    before and after applying SMOTE, showing a more balanced dataset.
    Modeling on Resampled Data
    With the balanced dataset, two models were trained: Decision Tree and K-Nearest Neighbors (KNN).

    * Decision Tree Classifier (After SMOTE)
    The Decision Tree was retrained on the resampled data. Key results:
    • Accuracy: 77%
    • Recall: 90% - Significant improvement in identifying stroke cases (stroke=1).

    * K-Nearest Neighbors (KNN)
    The KNN model outperformed the Decision Tree:
    • Accuracy: 87.2%
    • Recall: 96% - Better identification of stroke cases after resampling.

## Conclusion:

The initial analysis using a Decision Tree model showed strong accuracy, but failed to correctly identify stroke cases due to the imbalanced nature of the data. After applying SMOTE, both Decision Tree and KNN models showed improvements in recall, with KNN providing the best results in terms of both accuracy and recall, making it a better fit for this problem.