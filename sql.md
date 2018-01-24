# SQL

## Create Table

```sql
CREATE TABLE celebs (id INTEGER, name TEXT, age INTEGER);
```

## Insert

```sql
INSERT INTO celebs (id, name, age) VALUES (1, 'Justin Bieber', 21);
```

## Update

```sql
UPDATE celebs 
SET age = 22 
WHERE id = 1; 

SELECT * FROM celebs;
```

## Alter Table Properties

```sql
ALTER TABLE celebs ADD COLUMN twitter_handle TEXT; 
```

## Delete Rows

```sql
DELETE FROM celebs WHERE twitter_handle IS NULL; 
```

## Create Table with constraints

```sql
CREATE TABLE awards (
  id INTEGER PRIMARY KEY,
  recipient TEXT NOT NULL,
  award_name TEXT DEFAULT "Grammy");
  
  
CREATE TABLE celebs (
    id INTEGER PRIMARY KEY, 
    name TEXT UNIQUE,
    date_of_birth TEXT NOT NULL,
    date_of_death TEXT DEFAULT 'Not Applicable',
);
```

## `As` in SQL

`AS` is a keyword in SQL that allows you to rename a column or table using an alias.  
The new name can be anything you want as long as you put it inside of single quotes.  
Here we renamed the name column as Movies.  

It is important to remember that the columns have not been renamed in the table.  
The aliases only appear in the result.  

```sql
SELECT name AS 'lala', imdb_rating AS 'IMDb'
 FROM movies;
 
 ## `Distinct`
 
 ```sql
 SELECT DISTINCT genre 
 FROM movies;
```

## `Where` clause

```sql
SELECT * 
 FROM movies 
 WHERE imdb_rating < 5;
```

## `Like` clause

```sql
SELECT * 
 FROM movies
 WHERE name LIKE 'Se_en';
 
SELECT * 
 FROM movies
 WHERE name LIKE '%ee%';
```
## `IS NULL` or `IS NOT NULL`

we cannot use `=` or `!=` with NULL so we have `IS NULL` and `IS NOT NULL`  

```sql
SELECT name
 FROM movies 
 WHERE imdb_rating IS NULL;
```

## `Between` 

This statement filters the result set to only include movies with names  
that begin with letters 'A' up to but not including 'J'.  

```sql
SELECT *
 FROM movies
 WHERE name BETWEEN 'A' AND 'J';
```

In this statement, the BETWEEN operator is being used to filter the result  
set to only include movies with years between 1990 up to and including 1999.  

```sql
 SELECT *
 FROM movies
 WHERE year BETWEEN 1990 AND 1999;
```

**Numbers are inclusive but letters are exclusive**  

## Order By

**It goes after where condition**  

```sql
SELECT name, year
 FROM movies
 ORDER BY name;
```

## `Case`

Programmatically set values to a new column  
The following query creates a new column called `review` and  
we are able to set values programatically using `when` and `then`  

```sql
SELECT name,
 CASE
  WHEN imdb_rating > 7 THEN 'Good'
  WHEN imdb_rating > 5 THEN 'Okay'
 END as 'review'
FROM movies;
```
A more detail example with default else statement  

```sql
SELECT name,
 CASE
  WHEN genre = 'romance' THEN 'fun'
  WHEN genre = 'comedy' THEN 'fun'
  ELSE 'serious'
 END as 'mood'
FROM movies;
```

## Aggregate

Here is a quick preview of some important aggregates that we will cover in the next five exercises:  

`COUNT`: count the number of values  
`SUM`: add up all of the values in a column  
`MAX/MIN`: get the largest/smallest value  
`AVG`: get the mean for all values in a column  
`ROUND`: round the values in the column  

### Count

COUNT is a function that takes the name of a column as an argument and  
counts the number of non-empty values in that column.  

```sql
SELECT COUNT(*)
 FROM table_name;
```

```sql
SELECT COUNT(*) 
 FROM fake_apps where price = 0;
 ```
 
 ### SUM
 
 SQL makes it easy to add all values in a particular column using SUM.

SUM is a function that takes the name of a column as an argument and  
returns the sum of all the values in that column.  

```sql
SELECT SUM(downloads)
 FROM fake_apps;
 ```

### MIN

```sql
SELECT MIN(downloads)
 FROM fake_apps;
 ```
 
 ### Average
 
 SQL uses the AVG function to quickly calculate the  
 average value of a particular column.

The statement below returns the average number of downloads  
for an app in our database:

```sql
SELECT AVG(downloads)
  FROM fake_apps;
