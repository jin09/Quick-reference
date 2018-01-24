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
