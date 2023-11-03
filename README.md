# Credit-scrore-classifiction

This project aims to find the best model that is able to classify the credit score data. To validate the results with the helps of plots and explanation.

Data pre-processing

The data-set has been loaded from Kaggle. It consists of 27 features with 100000 examples after data cleaning. A train test split was done on the dataset to get a training set of 80000 examples and a testing set of 20000 examples. It consists of multiple classes - good, bad and standard respectively.
The purpose of analysing on this topic is to figure out how the features influenced the performance of the model. Some of the challenges faced were as follows -
• dealing with mixed data as categorical, metadata and continuous data type. • examining different metric for feature selection
• selecting a model from multiple metrics
Figure 1 shows the 27 features of the data after cleaning. The three classes have the following no of examples each:
• Good : - 17828
• Bad : - 28998
• Standard : - 53174

Dataset use - https://www.kaggle.com/code/ayanada/credit-score-classification/input?select=train.csv


Feature selection

Three types of feature set were considered for the analysis-
• one with all the features from the original dataset (figure 1).
• features extracted using chi square, F statistic and mutual information scores. The scores from chi square, F statistic and mutual information was normalised using the min and max value to a range of 0-1. The features that have very low value (¡0.5) in all the three metric have been removed. Figure 2 shows the value of chi square, F statistic and mutual information for all the features. The red line indicates the features that have low value is all the three metrics that will be removed. [’Num Bank Accounts’, ’Num Credit Card’, ’Interest Rate’, ’Num of Loan’, ’Delay from due date’, ’Num of Delayed Payment’, ’Num Credit Inquiries’, ’Credit Mix’, ’Outstanding Debt’, ’Credit History Age’, ’Payment of Min Amount’]
• features selected using forward selection - For every model we select a different set of features that impact the performance of the model most, unlike the statistics based selection which is independent of the model and it’s performance.

 
Models considered

For this project, the following different models were selected - Analyzed different models:
• Logistic regression - started with the simple classifier which would act as a base learner. This would be useful for feature generation.
• Decision trees - easy to implement but has high variance and expected to overfit for large depth.
• Decision tree with bagging - to decrease variance, randomness to combat high dimen- sionality.
• Decision stump with Gradient boosting - stumps further limit the depth of the decision tree and prevent overfitting.
• K Nearest Neighbours - use k neighbours in classsification by identifying patterns among the credit score data.
• Neural network - it is a self-learner and universal function approximator. All the above models will be tested using five fold cross validation.

Metrics

The models were compared based on the followwing metrics -
• train accuracy
• test accuracy
• confusion matrix
• F1 score
• average ROC curve (one vs all) and AUC for multiclass
A combination of above metrics are used for comparison. The exact combined score is expressed as -
Score = [Train Accuracy] + 1.25*[Test accuracy] + [F1 Score] + [AUC Score]
This particular combination is selected based on the intuition that a model with good test accuracy and is similar with respect to other metrics should be preferred over models with slightly better metrics other than test accuracy.

