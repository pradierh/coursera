# Data Scientist Role Play: Profiling and Analyzing the Yelp Dataset Coursera Worksheet

### Cursera SQL for data science final assignment

## Instructions
Welcome to the final assignment of our course! This assignment is designed to test your knowledge of a wide range of concepts and SQL design techniques discussed throughout the course. For this assignment, specifically, you are going to be ***playing the role of a real-world data scientist*** using SQL to both answer specific questions for an organization and make inferences based on your discoveries. 

We will be using a dataset from a US-based organization called Yelp, which provides a platform for users to provide reviews and rate their interactions with a variety of organizations – businesses, restaurants, health clubs, hospitals, local governmental offices, charitable organizations, etc. Yelp has made a portion of this data available for personal, educational, and academic purposes.

You will be asked a series of questions regarding the data to help you profile and better understand the data in the first part of the assignment. Once you have answered each question, you will come up with your own question for analysis and will prepare a dataset for the analysis you choose to do in the second part of the assignment.

Naturally, the questions will require you to write a variety of SQL statements. The reading in this lesson entitled, ***"Yelp Data Set SQL Lookup,"*** will allow you to run all of the queries you need to against the Yelp Data Set below. Also, be sure to check out the ***Yelp Dataset ER Diagram*** and instructions below for more detailed information on the dataset and how to complete the assignment. The Grading Criteria Overview section includes ***the Worksheet*** to be filled out and turned in.

### Review criteria 

This is a 2-part assignment. In the first part, you are asked a series of questions that will help you profile and understand the data just like a data scientist would. For this first part of the assignment, you will be assessed both on the correctness of your findings, as well as the code you used to arrive at your answer. You will be graded on how easy your code is to read, so remember to use proper formatting and comments where necessary.

In the second part of the assignment, you are asked to come up with your own inferences and analysis of the data for a particular research question you want to answer. You will be required to prepare the dataset for the analysis you choose to do. As with the first part, you will be graded, in part, on how easy your code is to read, so use proper formatting and comments to illustrate and communicate your intent as required.

For both parts of this assignment, use this "worksheet." It provides all the questions you are being asked, and your job will be to transfer your answers and SQL coding where indicated into this worksheet so that your peers can review your work. You should be able to use any Text Editor (Windows Notepad, Apple TextEdit, Notepad ++, Sublime Text, etc.) to copy and paste your answers. If you are going to use Word or some other page layout application, just be careful to make sure your answers and code are lined appropriately.
In this case, you may want to save as a PDF to ensure your formatting remains intact for you reviewer.

### Yelp Dataset ER Diagram

<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/rnhPP7g_EeeX9g4BeVWsoA_8d321af227c067c5b451df37b48ab758_YelpERDiagram.png?expiry=1687478400000&hmac=UNQX74-qY-wYAl43HVufGyr_NsNNwHbMSk9yyuJ4MIQ" width="822" height="732">

## Part 1: Yelp Dataset Profiling and Understanding

### 1. Profile the data by finding the total number of records for each of the tables below:

| Table             | Number of Rows |
| ----------------- | -------------- |
| Attribute table   | 10000          |
| Business table    | 10000          |
| Category table    | 10000          |
| Checkin table     | 10000          |
| elite_years table | 10000          |
| friend table      | 10000          |
| hours table       | 10000          |
| photo table       | 10000          |
| review table      | 10000          |
| tip table         | 10000          |
| user table        | 10000          |

### 2. Find the total distinct records by either the foreign key or primary key for each table. If two foreign keys are listed in the table, please specify which foreign key.

| Table        | Number of Rows |
| ------------ | -------------- |
| Business     | 10000          |
| Hours        | 1562           |
| Category     | 2643           |
| Attribute    | 1115           |
| Review       | 8090 (business_id) |
| Checkin      | 493            |
| Photo        | 6493           |
| Tip          | 3979 (business_id) |
| User         | 10000          |
| Friend       | 11 (user_id)   |
| Elite_years  | 2780           |

Note: Primary Keys are denoted in the ER-Diagram with a yellow key icon.	

### 3. Are there any columns with null values in the Users table? Indicate "yes," or "no."

	Answer: no
	
	
SQL code used to arrive at answer:

``` sql
SELECT *
FROM USER
WHERE NAME IS NULL
        OR review_count IS NULL
        OR yelping_since IS NULL
        OR useful IS NULL
        OR funny IS NULL
        OR cool IS NULL
        OR fans IS NULL
        OR average_stars IS NULL
        OR compliment_hot IS NULL
        OR compliment_more IS NULL
        OR compliment_profile IS NULL 
        OR compliment_cute IS NULL
        OR compliment_list IS NULL
        OR compliment_note IS NULL
        OR compliment_plain IS NULL
        OR compliment_funny IS NULL
        OR compliment_writer IS NULL
        OR compliment_photos IS NULL;
```
### 4. For each table and column listed below, display the smallest (minimum), largest (maximum), and average (mean) value for the following fields:

#### i. Table: Review, Column: Stars
	
	min:1		max:5		avg:3.7082
		
	
#### ii. Table: Business, Column: Stars
	
	min:1		max:5		avg:3.6549
		
	
 #### iii. Table: Tip, Column: Likes
	
	min:0		max:2		avg:0.0144
		
	
#### iv. Table: Checkin, Column: Count
	
	min:1		max:53		avg:1.9414
		
	
#### v. Table: User, Column: Review_count
	
	min:0		max:2000	avg:24.2995

### 5. List the cities with the most reviews in descending order:

SQL code used to arrive at answer:

``` sql
SELECT 
  city, 
  SUM(review_count) AS total_reviews 
FROM 
  business 
GROUP BY 
  city 
ORDER BY 
  total_reviews DESC;
```

Copy and Paste the Result Below:

| city            | total_reviews |
| --------------- | ------------- |
| Las Vegas       | 82854         |
| Phoenix         | 34503         |
| Toronto         | 24113         |
| Scottsdale      | 20614         |
| Charlotte       | 12523         |
| Henderson       | 10871         |
| Tempe           | 10504         |
| Pittsburgh      | 9798          |
| Montréal        | 9448          |
| Chandler        | 8112          |
| Mesa            | 6875          |
| Gilbert         | 6380          |
| Cleveland       | 5593          |
| Madison         | 5265          |
| Glendale        | 4406          |
| Mississauga     | 3814          |
| Edinburgh       | 2792          |
| Peoria          | 2624          |
| North Las Vegas | 2438          |
| Markham         | 2352          |
| Champaign       | 2029          |
| Stuttgart       | 1849          |
| Surprise        | 1520          |
| Lakewood        | 1465          |
| Goodyear        | 1155          |
(Output limit exceeded, 25 of 362 total rows shown)

### 6. Find the distribution of star ratings to the business in the following cities:

i. Avon

SQL code used to arrive at answer:

```sql
select stars, count(stars)
from business
where city = 'Avon'
group by stars
```

Copy and Paste the Resulting Table Below (2 columns star rating and count):

| stars | sum_of_review |
|-------|---------------|
| 1.5   | 1             |
| 2.5   | 2             |
| 3.5   | 3             |
| 4.0   | 2             |
| 4.5   | 1             |
| 5.0   | 1             |

ii. Beachwood

SQL code used to arrive at answer:

```SQL
select stars, count(stars)
from business
where city = 'Beachwood'
group by stars
```

Copy and Paste the Resulting Table Below (2 columns star rating and count):

| stars | sum_of_review |
|-------|---------------|
| 2.0   | 1             |
| 2.5   | 1             |
| 3.0   | 2             |
| 3.5   | 2             |
| 4.0   | 1             |
| 4.5   | 2             |
| 5.0   | 5             |

### 7. Find the top 3 users based on their total number of reviews:
		
SQL code used to arrive at answer:

```SQL
SELECT 
  name, 
  review_count AS total_reviews 
FROM 
  user 
ORDER BY 
  review_count DESC 
LIMIT 
  3;
```

Copy and Paste the Result Below:

| name   | total_reviews |
|--------|---------------|
| Gerald |          2000 |
| Sara   |          1629 |
| Yuri   |          1339 |

### 8. Does posing more reviews correlate with more fans?

Please explain your findings and interpretation of the results:
  
	No there is not any correlation with posing more reviews and having more fans.
	After looking for a function that could help determine a certain correlation, 
	I came across the corr() function, which unfortunately isn't included in SQLite. 
	So I found the formula and applied it in a query. The result being close to 0,
 	this determines that there is very little or no correlation between these two columns.

### 9. Are there more reviews with the word "love" or with the word "hate" in them?

	Answer: There are more reviews with the word "love" than reciew with word "hate".

| love_count | hate_count |
|------------|------------|
|       1780 |        232 |

SQL code used to arrive at answer:

```SQL
SELECT
    SUM(CASE WHEN text LIKE '%love%' THEN 1 ELSE 0 END) AS love_count,
    SUM(CASE WHEN text LIKE '%hate%' THEN 1 ELSE 0 END) AS hate_count
FROM
    review;
```

### 10. Find the top 10 users with the most fans:

SQL code used to arrive at answer:

```SQL
SELECT 
  name, 
  fans 
FROM 
  user 
ORDER BY 
  fans DESC 
LIMIT 
  10;
```

Copy and Paste the Result Below:

 | name      | fans |
|-----------|------|
| Amy       |  503 |
| Mimi      |  497 |
| Harald    |  311 |
| Gerald    |  253 |
| Christine |  173 |
| Lisa      |  159 |
| Cat       |  133 |
| William   |  126 |
| Fran      |  124 |
| Lissa     |  120 |

## Part 2: Inferences and Analysis

### 1. Pick one city and category of your choice and group the businesses in that city or category by their overall star rating. Compare the businesses with 2-3 stars to the businesses with 4-5 stars and answer the following questions. Include your code.

| Chosen city   | Chosen category |
|---------------|-----------------|
| Las Vegas     | Shopping        |

#### i. Do the two groups you chose to analyze have a different distribution of hours?

	With my query i only got 4 results.
	One of them is 3.5 and for the purpose of the exercise i'll include it in the 2-3 stars group.
	So 2 of them are in the 2-3 group and the other half in the 4-5 group.
	It seems that the 4-5 group has shorter hours than the 2-3.

	Average accumulated opening hours for the 2-3 star group --> 70h
 	Average accumulated opening hours for the 4-5 star group --> 52.25h

#### ii. Do the two groups you chose to analyze have a different number of reviews?

	Yes they do. The 2-3 group has 17 reviews. The 4-5 has 36 reviews.
         
#### iii. Are you able to infer anything from the location data provided between these two groups? Explain.
  
	With the clear lack of data I can't deduce anything from this sample. 

SQL code used for analysis:

```SQL
SELECT name,
       category,
       stars,
       review_count,
       hours,
       is_open,
       postal_code,
       neighborhood
FROM   business
       INNER JOIN category
               ON business.id = category.business_id
       INNER JOIN hours
               ON business.id = hours.business_id
WHERE  city = 'Las Vegas'
       AND category = 'Shopping'
ORDER  BY stars; 
```
		
### 2. Group business based on the ones that are open and the ones that are closed. What differences can you find between the ones that are still open and the ones that are closed? List at least two differences and the SQL code you used to arrive at your answer.
		
#### i. Difference 1:

	The first difference is that open businesses have a higher average number of stars than closed businesses.
         
#### ii. Difference 2:

	The second difference is that the average number of reviews is
 	higher for businesses that are still open than for those that are closed.

SQL code used for analysis:

```SQL
SELECT 
  count(id), 
  AVG(stars), 
  AVG(review_count), 
  is_open 
FROM 
  business 
GROUP BY 
  is_open;
```

| count(id) | AVG(stars)    | AVG(review_count) | is_open |
|-----------|---------------|-------------------|---------|
| 1520      | 3.52039473684 | 23.1980263158     | 0       |
| 8480      | 3.67900943396 | 31.7570754717     | 1       |

### 3. For this last part of your analysis, you are going to choose the type of analysis you want to conduct on the Yelp dataset and are going to prepare the data for analysis.

Ideas for analysis include: Parsing out keywords and business attributes for sentiment analysis, clustering businesses to find commonalities or anomalies between them, predicting the overall star rating for a business, predicting the number of fans a user will have, and so on. These are just a few examples to get you started, so feel free to be creative and come up with your own problem you want to solve. Provide answers, in-line, to all of the following:
	
### i. Indicate the type of analysis you chose to do:

 	The result of executing this query would provide you with aggregated counts of positive,
 	negative, and neutral sentiments for each star rating category in the "review" table.
  	This can help you gain insights into the sentiment distribution based on the star
   	ratings given by customers in their reviews.
	

#### ii. Write 1-2 brief paragraphs on the type of data you will need for your analysis and why you chose that data:

	The data needed for this query are only situated in the review table.
 	I only needed the stars and text fields to perform this query.
  	After this i used chatGPT to give me a list of keywords that can refer
 	to a good or bad sentiment.

> Please note that this query is just an indicator for the sentiment distribution based
> on the star ratings.

#### iii. Output of your finished dataset:

