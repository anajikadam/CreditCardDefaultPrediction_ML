# Project
The objective of this case study is to identify whcih borrowers are likely to fall in the serioud delinquency of more than 3 months in the next 2 years. The more accurate we are able to identify, the better it will be for banks to save their money and take necessary actions.

'

### Prerequisites
install python version having 3.7.x as the format else logger syntax might throw an error.

For any package installation - pip install "package_name"

'


### Data Overview
The dataset is having 150000 records or 150000 borrowers we are having in the training dataset. We will split the 80% of the data into training and the remaining 20% of the data into test.

The target variable is a binary one having 1 falling in the serious delinquency and 0 for not. There are a mized of continuous and numerical features. Missing values in the data is having only in the 2 columns, one having 20% which is the numerical feature having Monthly Income and the another one having 3% which is the categorical feature having No of Dependents.

6.7% of the customers from the entire dataset are falling in the serious delinquency which is a classical case of Class Imbalance Problem.

'

## Code Overview

1. To perform modeling on the dataset, 80% of the data is training and to check how the model is performing 20% of the data is test.
2. After having the analysis and visualization of the independent variables/features, there are few major noticeable outliers which needs to be removed to avoid fitting issues.

    2.1 Features having the count of behind due date in the emi repayment have a common pattern of outliers which are clipped.
    
    2.2 Removing the rows where data entry errors are noticeable in case of Debt Ratio and removal of rows which do not make any sense as per the description of some feature.

3. Missing value is imputed using the mean and mode as per the type of the feature.

4. Features are engineered to make a model more robust and more informative in decision making to better classify non delinquent borrowers to delinquent borrowers. For that interaction of the features are performed and binary indicators to capture yes/no behaviour.

5. To tackle class imbalance issue upsampling and synthetic samping of the minority clas along with the downsampling of the majority class is done to better train a model.

6. Feature Scaling is done so that certain models such as Neural Network and Logistic Regression which relies on features weights to minimise error.

7. For tree based models, no feature scaling is done as performance with or without feature scaling is nearly same.

8. Training of the models using NN, LR, Tree Based Models are done with few techniques to compare results which are feature scaling, tackling class imbalance issue with synthetic sampling and assigning class weights itself in the model using their hyperparameter.

9. For tree based models, hyperparameters were tuned using GridSearchCV to  have the optimal solution.

10. After doing all the kinds of modeling, it was found that Logistic Regression and NN performs when scaling of the features are done if a scale or range of features are very different from each other.  

11. Tree based models were performing the best and among them LightGBM performance was better after looking at the feature importance and other metrics. Hence, LightGBM was chosen to train the model and predict the unseen data.

12. Metrics were chosen apart from Accuracy to accurately check how the model was performing. 

13. How the model was behaving internally at a global level was checked using SHAP and at a local level was checked using LIME.

## Running the Script

All the indepent operations such as pre processing, training the model are kept in the folder name ML_pipeline and a main script name "engine.py" is used to run the entire code by calling other python scripts from the ML_pipeline folder.

syntax to run - "path_name"/src/python engine.py

Output of the script will be exported to the output folder.
