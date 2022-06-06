# Jobathon-June-2022-Analytics-Vidhya
Smart Lead Scoring Engine, identify the potential leads for a D2C start-up

# Smart Lead Scoring Engine


* Can you identify the potential leads for a D2C startup?




### Problem Statement


* A D2C startup develops products using cutting edge technologies like Web 3.0. Over the past few months, the company has started multiple marketing campaigns offline and digital both. As a result, the users have started showing interest in the product on the website. These users with intent to buy product(s) are generally known as leads (Potential Customers). 


* Leads are captured in 2 ways - Directly and Indirectly. 


* Direct leads are captured via forms embedded in the website while indirect leads are captured based on certain activity of a user on the platform such as time spent on the website, number of user sessions, etc.


* Now, the marketing & sales team wants to identify the leads who are more likely to buy the product so that the sales team can manage their bandwidth efficiently by targeting these potential leads and increase the sales in a shorter span of time.


* Now, as a data scientist, your task at hand is to predict the propensity to buy a product based on the user's past activities and user level information.



### About Dataset


* You are provided with the leads data of last year containing both direct and indirect leads. Each lead provides information about their activity on the platform, signup information and campaign information. Based on his past activity on the platform, you need to build the predictive model to classify if the user would buy the product in the next 3 months or not.

	We have to use classification algorithms to predict “buy”.
•	The Classification algorithm is a Supervised Learning technique that is used to identify the category of new observations on the basis of training data. In Classification, a program learns from the given dataset or observations and then classifies new observation into a number of classes or groups. Such as, Yes or No, 0 or 1, Spam or Not Spam, cat or dog, etc. Classes can be called as targets/labels or categories.

•	The data dictionary is also given.

| Variable |	Description |
| ---------| -------------|
| id	| Unique identifier of a lead |
| created_at |	Date of lead dropped |
| signup_date |	Sign up date of the user on the website |
| campaign_var | (1 and 2)	campaign information of the lead |
| products_purchased |	No. of past products purchased at the time of dropping the lead |
| user_activity_var | (1 to 12)	Derived activities of the user on the website |
| buy |	0 or 1 indicating if the user will buy the product in next 3 months or not |



#### Approach to solve the problem: -

**Step 1: Define Problem Statement**

* The problem statement is given and we have to find the propensity to buy a product based on the user's past activities and user level information.

**Step 2: Data Gathering**

•	The training data set is given to train the model and the test data is given to test the data by predicting “buy”.

•	We also need to create a csv file containing the column id from test data and prediction which is “buy” column based on test data features.

**Step 3: Exploratory Data Analysis**

![image](https://user-images.githubusercontent.com/92113558/172220751-128d68a7-38c6-48be-afe7-5cac7eaf65ae.png)

![image](https://user-images.githubusercontent.com/92113558/172220792-9cb91d29-df89-4103-aa6a-c1e4c1642986.png)


•	Exploratory Data Analysis is an approach in analysing data sets to summarize their main characteristics, often using statistical graphics and other data visualization methods.

•	On plotting the target variable i.e., “buy” column.
  
•	We can clearly see the data is imbalanced. The problem is that models trained on unbalanced datasets often have poor results when they have to generalize (predict a class or classify unseen observations).
 
•	So, we have to balance this dataset.

![image](https://user-images.githubusercontent.com/92113558/172220859-2d4c9bbb-a7e6-4a59-99c3-e3acff667214.png)

•	Splitting up our data into an X array that contains the features to train on, and a y array with the target variable.

**Step 4: Feature Engineering**

•	Data Pre-processing

The data you collected is almost never in the right format. You will encounter a lot of inconsistencies in the data set such as missing values, redundant variables, duplicate values, etc. Removing such inconsistencies is very essential because they might lead to wrongful computations and predictions. Therefore, at this stage, you scan the data set for any inconsistencies and you fix them then and there.

•	Filling products purchased with mode.

In our training data we have missing values in column products_purchased and signup_date.
So, we need to fill the missing values in some mathematical and logical way. For products_purchased column we have discrete values. Discrete data is information that can only take certain values. So, I have used mode values for missing values.

•	Handle signup date column

In signup_date column we have missing values. But the signup_date column has the details Sign up date of the user on the website. So first convert it into datetime format and then We have to convert it to Year, Month, Day columns. And remove missing values by using mode.

•	Handling “created_at” column

On checking dtype of created_at column is object. Creating new column for date, month and year based on created_at column.
We have to do all the above data pre-processing steps for testing data also.

•	Handling Unbalance data

We can see data is imbalance so we have to balance the dataset by the use of Random Oversampling Technique.

**Step 5: - Feature Selection**

Feature selection is used for removing irrelevant features. We can use only important features for model prediction. Use best 8 features for prediction of model.
 

**Step 6: - Feature Scaling**
After selection of feature, we need to do feature scaling. Feature scaling bring down all the data on the same scale.

![image](https://user-images.githubusercontent.com/92113558/172220920-8b138a07-14d6-4b80-b1f7-2103f2515f05.png)


**Step 7:- Train Test Split**

Split the data into a training set and a testing set. We will train out model on the training set and then use the test set to evaluate the model.

**Step 8: Building a Machine Learning Model**

All the insights and patterns derived during Data Exploration are used to build the Machine Learning Model. This stage always begins by splitting the data set into two parts, training data, and testing data. The training data will be used to build and analyse the model. The logic of the model is based on the Machine Learning Algorithm that is being implemented.

It is a classification problem so we have to use classification algorithms.
•	Logistic Regression
•	Decision Tree Classifier
•	Random Forest Classifier
•	Ada Boost Classifier
•	XG Boost Classifier

**Step 9: Model Evaluation**
After building a model by using the training data set, it is finally time to put the model to a test. The testing data set is used to check the efficiency of the model and how accurately it can predict the outcome. Once the accuracy is calculated, any further improvements in the model can be implemented at this stage.

In this case we have used: -
•	Classification Report
•	Confusion matrix
•	F1 score (The evaluation metric for this hackathon would be F1 Score of Class 1.)
Created a data frame of models for f1 Score
| - |	Model	| F1 score |
| 1	| Logistic Regression |	0.821509 |
| 2	| Decision Tree Classifier	| 0.795573 |
| 3	| Random Forest Classifier	| 0.838503 |
| 4	| Ada Boost Classifier	| 0.837975 |
| 5	| XG Boost Classifier	| 0.861055 |

So based on f1 score for class 1 the Xg Boost Classifier will be used for test data.

•	ROC Curve
 ![image](https://user-images.githubusercontent.com/92113558/172220958-c8cd5ff0-bc07-49cc-939b-bba2bd001dee.png)

**Step 10: - Hyper Parameter Tunning of XG boost model:**

* For XG Boost Classifier we choosing the optimal parameters for better efficiency.
* 
**Step 11: - Predictions**

Once the model is evaluated and improved, it is finally used to make predictions. We are going to use test data for predictions.
After predictions we will create a csv file consist of id from the test data and predictions(“buy”) based on testing data.


