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

dropping variables

<img src = "./images/image11.png">

dummy variables, renaming

<img src = "./images/image12.png">

While there are no clear fetures that influenct clearly the risk of defalut i decided to create more features with polinomials and interaction 

<img src = "./images/image13.png">

Train test split

<img src = "./images/image14.png">

Feature selection

<img src = "./images/image15.png">

scaling

<img src = "./images/image16.png">

after basic models, hyper parameter tunning

<img src = "./images/image17.png">


evaluation

<img src = "./images/image19.png">

evaluation

<img src = "./images/image20.png">

final model

<img src = "./images/image21.png">

confusion matrix

<img src = "./images/image22.png">

summary

<img src = "./images/image23.png">