| stars | good_sentiment | bad_sentiment | neutral_sentiment |
|-------|----------------|---------------|-------------------|
| 1     | 317.0          | 738.0         | 531.0             |
| 2     | 289.0          | 339.0         | 330.0             |
| 3     | 567.0          | 328.0         | 467.0             |
| 4     | 1437.0         | 331.0         | 829.0             |
| 5     | 2973.0         | 240.0         | 1100.0            |

#### iv. Provide the SQL code you used to create your final dataset:

```SQL
SELECT 
  stars, 
  SUM(
    CASE WHEN r.text LIKE '%great%' 
    OR r.text LIKE '%excellent%'
    OR r.text LIKE '%outstanding%'
    OR r.text LIKE '%amazing%'
    OR r.text LIKE '%fantastic%'
    OR r.text LIKE '%wonderful%'
    OR r.text LIKE '%great%'
    OR r.text LIKE '%impressive%'
    OR r.text LIKE '%exceptional%'
    OR r.text LIKE '%delightful%'
    OR r.text LIKE '%helpful%'
    OR r.text LIKE '%friendly%'
    OR r.text LIKE '%efficient%'
    OR r.text LIKE '%reliable%'
    OR r.text LIKE '%well-organized%'
    OR r.text LIKE '%affordable%'
    OR r.text LIKE '%professional%'
    OR r.text LIKE '%satisfied' THEN 1 ELSE 'NULL' END
  ) AS good_sentiment, 
  SUM(
    CASE WHEN r.text LIKE '%bad%' 
    OR r.text LIKE '%terrible%'
    OR r.text LIKE '%awful%' 
    OR r.text LIKE '%horrible%' 
    OR r.text LIKE '%disappointing%' 
    OR r.text LIKE '%poor%' 
    OR r.text LIKE '%bad%' 
    OR r.text LIKE '%unpleasant%' 
    OR r.text LIKE '%frustrating%' 
    OR r.text LIKE '%rude%'
    OR r.text LIKE '%slow%' 
    OR r.text LIKE '%inefficient%' 
    OR r.text LIKE '%unprofessional%' 
    OR r.text LIKE '%dirty%' 
    OR r.text LIKE '%overpriced%' 
    OR r.text LIKE '%faulty%' 
    OR r.text LIKE '%unreliable%' 
    OR r.text LIKE '%misleading%' 
    OR r.text LIKE '%neglected%'
    OR r.text LIKE '%incompetent%'  
    OR r.text LIKE '%disorganized%'  THEN 1 ELSE 'NULL' END
  ) AS bad_sentiment,
    SUM(
    CASE WHEN r.text LIKE '%bad%'
    OR r.text LIKE '%great%'
    OR r.text LIKE '%satisfied%'
    OR r.text LIKE '%excellent%'
    OR r.text LIKE '%outstanding%'
    OR r.text LIKE '%amazing%'
    OR r.text LIKE '%fantastic%'
    OR r.text LIKE '%wonderful%'
    OR r.text LIKE '%great%'
    OR r.text LIKE '%impressive%'
    OR r.text LIKE '%exceptional%'
    OR r.text LIKE '%delightful%'
    OR r.text LIKE '%helpful%'
    OR r.text LIKE '%friendly%'
    OR r.text LIKE '%efficient%'
    OR r.text LIKE '%reliable%'
    OR r.text LIKE '%well-organized%'
    OR r.text LIKE '%affordable%'
    OR r.text LIKE '%professional%'
    OR r.text LIKE '%terrible%'
    OR r.text LIKE '%awful%' 
    OR r.text LIKE '%horrible%' 
    OR r.text LIKE '%disappointing%' 
    OR r.text LIKE '%poor%' 
    OR r.text LIKE '%bad%' 
    OR r.text LIKE '%unpleasant%' 
    OR r.text LIKE '%frustrating%' 
    OR r.text LIKE '%rude%'
    OR r.text LIKE '%slow%' 
    OR r.text LIKE '%inefficient%' 
    OR r.text LIKE '%unprofessional%' 
    OR r.text LIKE '%dirty%' 
    OR r.text LIKE '%overpriced%' 
    OR r.text LIKE '%faulty%' 
    OR r.text LIKE '%unreliable%' 
    OR r.text LIKE '%misleading%' 
    OR r.text LIKE '%neglected%'
    OR r.text LIKE '%incompetent%'  
    OR r.text LIKE '%disorganized%' THEN 'NULL'
    ELSE 1 END
  ) AS neutral_sentiment 
FROM
    review AS r
GROUP BY 
  r.stars;
  ```
