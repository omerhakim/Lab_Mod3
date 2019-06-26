# UTC Dataset
## Prediction of Credit Card Default in Taiwan

This UTC data set deals with the case of customers default payments in Taiwan.
My model try to predict  the probability of default with three different machine learning methods.  More details about the data set and the UTC research  can be found in the UTC website - https://archive.ics.uci.edu/ml/datasets/default+of+credit+card+clients#

Following is the Attribute information: 

<img src = "./images/image2.png">

I started my work with a basic EDA of the Data:

<img src = "./images/image3.png">

Following the preliminary EDA I decided to drop outliers and the sizes of the bills (who did not show any correlation with the risk of default)

<img src = "./images/image4.png">

I also decided to merge the payment time to three groups: on time, one month delay and more than one month delay.


<img src = "./images/image5.png">


After applying the changes, this is how curently the top five elements in my dataset look like:


<img src = "./images/image6.png">

I also checked an histogram of the data to get better idea about the distebutions of the differnce features

<img src = "./images/image7.png">

And the distribution and the size of credit among different variables

<img src = "./images/image8.png">

I also checked the default status among different groups. my conclution wre written under the chart:

<img src = "./images/image9.png">

I found out that there is some correlation between delay in paymnts to default in the next months

<img src = "./images/image10.png">

Before starting training my model, I created dummy variables out of the features "Sex", "Education and "Marriage". I also rename some of the columns in order to have better understaning of the features.

<img src = "./images/image11.png">

after adding the new dummy variables,  dropped the original ones.

<img src = "./images/image12.png">

Because I didn't find in my EDA a clear feture that influence clearly on the risk of defalut, I decided to create more features including polinomials and interaction (multiplcation) 

<img src = "./images/image13.png">

To be able to train and validate the model, I used Sklearn Train_Test_Split method. I split the data frame into features (independet variables) and target (dependet vaiable).

<img src = "./images/image14.png">

From the 189 features I have now after applying polynaomials and interactions tools, I chose 45, using F_regression of the SelectKbest methos from Sklearn.

<img src = "./images/image15.png">

After the feature selection I scaled the data using Sklearn Standard scaler.

<img src = "./images/image16.png">

For each one of my models (Logistic Regression, K Nearest Neigbors and Decision Tree) I ran hyper-parameter tuning, using sklearn grid search. Folloeing is an example of the logistic regression tuning. Example for the other models can be found in the code document.

<img src = "./images/image17.png">


After choosing the best parameter I evalute my models agains each other. I looked for the best F1 score. This is the KNN result:

<img src = "./images/image19.png">

and this is the Decision Trees" result:

<img src = "./images/image20.png">

My best F1 score (0.533) was achieved with the logistic regression model which was cohsen to my final model.

<img src = "./images/image21.png">

confusion matrix

<img src = "./images/image22.png">

summary

<img src = "./images/image23.png">
