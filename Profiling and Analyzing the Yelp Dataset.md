## Part 1: Yelp Dataset Profiling and Understanding

1. Profile the data by finding the total number of records for each of the tables below:
```javascript
	select count(*)
	from table_name;
```
i. Attribute table = 10000\
ii. Business table = 10000\
iii. Category table = 10000\
iv. Checkin table = 10000 \
v. elite_years table = 10000 \
vi. friend table = 10000\
vii. hours table = 10000\
viii. photo table = 10000\
ix. review table = 10000\
x. tip table = 10000\
xi. user table = 10000

2. Find the total distinct records by either the foreign key or primary key for each table. 
```javascript
	select count(distinct(business_id))
	from table_name;
```
i. Business = ID: 10000\
ii. Hours = business_id: 1562\
iii. Category = business_id: 2643\
iv. Attribute = business_id: 1115\
v. Review = primary key: ID: 10000. foreign key : business_id : 8090; user_id: 9581\
vi. Checkin = business_id : 493\
vii. Photo = primary key: ID: 10000. foreign key : business_id: 6493\
viii. Tip = user_id: 537; business_id: 3979\
ix. User = ID: 10000\
x. Friend = user_id: 11\
xi. Elite_years =user_id : 2780

3. Are there any columns with null values in the Users table?

	Answer: no.
```javascript
	select count(*)
	from user
	where id is null
	or name is null 
	or review_count is null 
	or yelping_since is null 
	or useful is null 
	or funny is null 
	or cool is null  
	or fans is null 
	or average_stars is null 
	or compliment_hot is null 
	or compliment_more is null 
	or compliment_profile is null 
	or compliment_cute is null 
	or compliment_list is null  
	or compliment_note is null 
	or compliment_plain is null 
	or compliment_cool is null 
	or compliment_funny is null 
	or compliment_writer is null 
	or compliment_photos is null;
```	

4. For each table and column listed below, display the smallest (minimum), largest (maximum), and average (mean) value for the following fields:
```javascript
	select min(column_name), max(column_name), avg(column_name)
	from table_name;
```


5. List the cities with the most reviews in descending order:
```javascript	
	select city, sum(review_count) as reviews
	from business
	group by city
	order by reviews desc;
```	

Result:

 city            | reviews 
--|--
| Las Vegas       |   82854 |
| Phoenix         |   34503 |
| Toronto         |   24113 |
| Scottsdale      |   20614 |
| Charlotte       |   12523 |
| Henderson       |   10871 |
| Tempe           |   10504 |
| Pittsburgh      |    9798 |
| Montréal        |    9448 |
| Chandler        |    8112 |
| Mesa            |    6875 |
| Gilbert         |    6380 |
| Cleveland       |    5593 |
| Madison         |    5265 |
| Glendale        |    4406 |
| Mississauga     |    3814 |
| Edinburgh       |    2792 |
| Peoria          |    2624 |
| North Las Vegas |    2438 |
| Markham         |    2352 |
| Champaign       |    2029 |
| Stuttgart       |    1849 |
| Surprise        |    1520 |
| Lakewood        |    1465 |
| Goodyear        |    1155 |

(Output limit exceeded, 25 of 362 total rows shown)
	

6. Find the distribution of star ratings to the business in the following cities:

i. Avon
```javascript	
	select stars, count(stars) as count
	from business
	where city = 'Avon'
	group by stars;
```
Resulting Table (2 columns – star rating and count):

 stars | count
--|--
|   1.5 |     1 |
|   2.5 |     2 |
|   3.5 |     3 |
|   4.0 |     2 |
|   4.5 |     1 |
|   5.0 |     1 |


ii. Beachwood
```javascript
	select stars, count(stars) as count
	from business
	where city = 'Beachwood'
	group by stars;
```
Resulting Table  (2 columns – star rating and count):

| stars | count |
--|--
|   2.0 |     1 |
|   2.5 |     1 |
|   3.0 |     2 |
|   3.5 |     2 |
|   4.0 |     1 |
|   4.5 |     2 |
|   5.0 |     5 |


