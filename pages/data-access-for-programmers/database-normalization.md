---
title: Database Normalization
subtitle: Data Access for Programmers
hideNav: false

live: https://fvtc.software/appel/data-access-for-programmers/database-normalization
---

# Database Normalization

Normalization is the process of organizing data in a database. This includes creating tables and establishing relationships between those tables according to rules designed both to protect the data and to make the database more flexible by eliminating redundancy and inconsistent dependency.

# Determinants and Dependencies

Before we can normalize a database, we need to understand determinants and functional dependencies.

A **determinant** is any attribute whose value determines other values within a row.

A **functional dependency** is a relationship between two attributes, typically between the determinant and the dependent attribute.

If you want to follow along with the video, we'll be using this data:

| Student ID | First Name | Last Name | City | State | Zip | Course IDs | Course Names | Registration Dates |
| ---------- | ---------- | --------- | ---- | ----- | --- | ---------- | ------------ | ------------------ |
| 123        | Jimmy      | Smith     | Appleton | WI | 54911 | 1       | Data Access for Programmers   | 1/05       |
| 124        | Erin       | Donaldson | Neenah   | WI | 54956 | 2, 3    | C# Intro to Programming, PHP  | 1/06, 1/06 |
| 125        | Erica      | Zastrow   | Appleton | WI | 54914 | 1, 4    | Data Access for Programmers, Computer Programming C++ | 1/05, 1/06 |
| 127        | Greg       | Olsen     | Appleton | WI | 54911 | 2       | C# Intro to Programming 		| 1/05       |
| 129        | Kim        | Palmer    | Neenah   | WI | 54956 | 4       | Computer Programming C++      | 1/05       |
| 131        | Bryce      | Davis     | Appleton | WI | 54911 | 1       | Data Access for Programmers	| 1/07       |
| 133        | Erin       | Price     | Appleton | WI | 54913 | 2, 3    | C# Intro to Programming, PHP  | 1/07, 1/05 |
| 134        | Marquise   | Alton     | Appleton | WI | 54915 | 2       | C# Intro to Programming 		| 1/05       |

