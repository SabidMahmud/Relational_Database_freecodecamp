## Learning PostgreSQL

#### starting the database

`psql --username=name --dbname=postgres`

**list the existing databases:**
`\l` this will list the existing databases in the system.

#### **Creating the first database**

```
CREATE DATABASE database_name;
```

#### Connecting to a database:

```
\c database_name;
```

#### display the tables in the databse:

```
\d
```

#### Creating table in the db:

```
CREATE TABLE table_name();
```

View more details about the table:

```
\d table_name;
```

#### adding a new column in table

```
ALTER TABLE table_name ADD COLUMN column_name DATATYPE;
```

#### delete any column:

```
ALTER TABLE table_name DROP COLUMN column_name;
```

#### renaming a column

```
ALTER TABLE table_name RENAME COLUMN column_name TO new_name;
```

#### insert data/row in a table

```
INSERT INTO table_name(column1, column2) VALUES(value1, value2);
```

#### To view the data of a table

```
SELECT columns FROM table_name;
```

To see alll the columns in a table, use an `*` to denote that you want to see all the columns.

#### deleting a row from a table

```
DELETE FROM table_name WHERE condition;
```

For example, if we want to remove the row from table named `second_table` where `username` is `Luigi` then the querry will be:

```
DELETE FROM second_table WHERE username='Luigi';
```

#### How to delete a table
```
DROP TABLE table_name;
```

