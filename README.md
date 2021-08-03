# SQL CheatSheet

- [SQL CheatSheet](#sql-cheatsheet)
  * [MANIPULATION](#manipulation)
    + [CREATE TABLE Statement creates a new table.](#create-table-statement-creates-a-new-table)
    + [INSERT INTO Statement adds a new row to a table.](#insert-into-statement-adds-a-new-row-to-a-table)
    + [UPDATE Statement edits a row in a table.](#update-statement-edits-a-row-in-a-table)
    + [ALTER TABLE Statement changes an existing table.](#alter-table-statement-changes-an-existing-table)
    + [DELETE Statement deletes rows from a table.](#delete-statement-deletes-rows-from-a-table)
    + [Column Constraints add information about how a column can be used.](#column-constraints-add-information-about-how-a-column-can-be-used)
  * [QUERIES](#queries)
    + [SELECT Statement is the clause we use every time we want to query information from a database.](#select-statement-is-the-clause-we-use-every-time-we-want-to-query-information-from-a-database)
    + [AS Clause renames a column or table by an alias.](#as-clause-renames-a-column-or-table-by-an-alias)
    + [DISTINCT Clause returns unique values.](#distinct-clause-returns-unique-values)
    + [WHERE Clause is a popular command to filter the results of the query based on specified conditions.](#where-clause-is-a-popular-command-to-filter-the-results-of-the-query-based-on-specified-conditions)
    + [LIKE Operator](#like-operator)
      - [_ Wildcard is used to match any single unspecified character.](#--wildcard-is-used-to-match-any-single-unspecified-character)
      - [% Wildcard is used to match zero or more unspecified characters.](#--wildcard-is-used-to-match-zero-or-more-unspecified-characters)
    + [NULL Values](#null-values)
    + [BETWEEN Operator](#between-operator)
    + [AND Operator](#and-operator)
    + [OR Opertor](#or-opertor)
    + [ORDER BY Clause sorts the result.](#order-by-clause-sorts-the-result)
    + [LIMIT Clause specifies the maximum number of rows that the query will return.](#limit-clause-specifies-the-maximum-number-of-rows-that-the-query-will-return)
    + [CASE Statement creates different outputs.](#case-statement-creates-different-outputs)
  * [AGGREGATE](#aggregate)
    + [COUNT counts the number of rows](#count-counts-the-number-of-rows)
    + [SUM returns the sum of the values in a column](#sum-returns-the-sum-of-the-values-in-a-column)
    + [MAX and MIN returns the largest and smallest values in a column](#max-and-min-returns-the-largest-and-smallest-values-in-a-column)
    + [AVG returns the average in a column](#avg-returns-the-average-in-a-column)
    + [ROUND rounds the values in a column](#round-rounds-the-values-in-a-column)
    + [GROUP BY groups the values in a column before other operation](#group-by-groups-the-values-in-a-column-before-other-operation)
    + [HAVING filter groups from GROUP BY](#having-filter-groups-from-group-by)
  * [MULTIPLES TABLES](#multiples-tables)
    + [INNER JOIN returns table with rows match the ON condition](#inner-join-returns-table-with-rows-match-the-on-condition)
    + [LEFT JOIN](#left-join)
    + [Primary Key vs Foreign Key](#primary-key-vs-foreign-key)
    + [CROSS JOIN combines all rows of one table with all rows of another table](#cross-join-combines-all-rows-of-one-table-with-all-rows-of-another-table)
    + [UNION allows to stack one table on top of the other table](#union-allows-to-stack-one-table-on-top-of-the-other-table)
    + [WITH is used to combine two tables but at least one of them is the result of another calculation.](#with-is-used-to-combine-two-tables-but-at-least-one-of-them-is-the-result-of-another-calculation)

<small><i><a href='http://ecotrust-canada.github.io/markdown-toc/'>Table of contents generated with markdown-toc</a></i></small>

*Cheatsheet is referred from materials of Codecademy*

<hr>
:muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle::muscle:
<hr>

## DOT COMMANDS

Once in sqlite3, *.help* will list all available dot command.

![image](https://user-images.githubusercontent.com/79841341/127645989-c35a382f-e432-4acc-9297-b9f282ef5eb7.png)

I find some commands helpful to me. More will be added if I found them useful during the course.
- .tables list all tables
- .headers on|off to toogle header row
- .fullschhema to show the schema of the table

<hr>
:ok_hand: :ok_hand: :ok_hand: :ok_hand: :ok_hand: :ok_hand: :ok_hand: :ok_hand: :ok_hand: :ok_hand: :ok_hand: :ok_hand: :ok_hand: :ok_hand: :ok_hand: :ok_hand: :ok_hand: :ok_hand: :ok_hand: :ok_hand: :ok_hand: :ok_hand: :ok_hand: :ok_hand: :ok_hand: :ok_hand: 
<hr>

## MANIPULATION

### CREATE TABLE Statement creates a new table.
The **CREATE TABLE** statement creates a new table in a database.
```SQL
CREATE TABLE table_name (
  column1 datatype,
  column2 datatype,
  column3 datatype,
 )
 ```

### INSERT INTO Statement adds a new row to a table.
The **INSERT INTO** statement is used to add a new record (row) to a table, which has 2 forms:
```SQL
-- Insert into columns in order:
INSERT INTO table_name
VALUES (value1, value2);
 
-- Insert into columns by name:
INSERT INTO table_name (column1, column2)
VALUES (value1, value2);
```

### UPDATE Statement edits a row in a table.
It is used to edit records (rows) in a table. It includes a **SET** clause that indicates the column to edit and a **WHERE** clause for specifiying the records(s)
```SQL
UPDATE table_name
SET column1 = value1, column2 = value2
WHERE some_column = some_value;
```

### ALTER TABLE Statement changes an existing table.
The **ALTER TABLE** statement is used to modify the columns of an existing table. When combined with the **ADD COLUMN** clause, it is used to add a new column.
```SQL
ALTER TABLE table_name
ADD column_name datetype;
```

### DELETE Statement deletes rows from a table.
The **DELETE** statement is used to delete records (rows) is a table. The **WHERE** clause specifies which record or records that should be deleted. If the **WHERE** clause is omitted, all records will be deleted.
```SQL
DELETE FROM table_name
WHERE some_column = some_value;
```

### Column Constraints add information about how a column can be used.
They are rules applied to the values of individual columns:
- **PRIMARY KEY** constraint can be used to uniquely identify the row. There can be only one **PRIMARY KEY** column per table.
- **UNIQUE** columns have a different value for every row. There can be multiple **UNIQUE** columns.
- **NOT NULL** columns must have a value.
- **DEFAULT** assigns a default value for the column when no value is specified.
```SQL
CREATE TABLE student (
  id INTEGER PRIMARY KEY,
  name TEXT UNIQUE,
  grade INTEGER NOT NULL,
  age INTEGER DEFAULT 10
);
```

<hr>
:muscle: :muscle: :muscle: :muscle: :muscle: :muscle: :muscle: :muscle: :muscle: :muscle: :muscle: :muscle: :muscle: :muscle: :muscle: :muscle: :muscle: :muscle: :muscle: :muscle: :muscle: :muscle: :muscle: :muscle: :muscle: :muscle: :muscle: :muscle: :muscle: :muscle: 
<hr>

## QUERIES

### Structure of a query
Typical of a query is:

```SQL
SELECT <column>
FROM <table>
WHERE <rowconditions>
GROUP BY groups
HAVING groupconditions
ORDER BY sortcolumns
LIMIT numrows;
```

### SELECT Statement is the clause we use every time we want to query information from a database.
The <b>SELECT *</b> statement returns all columns from the provided table in the result. We can also select any column by its header.

```SQL
SELECT *
FROM movies;
```

### AS Clause renames a column or table by an alias.
Columns or tables can be aliased using <b>AS</b> clause.

```SQL
SELECT name AS 'movie_title'
FROM movies;
```

### DISTINCT Clause returns unique values.
This is used to select unique values of a column.

```SQL
SELECT DISTINCT city
FROM contact_details;
```

### WHERE Clause is a popular command to filter the results of the query based on specified conditions.
This is used to filter records (rows) matching a certain ncondition. This below example select all rows where the pub_year equals 2017.

```SQL
SELECT title
FROM library
WHERE pub_year = 2017;
```

### LIKE Operator
This operator can be used inside a **WHERE** clause. There are 2 wildcard can be used with **LIKE**:
#### _ Wildcard is used to match any single unspecified character.
  
  ```SQL
  SELECT name
  FROM movies
  WHERE name LIKE '_ove';
  ```  
  
#### % Wildcard is used to match zero or more unspecified characters. 
Below example will match any movies starting with "The"
  
  ```SQL
  SELECT name
  FROM movies
  WHERE name LIKE 'The%';
  ```
 
### NULL Values
NULL value can be matched or not matched by using **IS NULL** or **IS NOT NULL** and WHERE clause.

```SQL
SELECT address
FROM records
WHERE address IS NOT NULL;
```

### BETWEEN Operator

```SQL
SELECT *
FROM movies
WHERE year BETWEEN 1980 AND 1990;
```

### AND Operator

```SQL
SELECT model
FROM cars
WHERE color = 'blue'
  AND year > 2014;
```
  
### OR Opertor

```SQL
SELECT name
FROM customers
WHERE state = 'CA'
  OR state = 'NY';
```
### ORDER BY Clause sorts the result.
This can be used to sort the result by particular column in descending (with **DESC** keyword) or ascending (with **ASC** keyword) order.

```SQL
SELECT *
FROM contacts
ORDER BY birth_date DESC;
```

### LIMIT Clause specifies the maximum number of rows that the query will return.
This is used to narrow or limit the result. The below example is to select 5 rows.

```SQL
SELECT *
FROM movies
LIMIT 5;
```

### CASE Statement creates different outputs.
This is SQL's way of handling if-then logic. This will return a new column.

```SQL
SELECT name,
  CASE
    WHEN genre = 'romance' THEN 'Chill'
    WHEN genre = 'comedy' THEN 'Chill'
    ELSE 'Intense'
  END
FROM movies;
```
![image](https://user-images.githubusercontent.com/79841341/126802950-3effc9fc-b618-4675-b50d-3e2db157fc00.png)

```SQL
SELECT name,
  CASE
    WHEN genre = 'romance' THEN 'Chill'
    WHEN genre = 'comedy' THEN 'Chill'
    ELSE 'Intense'
  END AS 'Mood'
FROM movies;
```

![image](https://user-images.githubusercontent.com/79841341/126803072-467b61a2-4b0d-4ff9-bc4d-6114699cebf7.png)

OR operator can be used to have the same result as the above.

```SQL
SELECT name,
  CASE
    WHEN genre = 'romance' OR genre = 'comedy' THEN 'Chill'
    ELSE 'Intense'
  END AS 'Mood'
FROM movies;
```

<hr>
:innocent: :innocent: :innocent: :innocent: :innocent: :innocent: :innocent: :innocent: :innocent: :innocent: :innocent: :innocent: :innocent: :innocent: :innocent: :innocent: :innocent: :innocent: :innocent: :innocent: :innocent: :innocent: :innocent: :innocent: 
<hr>

## AGGREGATE

### COUNT counts the number of rows

### SUM returns the sum of the values in a column

### MAX and MIN returns the largest and smallest values in a column

### AVG returns the average in a column

### ROUND rounds the values in a column

### GROUP BY groups the values in a column before other operation
*GROUP BY* comes after *WHERE* but before *ORDER BY* or *LIMIT*.

```SQL
SELECT year, AVG(imdb_rating)
FROM movies
GROUP BY year
ORDER BY year DESC
LIMIT 3;
```

*GROUP BY* allows to use number index to replace column in SELECT. The below give the same result.

```SQL
SELECT ROUND(imdb_rating),
   COUNT(name)
FROM movies
GROUP BY ROUND(imdb_rating)
ORDER BY ROUND(imdb_rating);
```

```SQL
SELECT ROUND(imdb_rating),
   COUNT(name)
FROM movies
GROUP BY 1
ORDER BY 2;
```

### HAVING filter groups from GROUP BY
*HAVING* comes after *GROUP BY* and before *ORDER BY* and *LIMIT*.
- HAVING filters groups
- WHERE filters rows (records)

```SQL
SELECT price,
  ROUND(AVG(downloads)),
  COUNT(*)
FROM fake_apps
GROUP BY price
HAVING COUNT(*) > 10;
```

<hr>
:grinning: :grinning: :grinning: :grinning: :grinning: :grinning: :grinning: :grinning: :grinning: :grinning: :grinning: :grinning: :grinning: :grinning: :grinning: :grinning: :grinning: :grinning: :grinning: :grinning: :grinning: :grinning: :grinning: :grinning: 
<hr>

## MULTIPLES TABLES

### INNER JOIN returns table with rows match the ON condition
INNER JOIN is the default JOIN function.

```SQL
SELECT *
FROM table1
JOIN table2
on table1.C2 = table2.C2;
```

![inner_join](https://content.codecademy.com/courses/learn-sql/multiple-tables/inner-join.gif)

### LEFT JOIN
*LEFT JOIN* keeps all rows from the first table regardless of matching with second table.

```SQL
SELECT *
FROM table1
LEFT JOIN table2
on table1.C2 = table2.C2;
```

![left_join](https://content.codecademy.com/courses/learn-sql/multiple-tables/left-join.gif)

### Primary Key vs Foreign Key
Each table has a column, *primary key*, that uniquely identifies each of row.

*Primary keys* have a few requirements:
- None of the value is NULL
- Each value must be unique
- A table can only have one primary key column

When the *primary key* of one table appears in a different table, it is called a foreign key of that table.

Why is this important? JOIN usually joins a foreign key from one table with the primary key from another table.

### CROSS JOIN combines all rows of one table with all rows of another table
A common usage of *CROSS JOIN* is to compare each row of a table to a list of values.

Example of *CROSS JOIN*:

```SQL
SELECT shirts.shirt_color,
  pants.pants_color
FROM shirts
CROSS JOIN pants;
```

### UNION allows to stack one table on top of the other table
Strict rules are applied for this appending data:
- Tables must have the same number of columns.
- The columns must have the same data types in the same order as the first table.

```SQL
SELECT *
FROM table1
UNION
SELECT *
FROM table2;
```

### WITH combines two tables which at least one of them is the result of another calculation.
Let's dive into an example to understand *WITH*

```SQL
WITH previous_query AS (
  SELECT customer_id,
   COUNT(subscription_id) AS 'subscriptions'
  FROM orders
  GROUP BY customer_id
)
SELECT customers.customer_name,
  previous_query.subscriptions
FROM previous_query
JOIN customers
ON previous_query.customer_id = customers.customer_id
```

*WITH* is used to create an aliased table previous_query whose whole query syntax is put into () after AS. Then the aliased previous_query can be used as a normal table to JOIN with the customer table.
