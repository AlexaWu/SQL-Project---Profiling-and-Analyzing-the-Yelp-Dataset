# SQL Project - Profiling and Analyzing the Yelp Dataset 

### :bookmark: Project dataset

This project using a large dataset and dataset ER diagram from Yelp, which provides a platform for users to provide reviews and rate their interactions with a variety of organizations – businesses, restaurants, health clubs, hospitals, local governmental offices, charitable organizations, etc. 

#### Entity Relationship Diagram 

_Note: Primary Keys are denoted in the ER-Diagram with a yellow key icon._

![Yelp Dataset ER Diagram.png](Yelp%20Dataset%20ER%20Diagram.png)

### :bookmark: Project summary

The project has two parts.

`Part 1` I used SQL (count & nulls, distinct, joins, aggregations, group by, order by, limit, like, etc.) to profile and understand Yelp dataset.

`Part 2` I prepared the data and conduct Yelp dataset data analysis including: 
- parse out keywords and business attributes for sentiment analysis
- cluster businesses to find commonalities or anomalies between them
- predicte the overall star rating for a business
- predicte the number of fans a user will have

### :bookmark: Project details

#### [Part 1: Yelp Dataset Profiling and Understanding](https://github.com/AlexaWu/SQL-Project---Yelp-Dataset/blob/master/Profiling%20and%20Analyzing%20the%20Yelp%20Dataset.md#part-1-yelp-dataset-profiling-and-understanding)
1. Profile the data by finding the total number of records for each of the tables.
2. Find the total distinct records by either the foreign key or primary key for each table.
3. Are there any columns with null values in the Users table?
4. For each table and column, display the smallest (minimum), largest (maximum), and average (mean) value
5. List the cities with the most reviews in descending order
6. Find the distribution of star ratings to the business in the following cities: i. Avon ii. Beachwood
7. Find the top 3 users based on their total number of reviews
8. Does posing more reviews correlate with more fans?
9. Are there more reviews with the word "love" or with the word "hate" in them?
10. Find the top 10 users with the most fans
11. Is there a strong relationship (or correlation) between having a high number of fans and being listed as "useful" or "funny?" Out of the top 10 users with the highest number of fans, what percent are also listed as “useful” or “funny”?

#### [Part 2: Inferences and Analysis](https://github.com/AlexaWu/SQL-Project---Yelp-Dataset/blob/master/Profiling%20and%20Analyzing%20the%20Yelp%20Dataset.md#part-2-inferences-and-analysis)
1. Pick one city and category of your choice and group the businesses in that city or category by their overall star rating. Compare the businesses with 2-3 stars to the businesses with 4-5 stars
2. Group business based on the ones that are open and the ones that are closed. What differences can you find between the ones that are still open and the ones that are closed? 
3. Conduct analysis on the Yelp dataset and prepare the data for analysis