7. Find the top 3 users based on their total number of reviews:
```javascript
	select id, name, review_count
	from user
	order by review_count desc
	limit 3;
```

	Result:
		
| id                     | name   | review_count |
--|--|--
| -G7Zkl1wIWBBmD0KRy_sCw | Gerald |         2000 |
| -3s52C4zL_DHRK0ULG6qtg | Sara   |         1629 |
| -8lbUNlXVSoXqaRRiHiSNg | Yuri   |         1339 |


8. Does posing more reviews correlate with more fans?
			      
	No. Based on the SQL code and result attached below, if we take a look at column review_count and column fans, 
	as the review_count decreasing, fans amount is floating but doesn't decrease. Therefore, posing more reviews not
	correlate with more fans, other factors should also be take into consideration.

```javascript
	select name, review_count, fans, yelping_since
	from user
	order by review_count desc;
```

| name      | review_count | fans | yelping_since       |
--|--|--|--
| Gerald    |         2000 |  253 | 2012-12-16 00:00:00 |
| Sara      |         1629 |   50 | 2010-05-16 00:00:00 |
| Yuri      |         1339 |   76 | 2008-01-03 00:00:00 |
| .Hon      |         1246 |  101 | 2006-07-19 00:00:00 |
| William   |         1215 |  126 | 2015-02-19 00:00:00 |
| Harald    |         1153 |  311 | 2012-11-27 00:00:00 |
| eric      |         1116 |   16 | 2007-05-27 00:00:00 |
| Roanna    |         1039 |  104 | 2006-03-28 00:00:00 |
| Mimi      |          968 |  497 | 2011-03-30 00:00:00 |
| Christine |          930 |  173 | 2009-07-08 00:00:00 |
| Ed        |          904 |   38 | 2009-08-10 00:00:00 |
| Nicole    |          864 |   43 | 2006-08-02 00:00:00 |
| Fran      |          862 |  124 | 2012-04-05 00:00:00 |
| Mark      |          861 |  115 | 2009-05-31 00:00:00 |
| Christina |          842 |   85 | 2012-10-08 00:00:00 |
| Dominic   |          836 |   37 | 2011-02-06 00:00:00 |
| Lissa     |          834 |  120 | 2007-08-14 00:00:00 |
| Lisa      |          813 |  159 | 2009-10-05 00:00:00 |
| Alison    |          775 |   61 | 2007-07-02 00:00:00 |
| Sui       |          754 |   78 | 2009-09-07 00:00:00 |
| Tim       |          702 |   35 | 2009-01-21 00:00:00 |
| L         |          696 |   10 | 2010-04-29 00:00:00 |
| Angela    |          694 |  101 | 2010-10-01 00:00:00 |
| Crissy    |          676 |   25 | 2008-07-31 00:00:00 |
| Lyn       |          675 |   45 | 2009-11-07 00:00:00 |

(Output limit exceeded, 25 of 10000 total rows shown)

	
9. Are there more reviews with the word "love" or with the word "hate" in them?

	Answer: Yes. There are 1780 reviews with the word 'love' and 232 reviews with the word 'hate'.
```javascript	
	select count(*)
	from review
	where text like '%love%';
```
| count(*) |
--|
|     1780 

```javascript
	select count(*)
	from review
	where text like '%hate%';
```

| count(*) |
--|
|      232 |
	

10. Find the top 10 users with the most fans:
```javascript
	select name, fans
  	from user
	order by fans desc
	limit 10;
```

Result:

| name      | fans |
--|--
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

11. Is there a strong relationship (or correlation) between having a high number of fans and being listed as "useful" or "funny?" Out of the top 10 users with the highest number of fans, what percent are also listed as “useful” or “funny”?

Key:
0% - 25% - Low relationship
26% - 75% - Medium relationship
76% - 100% - Strong relationship
```javascript
	select name, fans, useful, funny, cool,
	((useful+funny)*100)/(useful+funny+cool) as percentage
	from user
	order by fans desc
	limit 10;
```

Result:

| name      | fans | useful |  funny |   cool | percentage |
--|--|--|--|--|--
| Amy       |  503 |   3226 |   2554 |   2751 |         67 |
| Mimi      |  497 |    257 |    138 |    159 |         71 |
| Harald    |  311 | 122921 | 122419 | 122890 |         66 |
| Gerald    |  253 |  17524 |   2324 |  15008 |         56 |
| Christine |  173 |   4834 |   6646 |   4321 |         72 |
| Lisa      |  159 |     48 |     13 |      6 |         91 |
| Cat       |  133 |   1062 |    672 |   1076 |         61 |
| William   |  126 |   9363 |   9361 |   9370 |         66 |
| Fran      |  124 |   9851 |   7606 |   9344 |         65 |
| Lissa     |  120 |    455 |    150 |    342 |         63 |
	
	findings and interpretation of the results:
	
	As shown in the above result, there is top 10 users with the highest number of fans with their listed as "useful" or "funny".
	And the percent are also listed as “useful” or “funny”. Clearly, as the column 'fans' decreasing, the column 'percentage' 
	doesn't decrease the same as the column 'fans' decrease. Therefore, they have '0% - 25% - Low relationship'.
	
	

## Part 2: Inferences and Analysis

1. Pick one city and category of your choice and group the businesses in that city or category by their overall star rating. 
Compare the businesses with 2-3 stars to the businesses with 4-5 stars and answer the following questions. Include your code.
	
	I choose city 'Toronto' and category 'Restaurants'.

i. Do the two groups you chose to analyze have a different distribution of hours?
	Yes. As shown in the below result, calculate two group in total hours, the group 2-3 stars distribution of hours in total has longer 
	distribution of hours than group 4-5 stars.

ii. Do the two groups you chose to analyze have a different number of reviews?
	Yes. As shown in the below result, the group 4-5 stars has 26*7+8*7+89*5 = 683, 
	the group 2-3 stars has 47*7+34*7+5*7 = 602,
	so, group 4-5 stars have slightly more number of reviews than group 2-3 stars.
         
iii. Are you able to infer anything from the location data provided between these two groups? Explain.
	No, since both group 4-5 stars and group 2-3 stars are in the same state ON, so we couldn't infer further information through location data.

SQL code used for analysis:
```javascript
	select city, category, hours, stars, review_count, state,
	(stars between '2.0' and '3.0') as '2-3 stars',
	(stars between '4.0' and '5.0') as '4-5 stars'
	from business
	inner join category
	on business.id = category.business_id
  	inner join hours
	on business.id = hours.business_id
	where city = 'Toronto'
	and category = 'Restaurants'
 	group by stars
	order by stars DESC;
```

