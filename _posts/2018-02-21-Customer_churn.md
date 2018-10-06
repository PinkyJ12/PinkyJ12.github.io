---
layout: post
featured-img: churn
---

“The customer experience is the next competitive battleground.” – Jerry Gregoire

“The first step in exceeding your customer’s expectations is to know those expectations.” – Roy H. Williams

### Introduction

It is no secret that customer retention is a top priority for many companies; acquiring new customers can be several times more expensive than retaining existing ones. Furthermore, gaining an understanding of the reasons customers churn and estimating the risk associated with individual customers are both powerful components of designing a data-driven retention strategy. A churn model can be the tool that brings these elements together and provides insights and outputs that drive decision making across an organization.  

Customer churn occurs when customers or subscribers stop doing business with a company or service, also known as customer attrition. It is also referred as loss of clients or customers.
All industries suffer with “Churn”. It is seen more in the Satellite TV, telephone and internet providers where the percentage of people switching from one provider to another is significant month to month. A “churn” with respect to the Telecom industry, is defined as the percentage of subscribers moving from a specific service or a service provider to another in a given period of time.

Research shows today that the companies these companies have an average churn of 1.9 to 2 percent month on month and annualized churn ranging from 10 to 60 percent.
On the same basis, I decided to predict customer churn using telecom dataset.

I used 4-5 supervised models among which Logistic Regression and Random Forest worked best.



### Data Preprocessing
The data was downloaded from [IBM Sample Data Sets](https://www.ibm.com/communities/analytics/watson-analytics-blog/guide-to-sample-datasets/). Each row represents a customer, each column contains that customer’s attributes which I can categorised as Personal Info, Service Info and Billing Info:
The raw data contains 7043 rows (customers) and 21 columns (features). The “Churn” column is our target.

### Tools Used: 
Python, Jupyter notebook, Pandas, Flask ,  Tableau, AWS
### Packages 
pandas, 
matplotlib.pyplot
seaborn
LogisticRegression
GridSearchCV
roc_curve, auc
accuracy_score, recall_score, precision_score
confusion_matrix
cross_validation
RandomForestClassifier



Data is imported into pandas dataframe and cleaned. Firstly I checked for all null values and found that the null values were only in  "TotalCharges" and since Total charges is showing corelation with Monthly charges , I decided to drop Total Charges column as well as Customer ID column( as it was not making sense as a reason for customer to get churn).
By looking at values in the variables, its found that some wrangling is required. So, changed “No internet service” to “No” for six columns, that are: “OnlineSecurity”, “OnlineBackup”, “DeviceProtection”, “TechSupport”, “streamingTV”, “streamingMovies”. Also “No phone service” to “No” for column “MultipleLines”.
All of the categorical variables seem to have a reasonably broad distribution, therefore, all of them will be kept for the further analysis.

As the most of the variables were categorical, I changed them to numerical as 1 or 0 by using pandas get dummies function. Further changed all object datatypes to int values. 
Below are some graphs showing considerable relationship of features with the target data.
And finally stored the clean dataset in AWS postgresql by using sqlalchemy, to get exposure of AWS cloud.

After completing EDA, it was time to split the data into train and test and further look for the best model on the train dataset. 
After playing with some commands in posgresql , I further retrieved data in andas on my local machine.
As I started to model fit with my first Logistic Regression model, I realised my  target data is imbalanced as ratio of no. of customers churning was very less as compared to number of customers who stay with company (approx 1:6).
I firstly split the data to keep my test data completely separate from my trained data. Then upsampled the minority class in train dataset.Thus, now in trainset I've equal samples of both classes(churned and not churned).

The train data was trained on following models.

* Logistic Regression 
* Decision Tree
* Random Forest
* Naive Bayes
* SVM

Among which Logistic Regression and Naive Bayes performed well according to F1 score. It can be seen that in Decision Tree and Random Forest, there is compromise on Type1(False positive) error and Type2(False Negative) error respectively. The model can be improved further after setting its cutoff value depends upon company needs. 
 

Figure 10
Odds Ratio
One of the interesting performance measurements in logistic regression is Odds Ratio.Basically, Odds ratio is what the odds of an event is happening.



## Summary

From above, we can see that each model can be explained as per company's need.
points to be considered are:

* Features such as tenure_group, Contract, PaperlessBilling, MonthlyCharges and InternetService appear to play an important role in customer churn.
* There does not seem to be a relationship between gender and churn.
* Customers in a month-to-month contract, with PaperlessBilling and are within 12 months tenure, are more likely to churn; On the other hand, customers with one or two year contract, with longer than 12 months tenure, that are not using PaperlessBilling, are less likely to churn.

#### Identify key metrics optimization

Think about the scope and the metric being optimized. For instance, if the costs associated with your retention campaigns are high, then your model should be focused on reducing the number of false-positive hits . Identifying the right metric will help to measure the model’s impact and corresponding return on investment. 
