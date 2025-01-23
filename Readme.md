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

#### sort data by column:

```sql
SELECT columns FROM table_name ORDER BY column_name;
```

#### adding a primary key in a column

```sql
ALTER TABLE table_name ADD PRIMARY KEY(colum_name);
```

#### to drop a constraint from a table in psql

```sql
ALTER TABLE table_name DROP CONSTRAINT constraint_name;
```

Wee can see the name of the constraint in the display table output.
`\d table_name` is the command to display table.

the output should be something like this:

```
mario_database=> \d characters;
                                             Table "public.characters"
+----------------+-----------------------+-----------+----------+--------------------------------------------------+
|     Column     |         Type          | Collation | Nullable |                     Default                      |
+----------------+-----------------------+-----------+----------+--------------------------------------------------+
| character_id   | integer               |           | not null | nextval('characters_character_id_seq'::regclass) |
| name           | character varying(30) |           | not null |                                                  |
| homeland       | character varying(60) |           |          |                                                  |
| favorite_color | character varying(30) |           |          |                                                  |
+----------------+-----------------------+-----------+----------+--------------------------------------------------+
Indexes:
    "characters_pkey" PRIMARY KEY, btree (name)
```

#### creating a foreign key:

```sql
ALTER TABLE table_name ADD COLUMN column_name DATATYPE REFERENCES referece_table_name(reference_column_name);
```
#### unique
To ensure one-to-one relationship, one row in the reference table will be related to exactly one row in the current table. This will be enforced by adding the `UNIQUE` constraint to the foreign key.

```sql
ALTER TABLE table_name ADD UNIQUE(column_name);
```

#### Creating table with the primary key
```sql
CREATE TABLE sounds(column_name DATA_TYPE CONSTRATINT);
```

#### Adding new column with the fk reference
```sql 
ALTER TABLE table_name ADD COLUMN column_name DATATYPE CONSTRAINT REFERENCES referenced_table_name(referenced_column_name);
```
#### Junction table
Many to many relationship usually use a junction table to link two tables together, forming two one to many relationships.

#### creating a composite primary key 
```sql 
ALTER TABLE table_name ADD PRIMARY KEY (column1, column2);
```

#### Show the relational data using `join` command
```sql
SELECT columns FROM table_1 FULL JOIN table_2 ON table_1.primary_key_column = table_2.foreign_key_column;
```

#### join operations in the junction table (many-to-many relationship)
```sql
SELECT columns FROM junction_table
FULL JOIN table_1 ON junction_table.foreign_key_column = table_1.primary_key_column
FULL JOIN table_2 on junction_table.foreign_key_column = table2.primary_key_column;
```