| city    | category    | hours                 | stars | review_count | state | 2-3 stars | 4-5 stars |
--|--|--|--|--|--|--|--
| Toronto | Restaurants | Monday|16:00-2:00     |   4.5 |           26 | ON    |         0 |         1 |
| Toronto | Restaurants | Tuesday|18:00-2:00    |   4.5 |           26 | ON    |         0 |         1 |
| Toronto | Restaurants | Friday|18:00-2:00     |   4.5 |           26 | ON    |         0 |         1 |
| Toronto | Restaurants | Wednesday|18:00-2:00  |   4.5 |           26 | ON    |         0 |         1 |
| Toronto | Restaurants | Thursday|18:00-2:00   |   4.5 |           26 | ON    |         0 |         1 |
| Toronto | Restaurants | Sunday|16:00-2:00     |   4.5 |           26 | ON    |         0 |         1 |
| Toronto | Restaurants | Saturday|16:00-2:00   |   4.5 |           26 | ON    |         0 |         1 |
| Toronto | Restaurants | Monday|11:00-23:00    |   4.5 |            8 | ON    |         0 |         1 |
| Toronto | Restaurants | Tuesday|11:00-23:00   |   4.5 |            8 | ON    |         0 |         1 |
| Toronto | Restaurants | Friday|11:00-23:00    |   4.5 |            8 | ON    |         0 |         1 |
| Toronto | Restaurants | Wednesday|11:00-23:00 |   4.5 |            8 | ON    |         0 |         1 |
| Toronto | Restaurants | Thursday|11:00-23:00  |   4.5 |            8 | ON    |         0 |         1 |
| Toronto | Restaurants | Sunday|14:00-23:00    |   4.5 |            8 | ON    |         0 |         1 |
| Toronto | Restaurants | Saturday|11:00-23:00  |   4.5 |            8 | ON    |         0 |         1 |
| Toronto | Restaurants | Sunday|12:00-16:00    |   4.0 |           89 | ON    |         0 |         1 |
| Toronto | Restaurants | Friday|18:00-23:00    |   4.0 |           89 | ON    |         0 |         1 |
| Toronto | Restaurants | Wednesday|18:00-23:00 |   4.0 |           89 | ON    |         0 |         1 |
| Toronto | Restaurants | Thursday|18:00-23:00  |   4.0 |           89 | ON    |         0 |         1 |
| Toronto | Restaurants | Saturday|18:00-23:00  |   4.0 |           89 | ON    |         0 |         1 |
| Toronto | Restaurants | Monday|10:30-21:00    |   3.0 |           47 | ON    |         1 |         0 |
| Toronto | Restaurants | Tuesday|10:30-21:00   |   3.0 |           47 | ON    |         1 |         0 |
| Toronto | Restaurants | Friday|10:30-21:00    |   3.0 |           47 | ON    |         1 |         0 |
| Toronto | Restaurants | Wednesday|10:30-21:00 |   3.0 |           47 | ON    |         1 |         0 |
| Toronto | Restaurants | Thursday|10:30-21:00  |   3.0 |           47 | ON    |         1 |         0 |
| Toronto | Restaurants | Sunday|11:00-19:00    |   3.0 |           47 | ON    |         1 |         0 |
| Toronto | Restaurants | Saturday|10:30-21:00  |   3.0 |           47 | ON    |         1 |         0 |
| Toronto | Restaurants | Monday|9:00-23:00     |   3.0 |           34 | ON    |         1 |         0 |
| Toronto | Restaurants | Tuesday|9:00-23:00    |   3.0 |           34 | ON    |         1 |         0 |
| Toronto | Restaurants | Friday|9:00-4:00      |   3.0 |           34 | ON    |         1 |         0 |
| Toronto | Restaurants | Wednesday|9:00-23:00  |   3.0 |           34 | ON    |         1 |         0 |
| Toronto | Restaurants | Thursday|9:00-23:00   |   3.0 |           34 | ON    |         1 |         0 |
| Toronto | Restaurants | Sunday|10:00-23:00    |   3.0 |           34 | ON    |         1 |         0 |
| Toronto | Restaurants | Saturday|10:00-4:00   |   3.0 |           34 | ON    |         1 |         0 |
| Toronto | Restaurants | Monday|11:00-23:00    |   2.0 |            5 | ON    |         1 |         0 |
| Toronto | Restaurants | Tuesday|11:00-23:00   |   2.0 |            5 | ON    |         1 |         0 |
| Toronto | Restaurants | Friday|11:00-23:00    |   2.0 |            5 | ON    |         1 |         0 |
| Toronto | Restaurants | Wednesday|11:00-23:00 |   2.0 |            5 | ON    |         1 |         0 |
| Toronto | Restaurants | Thursday|11:00-23:00  |   2.0 |            5 | ON    |         1 |         0 |
| Toronto | Restaurants | Sunday|11:00-23:00    |   2.0 |            5 | ON    |         1 |         0 |
| Toronto | Restaurants | Saturday|11:00-23:00  |   2.0 |            5 | ON    |         1 |         0 |


2. Group business based on the ones that are open and the ones that are closed. What differences can you find between the ones 
that are still open and the ones that are closed? List at least two differences and the SQL code you used to arrive at your answer.
		
i. Difference 1:
	Since 'group business that are open' have in total 269300 sum(review_count), 'group business that are closed' only have 35261 sum(review_count). 
	So, 'group business that are open' have more reviews than 'group business that are closed'.
	Besides, 'group business that are open' have avg(review_count) about 31.76, 'group business that are closed' have avg(review_count) about 23.20.
	Therefore, 'group business that are open' also have better reviews than 'group business that are closed'.
         
