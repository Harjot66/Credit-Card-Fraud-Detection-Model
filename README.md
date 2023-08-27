# Credit Card Fraud Detection
This is a project completed solely in python where I utilized multiple python packages to analyze hundreds of thousands of credit card transactions, some of which being fraudulent. I then used logistic regression and xgboost classification (supervised machine learning algorithms) in order to create multiple credit card fraud detection models, ultimately getting to a model which was 99.96% accurate at the testing phase.
## The Project
### Step 1 Data Exploration
In the first step of this project I explored the data, coming to a very important conclusion that the data was highly imbalanced and only had 492 fraudulent transactions compared to the 284,315 non-fraudulent transactions.
### Step 2 Logistic Regression
In step 2 of this project I went ahead and attempted to use simple logistic regression in order to help classify transactions as fraudulent and non-fraudulent. This model had a few problems however, due to the fraudulent and non-fraudulent transaction class weights not being balanced. This caused the model to miss more fraud as there were significantly more non-fraudulent transactions in the training dataset, while the weight of each fraudulent and non-fraudulent transaction remained the same. I then went ahead and balanced the weight inversly proportional to class frequencies in the input data, giving underrepresented classes a higher weight. However, this model classified significantly more non-fraudulent transactions as being fraudulent. This was due to the weighting of fraudulent transactions being too high, where the model began to classify more transactions as fraudulent. I then customized the weights to lower the weighting of fraudulent transactions. This resulted in a significant decrease in non-fraudulent transactions detected as being fraudulent. I then went ahead and calculated the Shapley values for each feature in the dataset to see which features is most influential in predicting credit card fraud. This, however was still only 99.79% accurate, and could be improved further.
### Step 3 XGBoost
In step 3 I trained a model using xgboost classification (a gradient boosted trees algorithm). This led to a significantly more accurate result in detecting fraud than any of the logistic regression models beforehand. I then increased the weights of fraudulent transactions by a factor of 100 in order to further improve the model. This then resulted in slightly less missed fraudulent transactions, however there were slightly more false positives. I then added a specified depth (specifies the depth of each of the individual trees in the algorithm) to the balanced xgboost model, which resulted in the most accurate model at 99.96% accuracy. It lowered the number of flase positives and missed fraudulent transactions.
## Dataset
The dataset contains transactions made by credit cards in September 2013 by European cardholders. This dataset presents transactions that occurred in two days, where we have 492 frauds out of 284,807 transactions. The dataset is highly unbalanced, the positive class (frauds) account for 0.172% of all transactions. It contains only numerical input variables which are the result of a PCA transformation. Unfortunately, due to confidentiality issues, we cannot provide the original features and more background information about the data. Features V1, V2, … V28 are the principal components obtained with PCA, the only features which have not been transformed with PCA are 'Time' and 'Amount'. Feature 'Time' contains the seconds elapsed between each transaction and the first transaction in the dataset. The feature 'Amount' is the transaction Amount, this feature can be used for example-dependant cost-sensitive learning. Feature 'Class' is the response variable and it takes value 1 in case of fraud and 0 otherwise. Given the class imbalance ratio, we recommend measuring the accuracy using the Area Under the Precision-Recall Curve (AUPRC). Confusion matrix accuracy is not meaningful for unbalanced classification. (From https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)
## Packages used
pandas, numpy, collections, matplotlib, seaborn, imblearn, shap, scikit-learn, xgboost
