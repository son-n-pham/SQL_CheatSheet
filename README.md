# SQL_CheatSheet

## Manipulation:

### CREATE TABLE Statement
The **CREATE TABLE** statement creates a new table in a database.
```
CREATE TABLE table_name (
  column1 datatype,
  column2 datatype,
  column3 datatype,
 )
 ```

### INSERT Statement
The **INSERT INTO** statement is used to add a new record (row) to a table, which has 2 forms:

> -- Insert into columns in order:
> INSERT INTO table_name
> VALUES (value1, value2);
 
> -- Insert into columns by name:
> INSERT INTO table_name (column1, column2)
> VALUES (value1, value2);
