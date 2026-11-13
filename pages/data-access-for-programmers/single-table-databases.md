---
title: Single Table Databases
subtitle: Data Access for Programmers
hideNav: false

live: https://fvtc.software/appel/data-access-for-programmers/single-table-databases
---

# Single Table Databases

As our data becomes larger and more complex, we need to start thinking about more advanced ways to store it. The most common way is to use a database management system or DBMS. A DBMS is a software system that allows us to store, organize, and manage data. 

## Introduction to Databases

In the following video, we will learn about a few different types of databases and a brief overview of how they work.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe
			src="https://www.youtube.com/embed/546kH96YSqs"
			width="100%" height="100%" frameborder="0" allowfullscreen
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
		></iframe>
	</div>
</details>

## MySQL and MySQL Workbench

A source of some confusion for new students is the difference between MySQL and MySQL Workbench. MySQL is a database management system, while MySQL Workbench is a graphical user interface (GUI) that allows us to interact with MySQL. The following video will give a brief overview of these two tools.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe
			src="https://www.youtube.com/embed/ZEmyVXtWr-M"
			width="100%" height="100%" frameborder="0" allowfullscreen
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
		></iframe>
	</div>
</details>

## Entity Relationship Diagrams

An entity relationship diagram (ERD) is a visual representation of the relationships between entities in a database. It's the first step in designing a database and is a great way to visualize the structure of your data.

> [!NOTE]
> Technically we're not creating an ERD here because there is only one entity, and therefore there is no relationship. However, the process is the same. If you want to be more accurate, you can call it an `entity diagram`.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe
			src="https://www.youtube.com/embed/S1q0cz_UI-0"
			width="100%" height="100%" frameborder="0" allowfullscreen
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
		></iframe>
	</div>
</details>

### Column Attributes

When creating a table, we need to specify the attributes of each column. The following video will give a brief overview of the different column attributes we can use.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe
			src="https://www.youtube.com/embed/QcHr-D9hG8M"
			width="100%" height="100%" frameborder="0" allowfullscreen
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
		></iframe>
	</div>
</details>

For future reference, here is a list of the column attributes we can use:

- `DataType` - The type of data that can be stored in the column.
- `Primary Key` - A unique identifier for each row in the table.
- `Not Null` - The column cannot be empty.
- `Unique` - The column cannot contain duplicate values.
- `Binary` - The column contains binary data.
- `Unsigned` - The column can only contain positive values.
- `Zerofill` - If the column is not long enough to display the value, it will be padded with zeros.
- `Auto Increment` - The column will automatically increment by one for each new row.
- `Generated` - The column will be computed using an expression rather than stored in the table.
- `Default` - The column will be set to the specified value if no value is provided.

# Exercise 1

Create the `Students` table (shown in the previous video) in MySQL Workbench. If you were following along with the video, you can skip this exercise.