You can download the Excel file here: [students.xlsx](https://github.com/RDAppel/courses/raw/master/support-files/dap/database-normalization/students.xlsx).

> [!NOTE]
> There is an error in the video. The Student ID for Erica Zastrow is 125, not 124.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/QCHyuVq0uFA" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Dependency Diagram

A **dependency diagram** is a visual representation of the relationships between attributes. In this video we will start to create a dependency diagram for our data. You don't have to follow along, but if you want to, we're using https://app.diagrams.net/.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/ZD80woN8m9s" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

So looking at the data above, we have the following determinants: `Student ID`, `Course ID`, and `Student ID` + `Course ID`. We also have the following functional dependencies:

- `Student ID` determines `First Name`, `Last Name`, `City`, `State`, and `Zip`.
- `Course ID` determines `Course Name`.
- `Student ID` + `Course ID` determines `Registration Date`.

# Normalization

As mentioned above, normalization is the process of organizing data in a database. There are several "normal forms" that a database can be in. The higher the normal form, the more normalized the database is. In this class we will focus on the first three normal forms.

## First Normal Form (1NF)

A database is in **First Normal Form** if it meets the following criteria:

- No multi-valued attributes. (Duplicate rows are allowed.)
- Remove all columns that are not dependent on the primary key.

Let's get started by creating new rows for any entity with multi-valued attributes. In our example, the `Course IDs,` `Course Names,` and `Registration Dates` columns are all multi-valued. Erin Donaldson, Erica Zastrow, and Erin Price are all taking two courses, so we will create a new row for each course.

After creating the new rows, we will end up with:

| Student ID | First Name | Last Name | City | State | Zip | Course ID | Course Name | Registration Date |
| ---------- | ---------- | --------- | ---- | ----- | --- | --------- | ----------- | ----------------- |
| 123        | Jimmy      | Smith     | Appleton | WI | 54911 | 1      | Data Access for Programmers | 1/05 |
| 124        | Erin       | Donaldson | Neenah   | WI | 54956 | 2      | C# Intro to Programming     | 1/06 |
| 124        | Erin       | Donaldson | Neenah   | WI | 54956 | 3      | PHP                         | 1/06 |
| 125        | Erica      | Zastrow   | Appleton | WI | 54914 | 1      | Data Access for Programmers | 1/05 |
| 125        | Erica      | Zastrow   | Appleton | WI | 54914 | 4      | Computer Programming C++    | 1/06 |
| 127        | Greg       | Olsen     | Appleton | WI | 54911 | 2      | C# Intro to Programming 	 | 1/05 |
| 129        | Kim        | Palmer    | Neenah   | WI | 54956 | 4      | Computer Programming C++    | 1/05 |
| 131        | Bryce      | Davis     | Appleton | WI | 54911 | 1      | Data Access for Programmers | 1/07 |
| 133        | Erin       | Price     | Appleton | WI | 54913 | 2      | C# Intro to Programming     | 1/07 |
| 133        | Erin       | Price     | Appleton | WI | 54913 | 3      | PHP                         | 1/05 |
| 134        | Marquise   | Alton     | Appleton | WI | 54915 | 2      | C# Intro to Programming 	 | 1/05 |

Next, we will remove any columns that are not dependent on the primary key. After doing so, we end up with these two tables:

> [!NOTE]
> We are using the * symbol here to indicate the primary keys.

| Student ID* | First Name | Last Name | City | State | Zip | Registration Date |
| ----------- | ---------- | --------- | ---- | ----- | --- | ----------------- |
| 123         | Jimmy      | Smith     | Appleton | WI | 54911 | 1/05 |
| 124         | Erin       | Donaldson | Neenah   | WI | 54956 | 1/06 |
| 124         | Erin       | Donaldson | Neenah   | WI | 54956 | 1/06 |
| 125         | Erica      | Zastrow   | Appleton | WI | 54914 | 1/05 |
| 125         | Erica      | Zastrow   | Appleton | WI | 54914 | 1/06 |
| 127         | Greg       | Olsen     | Appleton | WI | 54911 | 1/05 |
| 129         | Kim        | Palmer    | Neenah   | WI | 54956 | 1/05 |
| 131         | Bryce      | Davis     | Appleton | WI | 54911 | 1/07 |
| 133         | Erin       | Price     | Appleton | WI | 54913 | 1/07 |
| 133         | Erin       | Price     | Appleton | WI | 54913 | 1/05 |
| 134         | Marquise   | Alton     | Appleton | WI | 54915 | 1/05 |

| Course ID* | Course Name | Registration Date |
| ---------- | ----------- | ----------------- |
| 1          | Data Access for Programmers | 1/05 |
| 2          | C# Intro to Programming     | 1/06 |
| 3          | PHP                         | 1/06 |
| 1          | Data Access for Programmers | 1/05 |
| 4          | Computer Programming C++    | 1/06 |
| 2          | C# Intro to Programming     | 1/05 |
| 4          | Computer Programming C++    | 1/05 |
| 1          | Data Access for Programmers | 1/07 |
| 2          | C# Intro to Programming     | 1/07 |
| 3          | PHP                         | 1/05 |
| 2          | C# Intro to Programming     | 1/05 |

See how `Registration Date` ends up in both tables (for now), because of the dependency on both parts of the primary key. We will fix this in the next section.

This video demonstrates the process.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/9XlJATAgnKg" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Second Normal Form (2NF)

A database is in **Second Normal Form** if it meets the following criteria:

- It is in First Normal Form.
- All non-key attributes are dependent on the entire primary key. (This only applies to concatenated/composite primary keys.)

In this video we will explore how concatenated primary keys relate to Second Normal Form.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/KqSYSdXCYxM" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Remember that Registration Date is dependent on both Student ID and Course ID. So to get into second normal form, we will create a new table for Registration Date.

| Student ID* | Course ID* | Registration Date |
| ----------- | ---------- | ----------------- |
| 123         | 1          | 1/05              |
| 124         | 2          | 1/06              |
| 124         | 3          | 1/06              |
| 125         | 1          | 1/05              |
| 125         | 4          | 1/06              |
| 127         | 2          | 1/05              |
| 129         | 4          | 1/05              |
| 131         | 1          | 1/07              |
| 133         | 2          | 1/07              |
| 133         | 3          | 1/05              |
| 134         | 2          | 1/05              |

Because of this table, we can now remove the `Registration Date` column from the other two tables. This is a big win, because we it means we get to remove a bunch of duplicate data!

Take a look at our Student table:

| Student ID* | First Name | Last Name | City | State | Zip |
| ----------- | ---------- | --------- | ---- | ----- | --- |
| 123         | Jimmy      | Smith     | Appleton | WI | 54911 |
| 124         | Erin       | Donaldson | Neenah   | WI | 54956 |
| 124         | Erin       | Donaldson | Neenah   | WI | 54956 |
| 125         | Erica      | Zastrow   | Appleton | WI | 54914 |
| 125         | Erica      | Zastrow   | Appleton | WI | 54914 |
| 127         | Greg       | Olsen     | Appleton | WI | 54911 |
| 129         | Kim        | Palmer    | Neenah   | WI | 54956 |
| 131         | Bryce      | Davis     | Appleton | WI | 54911 |
| 133         | Erin       | Price     | Appleton | WI | 54913 |
| 133         | Erin       | Price     | Appleton | WI | 54913 |
| 134         | Marquise   | Alton     | Appleton | WI | 54915 |

Notice how students 124 (Erin Donaldson), 125 (Erica Zastrow), and 133 (Erin Price) are duplicated? We can now safely remove the duplicate rows! So in second normal form, we end up with:

| Student ID* | First Name | Last Name | City | State | Zip |
| ----------- | ---------- | --------- | ---- | ----- | --- |
| 123         | Jimmy      | Smith     | Appleton | WI | 54911 |
| 124         | Erin       | Donaldson | Neenah   | WI | 54956 |
| 125         | Erica      | Zastrow   | Appleton | WI | 54914 |
| 127         | Greg       | Olsen     | Appleton | WI | 54911 |
| 129         | Kim        | Palmer    | Neenah   | WI | 54956 |
| 131         | Bryce      | Davis     | Appleton | WI | 54911 |
| 133         | Erin       | Price     | Appleton | WI | 54913 |
| 134         | Marquise   | Alton     | Appleton | WI | 54915 |

And our Course table becomes really concise:

| Course ID* | Course Name |
| ---------- | ----------- |
| 1          | Data Access for Programmers |
| 2          | C# Intro to Programming     |
| 3          | PHP                         |
| 4          | Computer Programming C++    |

## Third Normal Form (3NF)

A database is in **Third Normal Form** if it meets the following criteria:

- It is in Second Normal Form.
- All non-key attributes are dependent on the primary key.

The idea on this step is to remove any columns that have more that one functional dependency. In our example, we have two columns `City,` and `State` that are dependent on `Zip.` (If I know your zip-code, I know your city and state.) So we will create a new table for `Zip,` `City,` and `State.`

| Zip*  | City     | State |
| ----- | -------- | ----- |
| 54911 | Appleton | WI    |
| 54913 | Appleton | WI    |
| 54914 | Appleton | WI    |
| 54915 | Appleton | WI    |
| 54956 | Neenah   | WI    |

The City and State can then be removed from the Student table, leaving us with:

| Student ID* | First Name | Last Name | Zip   |
| ----------- | ---------- | --------- | ---   |
| 123         | Jimmy      | Smith     | 54911 |
| 124         | Erin       | Donaldson | 54956 |
| 125         | Erica      | Zastrow   | 54914 |
| 127         | Greg       | Olsen     | 54911 |
| 129         | Kim        | Palmer    | 54956 |
| 131         | Bryce      | Davis     | 54911 |
| 133         | Erin       | Price     | 54913 |
| 134         | Marquise   | Alton     | 54915 |

And at this point, we have four tables that are in third normal form!

Let's look at the same process, but with the dependency diagram.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/t0AdL6ZiLDc" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Denormalization

Denormalization is the process of taking a normalized database and adding redundant data to it. This is done to improve performance. In this video we will continue our example from above, and denormalize our database.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/0KGe5kfJHAQ" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Remembering the Normal Forms

A common mnemonic device for remembering the normal forms is:

- 1NF: The key.
- 2NF: The whole key.
- 3NF: Nothing but the key.

This video will explain.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/U9Kf8vl6iJ4" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>


# Review Questions

1. What is a determinant?

<details>
	<summary>Show the Answer</summary>

A determinant is any attribute whose value determines other values within a row.
</details>

2. What is a functional dependency?

<details>
	<summary>Show the Answer</summary>

A functional dependency is a relationship between two attributes, typically between the determinant and the dependent attribute.
</details>

3. What are the rules for first normal form?

<details>
	<summary>Show the Answer</summary>

To be in first normal form, a table must not have any multi-value attributes, and all columns must be dependent on the primary key.
</details>

4. What are the rules for second normal form?

<details>
	<summary>Show the Answer</summary>

To be in second normal form, a table must be in first normal form, and all non-key attributes must be dependent on the entire primary key.
</details>

5. What are the rules for third normal form?

<details>
	<summary>Show the Answer</summary>

To be in third normal form, a table must be in second normal form, and all non-key attributes must be dependent on only the primary key.
</details>

6. Why might you want to denormalize a database?

<details>
	<summary>Show the Answer</summary>

To improve performance. (Not having to join tables).
</details>

