# UTC Credit Dataset
## Prediction of Credit Card Default in Taiwan

This model predicts credit defaults, based on a UTC data set with default payments information of customers in Taiwan from 2005.*  To create this model, three machine learning algorithms were examined and compared: Logistic Regression,K Nearest Neighbors, and Decision Tree. The goal was to reach the highest-possible F1 score (i.e., the harmonic average of the precision and recall, with the F1 score ranging from 0 to 1, 1 being the perfect precision and recall).

Below is the attribute information from the UTC website: 

<img src = "./images/image2.png"  width = 1150  height = 250>

As a first step, a preliminary EDA was conducted:

<img src = "./images/image3.png" style = max width = 80%>

Following the EDA, it was decided to drop outliers and the features with the bills' amounts (which did not show significant correlation with the risk of default).

<img src = "./images/image4.png" style = max width = 90%>

I has also been decided to combine time-of-payment information into three groups: 
1) On-time payments (including early payments)
2) Late payments - up to 30 days late
3) Late payments - more than 30 days late

<img src = "./images/image5.png">

Once this grouping has been applied, the top 5 elements in the data set were as follows:

<img src = "./images/image6.png">

Next, a histogram of the data was examined, for some clarity on the distributions of the difference features - - - 

<img src = "./images/image7.png">

- - - and of the distribution and the size of credit among different variables.

<img src = "./images/image8.png" style = max width = 90%>

Next, default status information was arranged by different customer groups.  The preliminary co this information is reflected in the chart below:

<img src = "./images/image9.png">

To a certain degree, late payments correlated with going into default.

<img src = "./images/image10.png" style = max width = 40%>

Prior to training, dummy variables were created based on the following categorical features: "Sex", "Education", and "Marriage". Some of the columns were renamed to make the features more clear.

<img src = "./images/image11.png">

Once the new dummy variables were added, the original ones were dropped.

<img src = "./images/image12.png">

Because I didn't find in my EDA a clear features that influence significantly on the risk of default, I decided to create more features including polynomials and interaction (multiplication) 

<img src = "./images/image13.png">

After dividing the data frame into 'features' and 'target', the Sklearn Train_Test_Split method was applied in order to train and validate the model.

<img src = "./images/image14.png">

From the 189 features I had after applying polynomials and interactions, I selected the best 45, using F_regression of the SelectKbest method from Sklearn.

<img src = "./images/image15.png">

After the features selection,the data was scaled, using Sklearn Standard scaler.

<img src = "./images/image16.png">

For each one of the algorithms (Logistic Regression, K Nearest Neighbors and Decision Tree) I ran hyper-parameter tuning, using sklearn grid search. Following is an example of the logistic regression tuning. Example for the other algorithms can be found in the python code document.

<img src = "./images/image17.png" style = max width = 90%>

After choosing the best parameter I evaluated my algoritms against each other. I looked for the best F1 score.

This was the "KNN" result:

<img src = "./images/image19.png">

And this is the "Decision Trees" result:

<img src = "./images/image20.png">

My best F1 score (0.533) was achieved with the logistic regression algorithms which was chosen as the classifier for the final model.

<img src = "./images/image21.png">

I added  a chart for the confusion matrix of the logistic regression, to have better understanding of the result. Because we deal with credit, the scenario we would like to avoid the most is false Negative, and also in this matter, the logistic regression model had the best results.

<img src = "./images/image22.png" height = 475 width = 475>

Summary -

This data set is complicated to predict and includes many confusing features. going over different attempts of other users with this data on Kaggle website, F1 score of 0.53 seems to be relatively good results (also of course not so good in general in order to predict default). According to the research in UTC, only models using neural networks were able to achieve significantly better results, so I hope in the future to come back to this data set and apply more sophisticated tools for prediction. 


*For additional information on the UTC data set used for this model, and the UTC research in general, please refer to the UTC website at: https://archive.ics.uci.edu/ml/datasets/default+of+credit+card+clients#
