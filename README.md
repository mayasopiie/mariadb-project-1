# SQL Project 1 using MariaDB


## Level 0

### Create database named 'employees_demo'.
Query:
```sh
CREATE DATABASE employees_demo;
```

### Create table named 'employees' with the specified table schema below.
```
+------------+---------------+------+-----+---------+----------------+
| Field      | Type          | Null | Key | Default | Extra          |
+------------+---------------+------+-----+---------+----------------+
| emp_no     | int(11)       | NO   | PRI | NULL    | auto_increment |
| birth_date | date          | NO   |     | NULL    |                |
| first_name | varchar(14)   | NO   |     | NULL    |                |
| last_name  | varchar(16)   | NO   |     | NULL    |                |
| gender     | enum('M','F') | NO   |     | NULL    |                |
| hire_date  | date          | NO   |     | NULL    |                |
+------------+---------------+------+-----+---------+----------------+
```

Query:
```sh
CREATE TABLE employees (
    emp_no INT(11) NOT NULL AUTO_INCREMENT,
    birth_date DATE NOT NULL,
    first_name VARCHAR(14) NOT NULL,
    last_name VARCHAR(16) NOT NULL,
    gender ENUM('M', 'F') NOT NULL,
    hire_date DATE NOT NULL,
    PRIMARY KEY (emp_no)
);
```

### Fill employees table with several data.
Query:
```sh
INSERT INTO `employees` VALUES 
(1, '1991-12-01', 'Surya', 'Raja', 'M', '2004-02-02'), 
(2, '2010-12-01', 'Jonathan', 'Sugiarto', 'M', '2015-02-02'),
(3, '2010-12-01', 'Komarudin', 'Yaochuan', 'M', '2015-02-02'),
(4, '1994-12-01', 'Gommaar', 'Jonker', 'M', '2014-02-02'),
(5, '1977-01-01', 'Susi', 'Susanti', 'F', '2014-02-02');
```

## Level 1

### Create table named 'titles' with specified table schema below.
```
+-----------+-------------+------+-----+---------+-------+
| Field     | Type        | Null | Key | Default | Extra |
+-----------+-------------+------+-----+---------+-------+
| emp_no    | int(11)     | NO   | PRI | NULL    |       |
| title     | varchar(50) | NO   | PRI | NULL    |       |
| from_date | date        | NO   |     | NULL    |       |
+-----------+-------------+------+-----+---------+-------+
```
Query:
```sh
CREATE TABLE titles(
    emp_no INT(11) NOT NULL,
    title VARCHAR(50) NOT NULL,
    from_date DATE NOT NULL,
    CONSTRAINT titles_pk PRIMARY KEY (emp_no, title)
);
```

### Fill titles table with several data.
Query:
```sh
INSERT INTO titles VALUES 
(1, 'Senior Engineer', '2004-02-02'),
(2, 'Staff', '2015-02-02'),
(3, 'Senior Engineer', '2015-02-02'),
(4, 'Senior Staff', '2014-02-02'),
(5, 'Staff', '2014-02-02');
```

## Level 2

### Use ALTER TABLE table statement to add new column named 'to_date' inside `titles` table default value '9999-01-01'.
Query:
```sh
ALTER TABLE titles ADD COLUMN to_date DATE;
ALTER TABLE titles ALTER to_date SET DEFAULT '9999-01-01';
UPDATE titles SET to_date = '9999-01-01';
```

### Use ALTER TABLE statement to add 'from_date' column as primary key.
Query:
```sh
ALTER TABLE titles DROP PRIMARY KEY;
ALTER TABLE titles ADD CONSTRAINT titles_pk PRIMARY KEY (emp_no, title, from_date);
```


## Level 3
### Use the UPDATE statement to update data like specified table content below.
```
+--------+-----------------+------------+------------+
| emp_no | title           | from_date  | to_date    |
+--------+-----------------+------------+------------+
|      1 | Senior Engineer | 2004-02-02 | 9999-01-01 |
|      2 | Staff           | 2015-02-02 | 9999-01-01 |
|      3 | Senior Engineer | 2015-02-02 | 9999-01-01 |
|      4 | Senior Staff    | 2014-02-02 | 9999-01-01 |
|      5 | Staff           | 2014-02-02 | 2014-02-22 | # <- update to_date where emp_no = 5
+--------+-----------------+------------+------------+
```
Query:
```sh
UPDATE titles SET to_date = '2014-02-02' WHERE emp_no = 5 AND title = 'Staff';
```
