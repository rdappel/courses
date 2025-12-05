---
title: Multi-Table Queries
subtitle: Data Access for Programmers
hideNav: false

live: https://fvtc.software/appel/data-access-for-programmers/multi-table-queries
---

# Multi-Table Queries

Now that we have created databases with multiple tables, we can start to query data from multiple tables. This lesson covers the `JOIN` statement, which is used to combine data from multiple tables.

## Joining Tables

In the following video we'll be using the "Henry" database to demonstrate how to join tables. It's already installed on your Virtual Machine, so please open it up, and follow along.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/8Y1vmb7-RJE" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the final query from the video:

```sql
SELECT * FROM book
JOIN publisher ON book.PUBLISHER_CODE = publisher.PUBLISHER_CODE
JOIN inventory ON book.BOOK_CODE = inventory.BOOK_CODE
```

### Context Variables

We can use context variables to make our queries shorter and easier to read. This is especially useful when we are joining multiple tables. The following query is equivalent to the previous query.

```sql
SELECT * FROM book b -- notice the extra "b" after book
JOIN publisher p ON b.PUBLISHER_CODE = p.PUBLISHER_CODE -- notice the extra "p" after publisher
JOIN inventory i ON b.BOOK_CODE = i.BOOK_CODE -- notice the extra "i" after inventory
```

Looking at the query above, we can see that we have added a context variable to each table. The context variable is a single letter that we can use to refer to the table. On line 2, `book.PUBLISHER_CODE = publisher.PUBLISHER_CODE` is now shortened to `b.PUBLISHER_CODE = p.PUBLISHER_CODE`.

This video will demonstrate this query.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/mdGvZBUOXTg" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# Exercises

Let's practice joining tables. For these exercises, we'll be using the "Premiere" database, so make sure that you're using it, by double-clicking on it in the Navigator.

## Exercise 1 

Show all of the customers that have placed an order, and include their order data. (Use the customer and orders tables).

<details>
	<summary>Show the Answer</summary>

```sql
SELECT * FROM customer c
JOIN orders o ON c.CUSTOMER_NUM = o.CUSTOMER_NUM
```
</details>

## Exercise 2

Continue from the previous exercise, and show the CUSTOMER_NUM, CUSTOMER_NAME, and ORDER_DATE for all customers that have placed an order on 10/21/2007.

<details>
	<summary>Show the Answer</summary>

```sql
SELECT c.CUSTOMER_NUM, CUSTOMER_NAME, ORDER_DATE FROM customer c
JOIN orders o ON c.CUSTOMER_NUM = o.CUSTOMER_NUM
WHERE ORDER_DATE = '2007-10-21'
```
</details>

This video will demonstrate the previous two exercises.	

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/2T8xj67xHp0" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# Review Questions

1. What keywords are used to join tables?

<details>
	<summary>Show the Answer</summary>
	JOIN, ON
</details>

2. What are context variables used for?

<details>
	<summary>Show the Answer</summary>
	To shorten join queries by referring to tables with a shorter name.
</details>

3. When using join statements, should you join the tables first, or filter the data first?

<details>
	<summary>Show the Answer</summary>
	Join the tables first, then filter the data. (JOIN ON, comes before WHERE)
</details>
