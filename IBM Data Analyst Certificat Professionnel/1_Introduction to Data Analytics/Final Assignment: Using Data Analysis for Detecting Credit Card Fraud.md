# Introduction to Data Analytics Final Assignment
## Data-Driven Approaches for Credit Card Fraud Detection: A Comprehensive Analysis

Companies today are employing analytical techniques for the early detection of credit card frauds, a key factor in mitigating fraud damage. The most common type of credit card fraud does not involve the physical stealing of the card, but that of credit card credentials, which are then used for online purchases.
Imagine that you have been hired as a Data Analyst to work in the Credit Card Division of a bank. And your first assignment is to join your team in using data analysis for the early detection and mitigation of credit card fraud.
In order to prescribe a way forward, that is, suggest what should be done in order for fraud to get detected early on, you need to understand what a fraudulent transaction looks like. And for that you need to start by looking at historical data.

###  Here is a sample data set that captures the credit card transaction details for a few users.

<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/MNep_ZY-ScaXqf2WPrnG0Q_3be5abeee8944747ab0a58a705df415c_DA_1-Q7-Data-Table.png?expiry=1688342400000&hmac=j_aXDQBUGfUENeU01kVfkhuOzW2T8BDGymewLGzxriU" width="100%" height="100%">

Descriptive techniques of analysis, that is, techniques that help you gain an understanding of what happened, include the identification of patterns and anomalies in data. Anomalies signify a variation in a pattern that seems uncharacteristic, or, out of the ordinary. Anomalies may occur for perfectly valid and genuine reasons, but they do warrant an evaluation because they can be a sign of fraudulent activity.

### Past studies have suggested that some of the common events that you may need to watch out for include:

- A change in frequency of orders placed, for example, a customer who typically places a couple of orders a month, suddenly makes numerous transactions within a short span of time, sometimes within minutes of the previous order.
- Orders that are significantly higher than a user’s average transaction.
- Bulk orders of the same item with slight variations such as color or size—especially if this is atypical of the user’s transaction history.
- A sudden change in delivery preference, for example, a change from home or office delivery address to in-store, warehouse, or PO Box delivery.
- A mismatched IP Address, or an IP Address that is not from the general location or area of the billing address.

### Before you can analyze the data for patterns and anomalies, you need to:

- Identify and gather all data points that can be of relevance to your use case. For example, the card holder’s details, transaction details, delivery details, location, and network are some of the data points that could be explored.
- Clean the data. You need to identify and fix issues in the data that can lead to false or incomplete findings, such as missing data values and incorrect data. You may also need to standardize data formats in some cases, for example, the date fields.

Finally, when you arrive at the findings, you will create appropriate visualizations that communicate your findings to your audience. The graph below samples one such visualization that you would use to capture a trend hidden in the sample data set shared earlier on in the case study.

<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/M1sTK7IQQAibEyuyEAAIBw_62598de906f0424494f10efc877a7c5c_DA_1-Q9-Chart.png?expiry=1688342400000&hmac=6SgHGZuurLR4Vzqgv5EiRIKDk0MMLZm9QfM-M_ouU_c" width="50%%" height="50%">


## Final Assignment:

<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/MNep_ZY-ScaXqf2WPrnG0Q_3be5abeee8944747ab0a58a705df415c_DA_1-Q7-Data-Table.png?expiry=1688342400000&hmac=j_aXDQBUGfUENeU01kVfkhuOzW2T8BDGymewLGzxriU" width="100%" height="100%">

### 1. List at least 5 (five) data points that are required for the analysis and detection of a credit card fraud. (3 marks)

 	- Shipping address 
 	- IP address
 	- Transaction value 
 	- Units purchased
 	- Transaction date

### 2. Refer to the data table below and identify 3 (three) errors/issues that could impact the accuracy of your findings. (3 marks)

	- The date format is not standardized throughout the entire "transaction date" column  
	- There are missing values in "transaction value",  "age"," IP Address" 
	- Some values at "shipping address" are lacking informations. For exemple "In-store" value doesn't show the country or the city. 

### 3. Refer to the data table below and identify 2 (two) anomalies or unexpected behaviors, that would lead you to believe the transaction may be suspect. (2 marks)

 	- For johnp, in a short period of time the number of units purchases jumped from 1 or 2 to 10, 15, 20
 	- For johnp, the address shipping address changed 
 	- For johnp the transcation value jumped from usually less than 150$ per order to 2000$ / 3000$ / 4000$
 	- ellend has a purchase for a computer that costs 4,895$ and just for one unit 


### 4. Briefly explain your key take-away from the provided data visualization chart. (1 mark)

<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/M1sTK7IQQAibEyuyEAAIBw_62598de906f0424494f10efc877a7c5c_DA_1-Q9-Chart.png?expiry=1688342400000&hmac=6SgHGZuurLR4Vzqgv5EiRIKDk0MMLZm9QfM-M_ouU_c" width="50%%" height="50%">

 	- The graph express the transaction value per transaction.
 	- It can visually highlight an anomaly.
 	- For davidg it seems that there is nothing to be worried about, all the transactions don't go up the 200$.
 	- For johnp and ellend, the graphs clearly shows that the transactions clearly went from a maximum of 200$ to multiple 
   	thousands of dollars in multiple transactions for johnp wich is clearly a sign that there is something that 
    we need to be worried about. 
 	- For ellend it's only a one time transaction. It should ring a bell because the computer
   	that has been bought with her account is really expensive. But it can also be a one time 
    purchase for her birthday for exemple. 

### 5. Identify the type of analysis that you are performing when you are analyzing historical credit card data to understand what a fraudulent transaction looks like. 
> Hint: The four types of Analytics include: Descriptive, Diagnostic, Predictive, Prescriptive. (1 mark)

 	It's a descriptive type of analysis.
