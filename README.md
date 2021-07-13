# SQL_CheatSheet

## Manipulation:

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

### ALTER TABLE Statement
The **ALTER TABLE** statement is used to modify the columns of an existing table. When combined with teh **ADD COLUMN** clause, it is used to add a new column.
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
- **DEFAULT** assigns a default value for the oclumn when no value is specified.
```SQL
CREATE TABLE student (
  id INTEGER PRIMARY KEY,
  name TEXT UNIQUE,
  grade INTEGER NOT NULL,
  age INTEGER DEFAULT 10
);