> [!NOTE]
> Remember that even though you're allowed to use spaces in your column names, it's not a great idea. In the future, when you're writing queries, you'll have to use backticks (\`) around the column names if they contain spaces. My advice is to use camel case instead. For example, `FirstName` instead of `First Name`.

```ebnf
ID: Integer, Primary Key
First Name: String (VARCHAR)
Last Name: String (VARCHAR)
Phone: String (VARCHAR)
```

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe
			src="https://www.youtube.com/embed/4sBj8leGS98"
			width="100%" height="100%" frameborder="0" allowfullscreen
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
		></iframe>
	</div>
</details>

# Exercise 2

Create an Entity Diagram, suitable to hold the following `Inventory` data:

```ebnf
Item ID: 2447
Description: "Pogo 32 oz. Water Bottle"
Vendor ID: 355
In Stock Quantity: 6
Back Ordered Quantity: 800
```


<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe
			src="https://www.youtube.com/embed/npZNtd1jGGk"
			width="100%" height="100%" frameborder="0" allowfullscreen
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
		></iframe>
	</div>
</details>

# Creating Databases

SQL stands for Structured Query Language. It's a language that allows us to interact with databases. We'll be learning quite a bit of it throught this course.

Here is the SQL code for creating the `Students` table we created in the previous exercise:

```sql
CREATE TABLE Students (
	ID INT PRIMARY KEY,
	FirstName VARCHAR(63),
	LastName VARCHAR(63),
	Phone VARCHAR(15)
);
```

## Creating a Schema and Table

The following video will give a brief overview of how to create a schema and table in MySQL Workbench.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe
			src="https://www.youtube.com/embed/nzSHvnShOHs"
			width="100%" height="100%" frameborder="0" allowfullscreen
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
		></iframe>
	</div>
</details>

## Adding Data to the Table

To add (or insert) data into a table, we use the `INSERT INTO` statement. To insert data into the `Students` table, we would use the following SQL code:

```sql
INSERT INTO Students (ID, FirstName, LastName) VALUES (123456, "Ryan", "Appel");
```

Or if we are inserting data into all of the columns, we can omit the column names:

```sql
INSERT INTO Students VALUES (123456, "Ryan", "Appel");
```

The following video will give a brief overview of how to insert data into our table from the previous exercise video.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe
			src="https://www.youtube.com/embed/Q5AxufplWUg"
			width="100%" height="100%" frameborder="0" allowfullscreen
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
		></iframe>
	</div>
</details>

## A Few SQL Commands

As you saw at the end of the previous video, we can use the `SELECT` statement to retrieve data from a table. The code again for that was:

> [!NOTE]
> The asterisk `*` means "all columns". So you could read this as "select all columns from the Students table".

```sql
SELECT * FROM Students;
```

You may also want to delete a table from your database. To do that, you can use the `DROP TABLE` statement:

```sql
DROP TABLE Students;
```

You can also delete it using the GUI in MySQL Workbench. The following video will give a brief overview of how to do that.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe
			src="https://www.youtube.com/embed/nNrBzcAqWmw"
			width="100%" height="100%" frameborder="0" allowfullscreen
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
		></iframe>
	</div>
</details>

# Exercise 3

Create a database schema called `acme`. Then using your ERD From the previous exercise, create a table called `Inventory` in the `acme` database. Finally, insert the following data into the table:

```ebnf
Item ID: 2447
Description: "Pogo 32 oz. Water Bottle"
Vendor ID: 355
In Stock Quantity: 6
Back Ordered Quantity: 800
```

```ebnf
Item ID: 2473
Description: "Dimmer Switch"
Vendor ID: 21
In Stock Quantity: 411
Back Ordered Quantity: 0
```

```ebnf
Item ID: 2501
Description: "Reolink Wired Security Camera"
Vendor ID: 21
In Stock Quantity: 209
Back Ordered Quantity: 0
```

The video will walk you through the process if you have any trouble.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe
			src="https://www.youtube.com/embed/GWSxdOYJhEI"
			width="100%" height="100%" frameborder="0" allowfullscreen
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
		></iframe>
	</div>
</details>

# Review Questions

1. What is a database management system (DBMS)?
<details>
	<summary>Answer</summary>
	A software system that allows us to store, organize, and manage data.
</details>

2. What is the difference between MySQL and MySQL Workbench?
<details>
	<summary>Answer</summary>
	MySQL is a database management system, while MySQL Workbench is a graphical user interface (GUI) that allows us to interact with MySQL.
</details>

3. What is an entity relationship diagram (ERD)?
<details>
	<summary>Answer</summary>
	A visual representation of the relationships between entities in a database.
</details>

4. What is a column attribute?
<details>
	<summary>Answer</summary>
	A property of a column that specifies how the data in the column should be stored.
</details>

5. What is a Primary Key?
<details>
	<summary>Answer</summary>
	A unique identifier for each row in the table.
</details>

6. What does SQL stand for?
<details>
	<summary>Answer</summary>
	Structured Query Language.
</details>

7. What is the SQL code for creating a table?
<details>
	<summary>Answer</summary>
	<code>CREATE TABLE</code>
</details>

8. What is the SQL code for inserting data into a table?
<details>
	<summary>Answer</summary>
	<code>INSERT INTO</code>
</details>

9. What is the SQL code for retrieving all columns from a table?
<details>
	<summary>Answer</summary>
	<code>SELECT * FROM</code>
</details>

10. What is the SQL code for deleting a table?
<details>
	<summary>Answer</summary>
	<code>DROP TABLE</code>
</details>
