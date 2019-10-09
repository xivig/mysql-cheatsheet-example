# mysql-cheatsheet-exaple
Mysql cheat sheet for beginners
## DML

1
### A) CREATE DATABASE
**Example:**
```sql
DROP DATABASE IF EXISTS sample_database;
CREATE DATABASE sample_database;
USE sample_database;
```
### B) CREATE TABLE
**Example:**
```sql
-- create a table naming sample_table  
CREATE TABLE sample_table (
    id int(11) not null AUTO_INCREMENT PRIMARY KEY,
    name varchar(100) not null,
    cell_no varchar(50) not null
    );
```
```sql
-- select database  
USE sample_database;
```
```sql
-- shows all tables in the selected database  
SHOW TABLES;
```
```sql
-- shows table structure and data fields ** DESCRIBE command is only for table 
DESCRIBE sample_table;
```
**Example:**
```sql
DROP TABLE IF EXISTS `sample_table`;
CREATE TABLE IF NOT EXISTS `sample_table` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(100) NOT NULL,
  `cell_no` varchar(50) NOT NULL,
  `email` varchar(100) NOT NULL UNIQUE,
  PRIMARY KEY (`id`)
) ENGINE=MyISAM AUTO_INCREMENT=8 DEFAULT CHARSET=latin1;
```
2
### A) ALTER DATABASE
```sql
-- renaming a database from mysql operation tab
CREATE DATABASE sample_database1 / DROP DATABASE sample_database;
``` 
### B) ALTER TABLE
**Example:**
```sql
-- add a new column naming `last_name` after `name`
ALTER TABLE `sample_table` ADD `last_name` VARCHAR(100) NOT NULL AFTER `name`;
```
```sql
-- renaming name coumn to first_name
ALTER TABLE `sample_table` CHANGE `name` `first_name` VARCHAR(100) CHARACTER SET latin1 COLLATE latin1_swedish_ci NOT NULL;
```
```sql
-- making cell_no column unique
ALTER TABLE sample_table ADD UNIQUE (cell_no)
```
```sql
-- add a new column to the right of the email
ALTER TABLE `sample_table` ADD `cool` VARCHAR(100) NOT NULL AFTER `email`;
```
```sql
-- delete column cool from the table
ALTER TABLE `sample_table`  DROP `cool`;
```
3
### A) DROP DATABASE
**Example:**
```sql
-- delete a database
DROP DATABASE `sample_database`;
```
### B) DROP TABLE
```sql
DROP TABLE `sample_table1`;
```
4
```sql
-- shows all databases
SHOW DATABASES
```
```sql
-- shows all tables in the selected database
SHOW TABLES
```

DML

1
### SELECT * FROM table_name
**Example:**
```sql
SELECT * FROM sample_table
```
2
### INSERT INTO
```sql
INSERT INTO table_name (id, name, cell_no, email) VALUES ( null,'Cool', '258226', 'a@gmail.com');
```
**Example:**
```sql
-- insert single data in a row  
use sample_database;
INSERT into sample_table (id, name, cell_no) VALUES (
    null,'Cool', '258226'
    );
```
```sql
-- insert multiple  data in the table  
use sample_database;
INSERT into sample_table (id, name, cell_no) VALUES
  	(null,'Cool', '258226'),
	(null,'Cool1', '258227'),
	(null,'Cool2', '258228'),
	(null,'Cool3', '258229'),
	(null,'Cool3', '258220'),
	(null,'Cool4', '258221');
```
3
### update table_name SET column_name=some_value where id=value;
**Example:**
```sql
update sample_table SET name="Abc" where id=1;
```
4
### DELETE from table_name WHERE column_name=value;
**Example:**
```sql
DELETE from sample_table WHERE id=2;
```
