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

```sql
CREATE TABLE table_name();
```

View more details about the table:

```postgresql
\d table_name;
```

#### adding a new column in table

```sql
ALTER TABLE table_name ADD COLUMN column_name DATATYPE;
```

#### delete any column:

```sql
ALTER TABLE table_name DROP COLUMN column_name;
```

#### renaming a column

```sql
ALTER TABLE table_name RENAME COLUMN column_name TO new_name;
```

#### insert data/row in a table

```sql
INSERT INTO table_name(column1, column2) VALUES(value1, value2);
```

#### To view the data of a table

```sql
SELECT columns FROM table_name;
```

To see alll the columns in a table, use an `*` to denote that you want to see all the columns.

#### deleting a row from a table

```sql
DELETE FROM table_name WHERE condition;
```

For example, if we want to remove the row from table named `second_table` where `username` is `Luigi` then the querry will be:

```sql
DELETE FROM second_table WHERE username='Luigi';
```

#### How to delete a table
```sql
DROP TABLE table_name;
```

#### renameing a database:

```sql
ALTER TABLE database_name RENAME TO new_database_name;
```

### data type
#### serial:
This will make the column an `int` wwwith a `not null` constraint and automatically increment the integer when a new row is added. 

#### Adding multiple row at a time
Adding rows one at a time is quite tedious. Here's an example of how you could have added the three rows at once:
```sql
INSERT INTO characters(name, homeland, favorite_color)
VALUES('Mario', 'Mushroom Kingdom', 'Red'),
('Luigi', 'Mushroom Kingdom', 'Green'),
('Peach', 'Mushroom Kingdom', 'Pink');
```

#### Update information from a row

```sql
UPDATE table_name SET column_name=new_value WHERE condition;
```