# mysql-cheatsheet-example

# SQL languages

**DDL** is short name of Data Definition Language, which deals with database schemas and descriptions, of how the data should reside in the database.

**DML** is short name of Data Manipulation Language which deals with data manipulation, and includes most common SQL statements such SELECT, INSERT, UPDATE, DELETE etc, and it is used to store, modify, retrieve, delete and update data in database.

**DCL** is short name of Data Control Language which includes commands such as GRANT, and mostly concerned with rights, permissions and other controls of the database system.

# Datatypes
Text types

| Data type        | Description                                                                                                                                                                                                                                                                                      |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CHAR(size)       | Holds a fixed length string (can contain letters, numbers, and special characters). The fixed size is specified in parenthesis. Can store up to 255 characters                                                                                                                                   |
| VARCHAR(size)    | Holds a variable length string (can contain letters, numbers, and special characters). The maximum size is specified in parenthesis. Can store up to 255 characters. Note: If you put a greater value than 255 it will be converted to a TEXT type                                               |
| TINYTEXT         | Holds a string with a maximum length of 255 characters                                                                                                                                                                                                                                           |
| TEXT             | Holds a string with a maximum length of 65,535 characters                                                                                                                                                                                                                                        |
| BLOB             | For BLOBs (Binary Large OBjects). Holds up to 65,535 bytes of data                                                                                                                                                                                                                               |
| MEDIUMTEXT       | Holds a string with a maximum length of 16,777,215 characters                                                                                                                                                                                                                                    |
| MEDIUMBLOB       | For BLOBs (Binary Large OBjects). Holds up to 16,777,215 bytes of data                                                                                                                                                                                                                           |
| LONGTEXT         | Holds a string with a maximum length of 4,294,967,295 characters                                                                                                                                                                                                                                 |
| LONGBLOB         | For BLOBs (Binary Large OBjects). Holds up to 4,294,967,295 bytes of data                                                                                                                                                                                                                        |
| ENUM(x,y,z,etc.) | Let you enter a list of possible values. You can list up to 65535 values in an ENUM list. If a value is inserted that is not in the list, a blank value will be inserted.Note: The values are sorted in the order you enter them.You enter the possible values in this format: ENUM('X','Y','Z') |
| SET              | Similar to ENUM except that SET may contain up to 64 list items and can store more than one choice                                                                                                                                                                                               |

Number types

| Data type       | Description                                                                                                                                                                                                                           |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| TINYINT(size)   | -128 to 127 normal. 0 to 255 UNSIGNED*. The maximum number of digits may be specified in parenthesis                                                                                                                                  |
| SMALLINT(size)  | -32768 to 32767 normal. 0 to 65535 UNSIGNED*. The maximum number of digits may be specified in parenthesis                                                                                                                            |
| MEDIUMINT(size) | -8388608 to 8388607 normal. 0 to 16777215 UNSIGNED*. The maximum number of digits may be specified in parenthesis                                                                                                                     |
| INT(size)       | -2147483648 to 2147483647 normal. 0 to 4294967295 UNSIGNED*. The maximum number of digits may be specified in parenthesis                                                                                                             |
| BIGINT(size)    | -9223372036854775808 to 9223372036854775807 normal. 0 to 18446744073709551615 UNSIGNED*. The maximum number of digits may be specified in parenthesis                                                                                 |
| FLOAT(size,d)   | A small number with a floating decimal point. The maximum number of digits may be specified in the size parameter. The maximum number of digits to the right of the decimal point is specified in the d parameter                     |
| DOUBLE(size,d)  | A large number with a floating decimal point. The maximum number of digits may be specified in the size parameter. The maximum number of digits to the right of the decimal point is specified in the d parameter                     |
| DECIMAL(size,d) | A DOUBLE stored as a string , allowing for a fixed decimal point. The maximum number of digits may be specified in the size parameter. The maximum number of digits to the right of the decimal point is specified in the d parameter |

Date types

| Data type   | Description                                                                                                                                                                                                                              |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| DATE()      | A date. Format: YYYY-MM-DDNote: The supported range is from '1000-01-01' to '9999-12-31'                                                                                                                                                 |
| DATETIME()  | *A date and time combination. Format: YYYY-MM-DD HH:MI:SSNote: The supported range is from '1000-01-01 00:00:00' to '9999-12-31 23:59:59'                                                                                                |
| TIMESTAMP() | *A timestamp. TIMESTAMP values are stored as the number of seconds since the Unix epoch ('1970-01-01 00:00:00' UTC). Format: YYYY-MM-DD HH:MI:SSNote: The supported range is from '1970-01-01 00:00:01' UTC to '2038-01-09 03:14:07' UTC |
| TIME()      | A time. Format: HH:MI:SSNote: The supported range is from '-838:59:59' to '838:59:59'                                                                                                                                                    |
| YEAR()      | A year in two-digit or four-digit format.Note: Values allowed in four-digit format: 1901 to 2155. Values allowed in two-digit format: 70 to 69, representing years from 1970 to 2069                                                     |


Mysql cheat sheet for beginners
## DDL

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

## DML

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

### ** Complete example **
```sql

-- final database backup
DROP TABLE IF EXISTS `sample_table`;
CREATE TABLE IF NOT EXISTS `sample_table` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `first_name` varchar(100) NOT NULL,
  `last_name` varchar(100) NOT NULL,
  `cell_no` varchar(50) NOT NULL,
  `email` varchar(100) NOT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `email` (`email`)
) ENGINE=MyISAM AUTO_INCREMENT=8 DEFAULT CHARSET=latin1;

INSERT INTO `sample_table` (`id`, `first_name`, `last_name`, `cell_no`, `email`) VALUES
(1, 'Abc', 'Coll', '258226', 'abc@gmail.com'),
(2, 'Cool1', 'Coll', '258227', 'abc1@gmail.com'),
(3, 'Cool2', 'Coll', '258228', 'abc2@gmail.com'),
(4, 'Cool3', 'Coll', '258229', 'abc3@gmail.com'),
(5, 'Cool3', 'Coll', '258220', 'abc4@gmail.com'),
(6, 'Cool4', 'Coll', '258221', 'abc5@gmail.com');
COMMIT;

-- add a new column to the right of the email
ALTER TABLE `sample_table` ADD `cool` VARCHAR(100) NOT NULL AFTER `email`;
-- delete column cool from the table
ALTER TABLE `sample_table`  DROP `cool`;

```