```

The AVG function works by taking a column name as an argument  
and returns the average value for that column.  

### ROUND

By default, SQL tries to be as precise as possible without rounding.  
We can make the result set easier to read using the ROUND function.  

ROUND function takes two arguments inside the parenthesis:  

~ a column name  
~ an integer  

It rounds the values in the column to the number of decimal places specified by the integer.  

```sql
SELECT ROUND(price, 0)
 FROM fake_apps;
 ```
 round it to 0 decimal places  
 
 ```sql
 SELECT round(AVG(price), 2)
 FROM fake_apps;
 ```
 rounds off to 2 decimal places
 
 ### Group By
 
 For instance, we might want to know the mean IMDb ratings for all  
 movies each year. We could calculate each number by a series of queries  
 with different WHERE statements, like so:  
 
 ```sql
 SELECT AVG(imdb_rating)
 FROM movies
 WHERE year = 1999;

 SELECT AVG(imdb_rating)
 FROM movies
 WHERE year = 2000;

 SELECT AVG(imdb_rating)
 FROM movies
 WHERE year = 2001;
 ```
 We can do this by `group by`  
 
 ```sql
 SELECT year,
    AVG(imdb_rating)
 FROM movies
 GROUP BY year
 ORDER BY year;
 ```

The `GROUP BY` statement comes after any `WHERE` statements, but before `ORDER BY` or `LIMIT`.  

### Question:
**add a WHERE clause to count the total number of apps that has been  
downloaded more than 20,000 times, at each price.**  

```sql
SELECT price, COUNT(*) 
 FROM fake_apps 
 where downloads > 20000
 GROUP BY price;
 ```
 
 Sometimes, we want to GROUP BY a calculation done on a column.

For instance, we might want to know how many movies have IMDb ratings  
that round to 1, 2, 3, 4, 5. We could do this using the following syntax:  

```sql
 SELECT ROUND(imdb_rating),
    COUNT(name)
 FROM movies
 GROUP BY ROUND(imdb_rating)
 ORDER BY ROUND(imdb_rating);
 ```
 However, this query may be time-consuming to write and more prone to error.  
 
 SQL lets us use column reference(s) in our GROUP BY that will make our lives easier.  

* 1 is the first column selected
* 2 is the second column selected
* 3 is the third column selected
and so on.  

The following query is equivalent to the above:  

```sql
SELECT ROUND(imdb_rating),
    COUNT(name)
 FROM movies
 GROUP BY 1
 ORDER BY 1;
 ```
 
 ```sql
 SELECT category, 
    price,
    AVG(downloads)
 FROM fake_apps
 GROUP BY 1, 2;
 ```
 
 ### `Having` 
 
 Used to filter the grouped data, so written after `group by`  
 
 ```sql
 SELECT year,
    genre,
    COUNT(name)
 FROM movies
 GROUP BY 1, 2
 HAVING COUNT(name) > 10
 
 
 
 SELECT price, 
    ROUND(AVG(downloads))
 FROM fake_apps
 GROUP BY price
 having  count(*) > 9;
 ```
 
 ## Combine table on common data using `join`
 
 ### Inner joins `join`
 
 **This join is called inner join**
 
 ```sql
 SELECT orders.order_id,
       customers.customer_name
FROM orders JOIN customers ON orders.customer_id = customers.customer_id
```
When we perform a simple JOIN (often called an inner join) our  
result only include rows that match our ON condition.

![Image](../master/assets/inner-join.gif?raw=true)

### `LEFT OUTER JOIN`

SQL lets us do this through a command called `LEFT JOIN`.  
A left join will keep all rows from the first table, regardless  
of whether there is a matching row in the second table.

```sql
select * 
from newspaper left join online on newspaper.id = online.id;
```

![Image](../master/assets/left-join.gif?raw=true)  

### `RIGHT OUTER JOIN`

Similar to `left outer join`, where we show dominant records of right table  

```sql
select * 
from newspaper right join online on newspaper.id = online.id;
```
extra records of right table will be shown  

### `FULL OUTER JOIN`  

Non matching records of both tables will be shown.  

```sql
select * 
from newspaper full outer join online on newspaper.id = online.id;
```

### CROSS JOIN

Also called, `CARTESIAN PRODUCT`.  

```sql
select month,
  COUNT(*) as subscribers
from newspaper cross join months
where month > start_month and month < end_month
group by month;
```

## Union

Append query outputs one after the other only if they are of same type  

* Each SELECT statement within UNION must have the same number of columns
* The columns must also have similar data types
* The columns in each SELECT statement must also be in the same order

```sql
// Doesn't allow duplicate columns
SELECT column_name(s) FROM table1
UNION
SELECT column_name(s) FROM table2;

//alloes duplicate data as well

SELECT column_name(s) FROM table1
UNION ALL
SELECT column_name(s) FROM table2;
```

## `With` give query result a name alias and treat it like usual table

Using `with` we can give a query result a name and later use it as a table in  
a query. Maybe if I want to join the calculated result to another table, that way I can use  
the `with` operator to give an `alias` to a query.  

```sql
WITH previous_query as  
(SELECT customer_id,
       COUNT(subscription_id) as subscriptions
FROM orders
GROUP BY customer_id)
select customers.customer_name, previous_query.subscriptions
from previous_query join customers on previous_query.customer_id = customers.customer_id;
```

## Nested Queries using `IN` operator

1. find flight information about flights where the origin elevation is less than 2000 feet.
```sql
SELECT * 
FROM flights 
WHERE origin in (
    SELECT code 
    FROM airports 
    WHERE elevation < 2000);
```

## Complex Query 

```sql
SELECT a.dep_month,
       a.dep_day_of_week,
       AVG(a.flight_count) AS average_flights
  FROM (
        SELECT dep_month,
              dep_day_of_week,
               dep_date,
               COUNT(*) AS flight_count
          FROM flights
         GROUP BY 1,2,3
       ) a
 GROUP BY 1,2
 ORDER BY 1,2;
 ```

```sql
SELECT id
FROM flights AS f
WHERE distance < (
 SELECT AVG(distance)
 FROM flights
 WHERE carrier = f.carrier);
 ```

```sql
SELECT id, avg(a.sale_price) FROM (
  SELECT id, sale_price FROM order_items
  UNION ALL
  SELECT id, sale_price FROM order_items_historic) AS a 
  GROUP BY 1;
  ```
