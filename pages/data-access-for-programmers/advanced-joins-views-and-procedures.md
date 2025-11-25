---
title: Advanced Joins, Views, and Procedures
subtitle: Data Access for Programmers
hideNav: false

live: https://fvtc.software/appel/data-access-for-programmers/advanced-joins-views-and-procedures
---

# Advanced Joins, Views, and Procedures

This lesson covers advanced joins, views, and procedures. These topics will more or less round out our SQL knowledge for the semester.

# Advanced Joins

 Let's start by looking at a few more ways that we can join tables together. In previous lessons, we have used the `JOIN` statement to join tables together. The `JOIN` statement is a type of `INNER JOIN`. There are other types of joins that we can use to join tables together.

 ## Outer Joins

 The `OUTER JOIN` statement is used to join tables together, but it will also include rows that do not have a match in the other table. The following SQL statement will show all of the customer data, and their orders. If a customer does not have an order, the order data will be `NULL`, but they will still be included in the results.

 ```sql
SELECT * FROM customer c LEFT OUTER JOIN orders o ON c.CUSTOMER_NUM = o.CUSTOMER_NUM
```

> [!NOTE] The customer table appears first in the statement, making it the LEFT table. Because the query is using a LEFT OUTER JOIN, all of the rows from the LEFT (customer) table will be included in the results.

In this video we will discuss this query in more detail.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/WdI5S0Cz-gw" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

