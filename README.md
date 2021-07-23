# SQL CheatSheet

- [SQL CheatSheet](#sql-cheatsheet)
  * [MANIPULATION:](#manipulation-)
    + [CREATE TABLE Statement](#create-table-statement)
    + [INSERT Statement](#insert-statement)
    + [UPDATE Statement](#update-statement)
    + [ALTER TABLE Statement](#alter-table-statement)
    + [DELETE Statement](#delete-statement)
    + [Column Constraints](#column-constraints)
  * [QUERIES:](#queries-)
    + [SELECT Statement:](#select-statement-)
    + [AS Clause](#as-clause)
    + [DISTINCT Clause](#distinct-clause)
    + [WHERE Clause](#where-clause)
    + [LIKE  Operator](#like--operator)
    + [NULL Values](#null-values)
    + [BETWEEN Operator](#between-operator)
    + [AND Operator](#and-operator)
    + [OR Opertor](#or-opertor)
    + [ORDER BY Clause](#order-by-clause)
    + [LIMIT Clause](#limit-clause)

<small><i><a href='http://ecotrust-canada.github.io/markdown-toc/'>Table of contents generated with markdown-toc</a></i></small>


## MANIPULATION:

### CREATE TABLE Statement
The **CREATE TABLE** statement creates a new table in a database.
```SQL
CREATE TABLE table_name (
  column1 datatype,
  column2 datatype,
  column3 datatype,
 )
 ```

### INSERT Statement
The **INSERT INTO** statement is used to add a new record (row) to a table, which has 2 forms:
```SQL
-- Insert into columns in order:
INSERT INTO table_name
VALUES (value1, value2);
 
-- Insert into columns by name:
INSERT INTO table_name (column1, column2)
VALUES (value1, value2);
```

### UPDATE Statement
It is used to edit records (rows) in a table. It includes a **SET** clause that indicates the column to edit and a **WHERE** clause for specifiying the records(s)
```SQL
UPDATE table_name
SET column1 = value1, column2 = value2
WHERE some_column = some_value;
```

### ALTER TABLE Statement
The **ALTER TABLE** statement is used to modify the columns of an existing table. When combined with the **ADD COLUMN** clause, it is used to add a new column.
```SQL
ALTER TABLE table_name
ADD column_name datetype;
```

### DELETE Statement
The **DELETE** statement is used to delete records (rows) is a table. The **WHERE** clause specifies which record or records that should be deleted. If the **WHERE** clause is omitted, all records will be deleted.
```SQL
DELETE FROM table_name
WHERE some_column = some_value;
```

### Column Constraints
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
## QUERIES:

### SELECT Statement: is the clause we use every time we want to query information from a database.
The <b>SELECT *</b> statement returns all columns from the provided table in the result. We can also select any column by its header.

```SQL
SELECT *
FROM movies;
```

### AS Clause: renames a column or table.
Columns or tables can be aliased using <b>AS</b> clause.

```SQL
SELECT name AS 'movie_title'
FROM movies;
```

### DISTINCT Clause: return unique values.
This is used to select unique values of a column.

```SQL
SELECT DISTINCT city
FROM contact_details;
```

### WHERE Clause: is a popular command to filter the results of the query based on specified conditions.
This is used to filter records (rows) matching a certain ncondition. This below example select all rows where the pub_year equals 2017.

```SQL
SELECT title
FROM library
WHERE pub_year = 2017;
```

### LIKE  Operator
This operator can be used inside a **WHERE** clause. There are 2 wildcard can be used with **LIKE**:
- _ Wildcard: is used to match any single unspecified character.
  
  ```SQL
  SELECT name
  FROM movies
  WHERE name LIKE '_ove';
  ```  
  
- % Wildcard: ised used match to match zero or more unspecified characters. Below example will match any movies starting with "The"
  
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
### ORDER BY Clause: sorts the result.
This can be used to sort the result by particular column in descending (with **DESC** keyword) or ascending (with **ASC** keyword) order.

```SQL
SELECT *
FROM contacts
ORDER BY birth_date DESC;
```

### LIMIT Clause: specifies the maximum number of rows that the query will return.
This is used to narrow or limit the result. The below example is to select 5 rows.

```SQL
SELECT *
FROM movies
LIMIT 5;
```

### CASE Statement: creates different outputs.
This is SQL's way of handling if-then logic.

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

OR operator can be used to have the same result as above.

```SQL
SELECT name,
  CASE
    WHEN genre = 'romance' OR genre = 'comedy' THEN 'Chill'
    ELSE 'Intense'
  END AS 'Mood'
FROM movies;
```
