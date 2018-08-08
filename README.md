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