ii. Difference 2:
	As shown in the result below, 'group business that are open' have avg(stars) about 3.68, 'group business that are closed' have avg(stars) about 3.52.
	Therefore, 'group business that are open' have higher average stars rating than 'group business that are closed'.
         
SQL code used for analysis:
```javascript
	select is_open, avg(latitude), avg(longitude),
	sum(review_count), avg(review_count), avg(stars)
	from business
	group by is_open;
```

| is_open | avg(latitude) | avg(longitude) | sum(review_count) | avg(review_count) |    avg(stars) |
--|--|--|--|--|--
|       0 | 38.8135013816 | -92.3074901316 |             35261 |     23.1980263158 | 3.52039473684 |
|       1 | 38.5594333019 | -92.7458396236 |            269300 |     31.7570754717 | 3.67900943396 |

	

3. For this last part of your analysis, you are going to choose the type of analysis you want to conduct on the Yelp dataset and are going to prepare 
the data for analysis.

Ideas for analysis include: Parsing out keywords and business attributes for sentiment analysis, clustering businesses to find commonalities or anomalies 
between them, predicting the overall star rating for a business, predicting the number of fans a user will have, and so on. These are just a few examples 
to get you started, so feel free to be creative and come up with your own problem you want to solve. Provide answers, in-line, to all of the following:
	
i. Indicate the type of analysis you chose to do:
	Clustering businesses by stars rating, and find out the commonalities or anomalies between each stars rating. And use the result to prediting
	the future business's value, latitude, longitude, and review_count if we know its star rating.
         
ii. Write 1-2 brief paragraphs on the type of data you will need for your analysis and why you chose that data:
	I choose data from two table, table business and table attribute, because in these two tables, they contain several columns like value, latitude, 
	longitude, review_count, stars, etc. These data could help me create a table for further sentiment analysis. To be more specific, as shown in the 
	below result, I have group the data by stars. We could find out some interesting phenomenon:
	Between stars from 3.0 to 4.0, there are most business, value, and their reviews. And they also have better average reviews in general.
	Besides, with the stars increasing, the average latitude almost don't change, but the average longtitude has decreasing.
                  
iii. Output of your finished dataset:

| name                     | count(*) | sum(value) | avg(latitude) | avg(longitude) | avg(review_count) | sum(review_count) | stars |
--|--|--|--|--|--|--|--
| Burger King              |        5 |          2 |       41.7151 |       -81.2996 |               4.0 |                20 |   1.0 |
| Royal Dumpling           |        7 |        3.0 |       43.7752 |        -79.414 |               4.0 |                28 |   1.5 |
| Ghost Armor SS Springs   |       62 |       53.0 | 40.4840387097 | -82.0749045161 |     6.20967741935 |               385 |   2.0 |
| Papa Da Vinci            |       79 |       47.0 | 38.3523708861 |  -93.725264557 |     17.6835443038 |              1397 |   2.5 |
| Cardiac Solutions        |      193 |       91.0 | 41.9755170984 | -75.5360211399 |     49.7564766839 |              9603 |   3.0 |
| Poutine Lafleur          |      170 |       86.0 | 38.3326076471 | -94.9224229412 |     42.5941176471 |              7241 |   3.5 |
| Edulis                   |      182 |       96.0 | 38.7087873626 | -95.3600736264 |     116.104395604 |             21131 |   4.0 |
| Oaks Golf Course         |       48 |       33.0 | 37.4904041667 | -99.9474958333 |     8.89583333333 |               427 |   4.5 |
| Back-Health Chiropractic |       41 |       31.0 | 36.0819463415 | -102.581919512 |     8.31707317073 |               341 |   5.0 |

         
iv. Provide the SQL code you used to create your final dataset:
```javascript
	select business.name, count(*), sum(value), 
	avg(latitude), avg(longitude),
	avg(review_count), sum(review_count), stars
	from business
	inner join attribute
	on business.id = attribute.business_id
	group by stars;
```
