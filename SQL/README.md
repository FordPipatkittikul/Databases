# PostgreSQL

SQL is a devlarative language(langauage that we are stating what will happen)

testing query: https://www.db-fiddle.com/f/ogAiTgZPjwvDxwVHiVK3Ek/0

# Schema
    defines the structure of the database. It includes the definitions of tables, columns, data types, indexes, views, and other database objects.

# QUERY BREAKDOWN
    quick note SQL statement and query are the same

![QUERY](<query breakdown.png>)

`identifier` is just a different word for a part of the data(column or table)

# Relational Model

### Tables
    tables is representation of that object. It is collection of columns and rows
![Tables](table.png)

### Column
    Each column represent specific type of data.

    Degree : collection of columns.

    Attribute domain/Constraint: is what column can store.
![Column](Columns.png)

### Row
    Each of single row is a piece of data that represent one single piece data of that table

    Some people call tuple(It is basiclly row)

    Each and every tuple/row follow the column constraints

    Cardinality: collections of rows/tuples
![Row](Rows.png)


### Primary key
    Primary key is something that uniquely identifies data.

### Foriegn key
    Foriegn key references the primary key of a different table.

![alt text](key.png)

# How we use database

    1) `OLTP(online transaction processing)`
    
        For a day to day transactional for driving business. E.X. Amazon what this user's order, order's history, his card number.
    
        E.X.
        
        - A database is being used to log orders and customers.
    
    2) `OLAP(online analytical processing)`
    
        For future decision. A separate database that connects to the data warehouse being making analytical on it so we can think how to improve our product, website in future.
    
        E.X.
    
        - A database is being used to figure out what new products we should offer.
    
        - A database is being used to drive statistics for reporting to the executives.

# QUERY Syntax
    1) Renaming a columns
    SELECT column as 'new name'
    
    2) CONCAT() you can CONCAT(text1, text2) or CONCAT(column1, column2)
    SELECT CONCAT(emp_no, ' is a ', title) AS "Employee Title" FROM titles

### Function in query syntax
    1) Aggregate function run all of the data and produce one output. Like SUM()
    2) Scalar function run each individual row and produce multiple output. Like CONCAT()

### Filtering
    SELECT first_name,last_name,hire_date FROM employees
    WHERE (first_name = 'Georgi' AND last_name = 'Facello' AND hire_date = '1986-06-26') 
    OR (first_name = 'Bezalel' AND last_name = 'Simmel');
    
    -- AND, OR, NOT, comparison operators(https://www.w3schools.com/sql/sql_operators.asp)
       , BETWEEN AND, IN(https://www.w3schools.com/sql/sql_in.asp)
       , LIKE(https://www.w3schools.com/sql/sql_like.asp) in PostgreSQL only with text comparision, ILIKE is same as like but case insensitive matching
       
    -- when we do filtering when we do where cause. There is an order of filtering
![Screenshot (131)](https://github.com/user-attachments/assets/9e3e27f8-de58-42e9-8ab3-728018d8ac48)

### sorting data
    SELECT * FROM customers
    ORDER BY <column> ASC;

    SELECT * FROM customers
    ORDER BY <column> DESC;

    SELECT  first_name, last_name FROM employees
    ORDER BY first_name ASC, last_name DESC;

    SELECT * FROM customers
    ORDER BY LENGTH(name) DESC;

    SELECT * FROM employees
    WHERE first_name ILIKE 'K%'
    ORDER BY hire_date

### Multi Table SELECT
    SELECT a.emp_no, b.salary FROM employees as a, salaries As b
    WHERE a.emp_no = b.emp_no
    ORDER BY a.emp_no

### Date & Timezones
    https://www.w3schools.com/Sql/sql_dates.asp
    
    DATE
        convert a date to a date format. 
        SELECT DATE '1800/01/01';
        
    Intervals: https://www.javatpoint.com/mysql-interval
        It can store and manipulate a period of time in Years, Months, Days, Hours, Minutes, Seconds.
        SELECT * FROM employees
        WHERE AGE(birth_date) > INTERVAL '60 years';
    
    EXTRACT() https://www.w3schools.com/sql/func_mysql_extract.asp
        SELECT EXTRACT(MONTH FROM DATE '2017-06-15');

    now()  https://www.w3schools.com/sql/func_mysql_now.asp
        
    SELECT NOW()::date;   
    SELECT CURRENT_DATE;
        a way to get current day in date format.
        SELECT TO_CHAR(CURRENT_DATE, 'dd/mm/yyyy');

    AGE()
        we have to make sure something that passed into AGE() parameter is date data type not something else.

    DATE_TRUNC()
        SELECT DATE_TRUNC('year', date '1992/11/13');
          
### NULL
    IS
        a keyword that we can use to filter NULL. other comparison operators cannot Filtering.
        NULL = NULL  will return NULL not TRUE OR FALSE. NULL IS NULL will return TRUE.
    COALESCE 
        SELECT COALESCE(name, 'no name available') FROM Student;    -- COALESCE returns the first non-null value in a list and replace Null value with fallback argument
    testing: https://www.db-fiddle.com/f/PnGNcaPYfGoEDvfexzEUA/1313
    
### Three-Valued Logic
    Besides TRUE and FALSE, the result or logical expressions can also be UNKNOWN

### DISTINCT keyword
    https://www.w3schools.com/sql/sql_distinct.asp
    Inside a table, a column often contains many duplicate values; and sometimes you only want to list the different (distinct) values.
    
    SELECT DISTINCT column1, column2, ...
    FROM table_name;

### Commenting
     --select statement to filter Mayumi Schueller
    SELECT first_name,last_name AS "Full Name" FROM employees
    /*
    filter on first_name AND last_name 
    and focus filtering on first_name is 'Mayumi' AND last_name is 'Schueller'
    */ 
    WHERE first_name = 'Mayumi' AND last_name = 'Schueller';
    
### Common mistakes
     ' ' for you to write TEXT in sql, " " is for TABLES. 
