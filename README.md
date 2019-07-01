# UTC Credit Dataset
## Prediction of Credit Card Default in Taiwan

This model predicts credit defaults, based on a UTC data set with default payments information of customers in Taiwan from 2005.*  To create this model, three machine learning algorithms were examined and compared: Logistic Regression, K Nearest Neighbors, and Decision Tree. The goal was to reach the highest-possible F1 score (i.e., the harmonic average of the precision and recall, with the F1 score ranging from 0 to 1, 1 being the perfect precision and recall).

Below is the attribute information from the UTC website: 

<img src = "./images/image2.png"  width = 1150  height = 250>

As a first step, a preliminary EDA was conducted:

<img src = "./images/image3.png" style = max width = 80%>

Following the EDA, it was decided to drop outliers and the features with the bills' amounts (which did not show significant correlation with the risk of default).

<img src = "./images/image4.png" style = max width = 90%>

It has also been decided to combine time-of-payment information into three groups: 
1) On-time payments (including early payments)
2) Late payments - up to 30 days late
3) Late payments - more than 30 days late

<img src = "./images/image5.png">

Once this grouping has been applied, the top 5 elements in the data set were as follows:

<img src = "./images/image6.png">

Next, a histogram of the data was examined, for some clarity on the distributions of the difference features...

<img src = "./images/image7.png">

...and of the distribution and the size of credit among different variables.

<img src = "./images/image8.png" style = max width = 90%>

Next, default status information was arranged by different customer groups.  The preliminary conclusions of this information are reflected in the chart below:

<img src = "./images/image9.png">

To a certain degree, late payments correlated with going into default.

<img src = "./images/image10.png" style = max width = 40%>

Prior to training, dummy variables were created based on the following categorical features: "Sex", "Education", and "Marriage". Some of the columns were renamed to make the features more clear.

<img src = "./images/image11.png">

Once the new dummy variables were added, the original ones were dropped.

<img src = "./images/image12.png">

Since the EDA did not yield features with significant-enough influence on the the risk of default, it was decided to create more features. including polynomials and interaction (multiplication). 

<img src = "./images/image13.png">

After dividing the data frame into 'features' and 'target', the Sklearn Train_Test_Split method was applied in order to train and validate the model.

<img src = "./images/image14.png">

From the 189 resulting features (after applying polynomials and interactions), the best 45 features were selected using F_regression of the SelectKbest method from Sklearn.

<img src = "./images/image15.png">

Next, the data was scaled using Sklearn Standard Scaler.

<img src = "./images/image16.png">

Next, a hyper-parameter tuning was applied to each of the algorithms (Logistic Regression, K Nearest Neighbors and Decision Tree), using SKLearn grid search.  Following is an example of the logistic regression tuning. Example for the other algorithms can be found in the Python code document.

<img src = "./images/image17.png" style = max width = 90%>

After choosing the best parameter, algoritms were evaluated against each other, to find the best F1 score.

This was the "KNN" result:

<img src = "./images/image19.png">

And this is the "Decision Trees" result:

<img src = "./images/image20.png">

The best F1 score (0.533) was achieved with the logistic regression algorithm, which was therefore chosen as the classifier for the final model.

<img src = "./images/image21.png">

A visualization chart of the confusion matrix of the logistic regression was added for additional clarity on the results. In addition, since credit is at issue, it was crucial to avoid false negatives. and the logistic regression model scored the highest in this regard as well. 

<img src = "./images/image22.png" height = 475 width = 475>

As a final note, this data set is complicated to base predictions on, as it includes many confusing features. Upon reviewing different attempts made by other users to utilize this data (on Kaggle website), an F1 score of 0.53 seems to be relatively high for this particular data set.

*For additional information on the UTC data set used for this project, and the UTC research in general, please refer to the UTC website at: https://archive.ics.uci.edu/ml/datasets/default+of+credit+card+clients#
