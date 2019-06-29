# UTC Credit Dataset
## Prediction of Credit Card Default in Taiwan

This UTC data set deals with the case of customers default payments in Taiwan.
My model try to predict  the probability of credit default for a costumer in the following month. For my model I examined and compare three different machine learning methods: Logistic Regression,K Nearest Neighbors and Decision Tree. My goal was to reach the highest possible f1 score   More details about the data set and the UTC research  can be found in the UTC website - https://archive.ics.uci.edu/ml/datasets/default+of+credit+card+clients#

Following is the Attribute information: 

<img src = "./images/image2.png">

I started my work with a basic EDA of the Data:

<img src = "./images/image3.png">

Following the preliminary EDA I decided to drop outliers and the sizes of the bills (who did not show any correlation with the risk of default)

<img src = "./images/image4.png">

I also decided to merge the payment time to three groups: on time, one month delay and more than one month delay.


<img src = "./images/image5.png">

After applying the changes, this is how currently the top five elements in my data set look like:


<img src = "./images/image6.png">

I also checked an histogram of the data to get better idea about the distributions of the difference features

<img src = "./images/image7.png">

And the distribution and the size of credit among different variables

<img src = "./images/image8.png">

I also checked the default status among different groups. My preliminary  conclusion are  written under the chart:

<img src = "./images/image9.png">

I found out that there is some correlation between delay in payments to default in the next month

<img src = "./images/image10.png">

Before starting training my model, I created dummy variables out of the features "Sex", "Education and "Marriage". I also rename some of the columns in order to have better understanding of the features.

<img src = "./images/image11.png">

After adding the new dummy variables,   I dropped the original ones.

<img src = "./images/image12.png">

Because I didn't find in my EDA a clear features that influence significantly on the risk of default, I decided to create more features including polynomials and interaction (multiplication) 

<img src = "./images/image13.png">

To be able to train and validate the model, I used Sklearn Train_Test_Split method. I split the data frame into features (independent variables) and target (dependent variable).

<img src = "./images/image14.png">

From the 189 features I have now after applying polynomials and interactions tools, I chose the best 45, using F_regression of the SelectKbest method from Sklearn.

<img src = "./images/image15.png">

After the feature selection I scaled the data using Sklearn Standard scaler.

<img src = "./images/image16.png">

For each one of my models (Logistic Regression, K Nearest Neighbors and Decision Tree) I ran hyper-parameter tuning, using sklearn grid search. Following is an example of the logistic regression tuning. Example for the other models can be found in the code document.

<img src = "./images/image17.png">

After choosing the best parameter I evaluated my models against each other. I looked for the best F1 score. This is the KNN model result:

<img src = "./images/image19.png">

And this is the Decision Trees" result:

<img src = "./images/image20.png">

My best F1 score (0.533) was achieved with the logistic regression model which was chosen to my final model.

<img src = "./images/image21.png">

I added  a chart for the confusion matrix of the logistic regression, to have better understanding of the result. Because we deal with credit, the scenario we would like to avoid the most is false Negative, and also in this matter, the logistic regression model had the best results.

<img src = "./images/image22.png">

Summary - This data set is complicated to predict and includes many confusing features. going over different attempts with this data on Kaggle, F1 score of 0.53 seems to be relatively good results (also of course not so good in general in order to predict default). according to the research in UTC, only models using neural networks were able to achieve significantly better results, so I hope in the future to come back to this data and apply more sophisticated tools for prediction. 

