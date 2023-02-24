# SQL Cheatsheet

Welcome to the SQL Cheatsheet! This open source project aims to provide a comprehensive and easy-to-use reference for SQL syntax and commands. Whether you're a beginner or a seasoned SQL developer, this cheatsheet has got you covered.

- [Basic SQL Commands](#basic-sql-commands)
- [Sorting and Filtering](#sorting-and-filtering)
- [Aggregation](#aggregation)
- [Joins](#joins)
- [Subqueries](#subqueries)
- [Aliases](#aliases)
- [Group By](#group-by)
- [Having](#having)
- [Case](#case)
- [Views](#views)
- [Indexes](#indexes)
- [Transactions](#transactions)
- [Window Functions](#window-functions)
- [CTE (Common Table Expression)](#cte-common-table-expression)
- [Set Operators](#set-operators)
- [Subquery in FROM Clause](#subquery-in-from-clause)
- [Conditional Logic](#conditional-logic)

## Basic SQL Commands

#### SELECT: used to retrieve data from a table.

```sql
 SELECT column1, column2, ...
 FROM table_name;
```

#### FROM: used to specify the table from which to retrieve data.

```sql
 SELECT column1, column2, ...
 FROM table_name;
```

#### WHERE: used to filter data based on a condition.

```sql
 SELECT column1, column2, ...
 FROM table_name
 WHERE condition;
```

#### INSERT INTO: used to insert new data into a table.

```sql
 INSERT INTO table_name (column1, column2, ...)
 VALUES (value1, value2, ...);
```

#### UPDATE: used to update existing data in a table.

```sql
 UPDATE table_name
 SET column1 = value1, column2 = value2, ...
 WHERE condition;
```

#### DELETE FROM: used to delete data from a table.

```sql
 DELETE FROM table_name
 WHERE condition;
```

## Sorting and Filtering

#### ORDER BY: used to sort data in ascending or descending order.

```sql
 SELECT column1, column2, ...
 FROM table_name
 ORDER BY column_name ASC/DESC;
```

#### LIMIT: used to limit the number of results returned.

```sql
 SELECT column1, column2, ...
 FROM table_name
 LIMIT number_of_rows;
```

#### OFFSET: used to skip a certain number of rows before returning results.

```sql
 SELECT column1, column2, ...
 FROM table_name
 OFFSET number_of_rows;

```

#### Sorting by multiple columns.

```sql
 SELECT column1, column2, ...
 FROM table_name
 ORDER BY column1 ASC, column2 DESC;
```

## Aggregation

#### COUNT: used to count the number of rows in a table.

```sql
 SELECT COUNT(*) FROM table_name;
```

#### SUM: used to calculate the sum of values in a column.

```sql
 SELECT SUM(column_name) FROM table_name;
```

#### AVG: used to calculate the average of values in a column.

```sql
 SELECT AVG(column_name) FROM table_name;
```

#### MIN: used to find the minimum value in a column.

```sql
 SELECT MIN(column_name) FROM table_name;
```

#### MAX: used to find the maximum value in a column.

```sql
 SELECT MAX(column_name) FROM table_name;
```

## Joins

#### INNER JOIN: used to combine rows from two or more tables based on a matching column.

```sql
 SELECT column1, column2, ...
 FROM table1 INNER JOIN table2
 ON table1.column_name = table2.column_name;
```

#### LEFT JOIN: used to return all rows from the left table and matching rows from the right table.

```sql
 SELECT column1, column2, ...
 FROM table1 LEFT JOIN table2
 ON table1.column_name = table2.column_name;
```

#### RIGHT JOIN: used to return all rows from the right table and matching rows from the left table.

```sql
 SELECT column1, column2, ...
 FROM table1 RIGHT JOIN table2
 ON table1.column_name = table2.column_name;
```

#### FULL OUTER JOIN: used to return all rows from both tables, with NULL values for any unmatched rows.

```sql
 SELECT column1, column2, ...
 FROM table1 FULL OUTER JOIN table2
 ON table1.column_name = table2.column_name;
```

## Subqueries

A subquery is a query that is nested inside another query.

```sql
 SELECT column1, column2, ...
 FROM table_name
 WHERE column_name
 IN (SELECT column_name FROM table_name WHERE condition);
```

## Aliases

Aliases are used to give a table or column a temporary name.

```sql
 SELECT column1 AS alias1, column2 AS alias2
 FROM table_name;
```

## Group By

Group By is used to group rows that have the same values into summary rows.

```sql
 SELECT column_name, COUNT(*)
 FROM table_name
 GROUP BY column_name;
```

Grouping By multiple columns.

```sql
 SELECT column1, column2, COUNT(*)
 FROM table_name
 GROUP BY column1, column2;
```

Grouping By expressions.

```sql
 SELECT CASE
            WHEN column1 = 'A' THEN 'Group 1'
            WHEN column1 = 'B' THEN 'Group 2'
            ELSE 'Other'
        END AS group_name,
        COUNT(*)
 FROM table_name
 GROUP BY group_name;
```

## Having

Having is used to filter the results of a `GROUP BY` query based on a condition.

```sql
 SELECT column_name, COUNT(*)
 FROM table_name
 GROUP BY column_name
 HAVING COUNT(*) > 1;
```

## Case

Case is used to create a new column based on a condition.

```sql
 SELECT column1, column2, ...,
 CASE
   WHEN condition1 THEN result1
   WHEN condition2 THEN result2
   ELSE default_result
 END AS new_column_name
 FROM table_name;
```

To use multiple conditions.

```sql
 SELECT column1, column2, ...,
 CASE
   WHEN condition1 THEN result1
   WHEN condition2 THEN result2
   WHEN condition3 THEN result3
   ELSE default_result
 END AS new_column_name
 FROM table_name;
```

## Views

#### CREATE VIEW: used to create a virtual table based on the result of a SELECT statement.

```sql
 CREATE VIEW view_name AS SELECT column1, column2, ...
 FROM table_name WHERE condition;
```

#### SELECT: used to retrieve data from a view.

```sql
 SELECT * FROM view_name;
```

#### DROP VIEW: used to delete a view.

```sql
 DROP VIEW view_name;
```

## Indexes

#### CREATE INDEX: used to create an index on a table.

```sql
 CREATE INDEX index_name
 ON table_name (column_name);
```

#### DROP INDEX: used to delete an index from a table.

```sql
 DROP INDEX index_name;
```

## Transactions

#### BEGIN TRANSACTION: used to start a transaction.

```sql
 BEGIN TRANSACTION;
```

#### COMMIT: used to commit a transaction.

```sql
 COMMIT;
```

#### ROLLBACK: used to rollback a transaction.

```sql
 ROLLBACK;
```

## Window Functions:

Window functions are a powerful feature of SQL that allows you to perform calculations across rows that are related to the current row. They are applied to a set of rows that are defined by an `OVER()` clause. Some common window functions are:

- `ROW_NUMBER()`: assigns a unique sequential number to each row within a partition.
- `RANK()`: assigns a rank to each row within a partition, with ties receiving the same rank.
- `DENSE_RANK()`: assigns a rank to each row within a partition, with ties receiving the same rank, but leaving no gaps between ranks.
- `LAG()`: returns the value of a column from the previous row within a partition.
- `LEAD()`: returns the value of a column from the next row within a partition.
- `SUM()`, `AVG()`, `MIN()`, `MAX()`, etc.: performs an aggregate function over a window of rows.

```sql
 SELECT column1, column2, ...,
       ROW_NUMBER() OVER (PARTITION BY column_name
                          ORDER BY column_name) AS row_num
 FROM table_name;
```

## CTE (Common Table Expression):

CTE allows you to define a named temporary result set that can be used in subsequent queries. It is often used to break down a complex query into smaller, more manageable pieces.

```sql
 WITH cte_name AS (
   SELECT column1, column2, ...
   FROM table_name
   WHERE condition
 )
 SELECT column1, column2, ...
 FROM cte_name;
```

## Set Operators

Set Operators are used to combine the result sets of two or more `SELECT` statements.

#### UNION: used to combine the results of two or more SELECT statements, excluding duplicates.

```sql
 SELECT column1, column2, ...
 FROM table1
 UNION
 SELECT column1, column2, ...
 FROM table2;
```

#### UNION ALL: used to combine the results of two or more SELECT statements, including duplicates.

```sql
 SELECT column1, column2, ...
 FROM table1
 UNION ALL
 SELECT column1, column2, ...
 FROM table2;
```

#### INTERSECT: used to return only the common rows between two SELECT statements.

```sql
 SELECT column1, column2, ...
 FROM table1
 INTERSECT
 SELECT column1, column2, ...
 FROM table2;
```

#### EXCEPT: used to return only the unique rows in the first SELECT statement that are not in the second SELECT statement.

```sql
 SELECT column1, column2, ...
 FROM table1
 EXCEPT
 SELECT column1, column2, ...
 FROM table2;
```

## Subquery in FROM Clause:

This allows you to use a subquery as a table in the `FROM` clause. It is often used when you need to aggregate data from a subquery before joining it to other tables.

```sql
 SELECT column1, column2, ...
 FROM (
   SELECT column1, column2, ...,
   FROM table_name
   WHERE condition
 ) AS subquery_name
 JOIN table_name ON table_name.column_name = subquery_name. column_name;
```

## Conditional Logic:

#### IF/ELSE: allows you to execute different statements based on a condition.

```sql
 IF condition THEN
   statement1;
 ELSE
   statement2;
 END IF;
```

#### CASE: used to apply conditional logic to a query.

```sql
 SELECT column_name,
        CASE
            WHEN condition THEN value
            WHEN condition THEN value
            ELSE value
        END AS alias_name
 FROM table_name;
```

#### COALESCE: used to return the first non-null value in a list.

```sql
 SELECT COALESCE(column1, column2, ...) AS alias_name
 FROM table_name;
```

#### NULLIF: used to return null if two values are equal.

```sql
 SELECT NULLIF(value1, value2) AS alias_name
 FROM table_name;
```

#### IFNULL: used to return a specified value if the expression is null, otherwise it returns the expression.

```sql
 SELECT IFNULL(expression, value) AS alias_name
 FROM table_name;
```

## Contribute

This cheatsheet is an open source project, and contributions are always welcome. If you find a mistake, an omission, or want to suggest an improvement, please create an issue or submit a pull request on the project's GitHub repository. Your contributions help make this resource more useful for everyone.

## Acknowledgements

We want to thank the contributors who have helped create and maintain this cheatsheet. Your efforts have made this resource possible, and we are grateful for your contributions. We also want to acknowledge the SQL community for their support and feedback, which has helped shape this cheatsheet into what it is today.