If the Venn diagrams shown in the video were helpful, you may find [Oleksii Vasyliev's SQL Joins Visualizer](https://sql-joins.leopard.in.ua/) helpful as well. It allows you to select parts of the Venn diagram to see the SQL code that would produce that result.

# Exercise 1

Using the Premiere database, write a query that uses an `INNER JOIN` to join the `rep` and the `customer` tables together. `REP_NUM` is the Primary Key in the `rep` table, and the Foreign Key in the `customer` table.

<details>
	<summary>Show the Answer</summary>

```sql
SELECT * FROM rep r JOIN customer c ON r.REP_NUM = c.REP_NUM
```
</details>

When you have run that query, modify it to show all of the reps, even if they do not work with any customers. (Choose the correct type of join to accomplish this.) Hint: You might be surprised by the results.

<details>
	<summary>Show the Answer</summary>

```sql
SELECT * FROM rep r LEFT OUTER JOIN customer c ON r.REP_NUM = c.REP_NUM
```

> [!NOTE] You might have expected to see some reps with null values in the customer columns. However, the `rep` table does not have any reps that do not have customers. In this case we see the same results as an `INNER JOIN`.
</details>

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/HXRM9M6yjrc" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# Union Statements

The `UNION` statement is used to combine the results of two or more `SELECT` statements into a single result set, though not in the same way that a `JOIN` statement does.

When we use a `JOIN` statement, we are combining the columns from two or more tables into a single result set. When we use a `UNION` statement, we are combining the rows from two or more `SELECT` statements into a single result set. So instead of seeing more columns in the result set, we typically see more rows.

The following SQL statement will show all of the addresses from the `customer` table, and all of the addresses from the `rep` table.

```sql
SELECT STREET, CITY, STATE, ZIP FROM customer
UNION
SELECT STREET, CITY, STATE, ZIP FROM rep
```

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/ZOBYf887mZs" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# Exercise 2

For this exercise, we will use the Alexamara database. Specifically the employees and owner tables. Show the first and last names of all of the employees, and the first and last names of all of the owners.

<details>
	<summary>Show the Answer</summary>

```sql
SELECT Emp_First_Name, Emp_Last_Name FROM employees
UNION
SELECT FIRST_NAME, LAST_NAME FROM owner
```
</details>

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/rM2LCTHUK6M" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# Nested Queries

A nested query is a `SELECT` statement that is nested inside of another `SELECT` statement. The nested query is often used in the `WHERE` clause of the outer query. A nested query is often referred to as a subquery.

An example of a nested query is shown below. This query will show all of the customers that have a higher than average balance.

```sql
SELECT CUSTOMER_NUM, BALANCE FROM customer
WHERE BALANCE > (SELECT AVG(BALANCE) FROM customer)
```

This video will walk you through this query.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/Gfr1-QTQDN8" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# Views

Moving on from joining tables, a view is a virtual table based on the result-set of an SQL statement. A view contains rows and columns, just like a real table. The fields in a view are fields from one or more real tables in the database.

A view always shows up-to-date data! The database engine recreates the data, using the view's SQL statement, every time a user queries a view.

Views allow us to store a query in the database, and then use that query as if it were a table. This can be useful if we have a query that we use often, or if we want to limit the data that a user can see.

A view is created using the `CREATE VIEW` statement. The following statement will create a view that joins the rep and customer tables, showing rep numbers, names, customer numbers, customer names, and credit limits.

```sql
CREATE VIEW vsRepCustomerCredit AS
SELECT r.REP_NUM, LAST_NAME, FIRST_NAME, CUSTOMER_NUM, CUSTOMER_NAME, CREDIT_LIMIT FROM rep r
JOIN customer c ON r.REP_NUM = c.REP_NUM
```

We can then use the view in a `SELECT` statement, just like we would use a table.

```sql
SELECT * FROM vsRepCustomerCredit
```

To delete a view, you can simply use the `DROP VIEW` statement.

```sql
DROP VIEW vsRepCustomerCredit
```

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/NhRls66xvnU" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# Stored Procedures

A stored procedure is a prepared SQL code that you can save, so the code can be reused over and over again. So if you have an SQL query that you write over and over again, save it as a stored procedure, and then just call it to execute it.

You can also pass parameters to a stored procedure, so that the stored procedure can act based on the parameter value(s) that is passed.

Stored procedures are similar to functions in programming languages. They are also similar to views, in that they are stored in the database, and can be used over and over again.

We can create a stored procedure using the `CREATE PROCEDURE` statement. This video will walk you through creating one.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/snZXjZ65_uc" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# Exercise 3

Using the Premiere database, create a view that shows the all of the Customer (Names) from Grove (City). Verify it's working by running a `SELECT` statement against the view.

<details>
	<summary>Show the Answer</summary>

```sql
CREATE VIEW vwGroveCustomers AS
SELECT CUSTOMER_NAME from customer WHERE CITY = 'Grove';

SELECT * FROM vwGroveCustomers;
```
</details>

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/kph5NVpCR8M" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# Exercise 4

Again, using the Premiere database, create a stored procedure called "spCustomersFrom" that shows the customer's name from a given city. The city should be passed as a parameter. Call the parameter "FromCity," and make it a CHAR(15). Verify the stored procedure is working by calling it with the city of "Fillmore."

<details>
	<summary>Show the Answer</summary>

```sql
CREATE PROCEDURE spCustomersFrom(IN FromCity CHAR(15))
SELECT CUSTOMER_NAME FROM customer WHERE CITY = FromCity;

CALL spCustomersFrom('Fillmore');
```
</details>

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/xxoeeinO_h0" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# Review Questions

1. What is the difference between an `INNER JOIN` and an `OUTER JOIN`?

<details>
	<summary>Show the Answer</summary>

An `INNER JOIN` will only return rows that have a match in both tables. An `OUTER JOIN` will return all of the rows from one table, and the matching rows from the other table.
</details>

2. What is the difference between a `JOIN` and a `UNION`?

<details>
	<summary>Show the Answer</summary>

A `JOIN` will combine the columns from two or more tables into a single result set. A `UNION` will combine the rows from two or more `SELECT` statements into a single result set.
</details>

3. What is a nested query?

<details>
	<summary>Show the Answer</summary>

A nested query is a `SELECT` statement that is nested inside of another `SELECT` statement.
</details>

4. What is a view?

<details>
	<summary>Show the Answer</summary>

A view is a virtual table based on the result-set of an SQL statement.
</details>

5. What is a stored procedure?

<details>
	<summary>Show the Answer</summary>

A stored procedure is a prepared SQL code that you can save, so the code can be reused over and over again.
</details>