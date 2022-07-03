## Heart Disease Classification

This notebook takes a look at the the data pertaining to heart attributes of various people and analyzes it to predict whether a person has a heart disease or not.

The approach this project takes : 

* Problem Definition
* Getting the data ready
* Exploratory Data Analysis
* Model Selection/Evaluation
* Features
* Experimentation

### Problem Definition

In a statement,
> "Given clinical data about a patient,can we predict whether or not they have a heart disease?"

### Getting Data Ready

For this project we will be using the UCI Heart disease dataset that can be found at heart-disease-dataset and https://archive.ics.uci.edu/ml/datasets/heart+disease

It is also available at https://www.kaggle.com/datasets/johnsmith88/


#### Data Dictionary

* age - age in years
* sex - (1 = male; 0 = female)
* cp - chest pain type
* trestbps - resting blood pressure (in mm Hg on admission to the hospital)
* chol - serum cholestrol in mg/dl
* fbs - (fasting blood sugar &gt 120 mg/dl) (1 = true; 0 = false)
* restecg - resting electrocardiographic results
* thalach - maximum heart rate achieved
* exang - exercise induced angina(1 = yes; 0 = no)
* oldpeak - ST depression induced by exercise relative to rest
* slope - the slope of the peak exercise ST segment
* ca - number of major vessels (0-3) colored by fluorosopy
* thal - 1 = normal; 2 = fixed defect; 3 = reversable defect
* target - presence of heart disease in the patient. It is integer valued 0 = no disease and 1 = disease.

> Since Data has no missing values and is already in the numerical form, we can move  on to Exploratory Data Analysis

### Exploratory Data Analysis

Making observations by analysing the data using various tools.

#### Libraries Used

* pandas
* matplotlib
* numpy

#### Observation 1:

Out of 303 records, It was found that 165 patients had a heart disease. That is a approximately **54.46%** of the total records.

 ![Heart Disease Value Counts](Target%20Value%20Counts.png)


 #### Observation 2:

 * 72 out of 96 women have a heart disease **i.e 75%** of women show signs of heart disease.

* 93 out of 207 men have a heart disease **i.e 44.93%** of men show sgins of heart disease

![target vs sex](https://user-images.githubusercontent.com/76565276/177000643-fe522790-b02c-4659-8a1b-b4547ef9a1ec.png)


#### Observation 3:

Upon analysing age distribution data, it is found that there are no outliers in the dataset.

![Age Distribution](age%20distribution.png)

#### Observation 4:

People with cp(chest pain type) = 2 have the highest chances of succumbing to heart diseases.

![Heart Disease Frequency VS Chest Pain Type](Heart%20Disease%20Frequency%20by%20chest%20pain%20type.png)



### Model Selection/Evaluation

#### Libraries Used

* sklearn


We're going to try three different models for this classification problem and evaluate them to see which one gives us the best result. They are:

1. Logistic Regression
2. K-Nearest Neighbours
3. Random Forest Classifier

#### Baseline Scores

1. Logistic Regression : **88.52%**
2. Random Forest Classifier : **83.60%**
3. K-Nearest Neighbours : **68.85%**

#### Tuning KNN Model

 Even after tuning the n-neighbors hyperparameter, KNN only gave a maximum score of **75.41%**

 ![KNN Max Score](knn%20max%20score.png)

#### Tuning Logistic Regression and Random Forest Classifier models using RandomizedSearchCV

After using RandomizedSearchCV:

1. The Logistic Regression model performed the same with a score of **88.52%**
2. The Random Forest Classifier showed a slight improvement with a score of **86.89%**


#### Hyperparameter Tuning Using GridSearchCV

Since the Logistic Regression has given us the best results so far, we will be performing the GridSearchCV only on this model.

* After performing the GridSearchCV, the Logistic Regression model gives the same result as the baseline score i.e. **88.52%**


> Therefore Logistic Regression is the model of our choice


### Model Evaluation

#### Plotting the ROC Curve

The Receiver Operating Characteristic(ROC) was plotted and Area Under Curve(AUC) was **92%**

![ROC Curve](roc%20curve.png)


#### Confusion Matrix

![Confusion Matrix](confusion%20matrix.png)

#### Cross Validated Accuracy, Precision, Recall,F1-Score 

Upon Cross Validation : 

1. Accuracy : **84.80%**
2. Precision : **82.16%**
3. Recall : **92.73%**
4. f1-score : **87.05%**

![Cross Validated Classification Report](cross%20validated%20classification%20report.png)