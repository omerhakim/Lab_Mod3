# UTC Credit Dataset
## Prediction of Credit Card Default in Taiwan

This UTC data set deals with the case of customers default payments in Taiwan in the year 2005.
My model try to predict the probability of credit default for a costumer in the following month. For my model I examined and compared three different machine learning algorithms: Logistic Regression,K Nearest Neighbors and Decision Tree. My goal was to reach the highest possible f1 score. The F1 score is the harmonic average of the precision and recall, where an F1 score reaches its best value at 1 (perfect precision and recall) and worst at 0.

More details about the data set and the UTC research can be found in the UTC website - https://archive.ics.uci.edu/ml/datasets/default+of+credit+card+clients#

Following is the Attributes information from the UTC website: 

<img src = "./images/image2.png"  width = 1150  height = 250>

I started my work with a basic EDA of the Data:

<img src = "./images/image3.png" style = max width = 80%>

Following the preliminary EDA I decided to drop outliers and the features with the bills' amount (who did not show significant correlation with the risk of default)

<img src = "./images/image4.png" style = max width = 90%>

I also decided to merge the payment's time to three groups: On time (or early payment), one month delay and more than one month delay.

<img src = "./images/image5.png">

After applying these changes, this is how the top five elements in my data set looked like:


<img src = "./images/image6.png">

I also checked an histogram of the data to get better idea about the distributions of the difference features

<img src = "./images/image7.png">

And the distribution and the size of credit among different variables

<img src = "./images/image8.png" style = max width = 90%>

I also checked the default status among different groups. My preliminary  conclusion are  written under the chart:

<img src = "./images/image9.png">

I found out that there is some correlation between delay in payments to default in the next month

<img src = "./images/image10.png" style = max width = 40%>

Before starting training my model, I created dummy variables out of the categorical features "Sex", "Education" and "Marriage". I also renamed some of the columns in order to have better understanding of the features.

<img src = "./images/image11.png">

After adding the new dummy variables,   I dropped the original ones.

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

