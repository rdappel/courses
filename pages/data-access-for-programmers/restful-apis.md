---
title: RESTful APIs
subtitle: Data Access for Programmers
hideNav: false

live: https://fvtc.software/appel/data-access-for-programmers/restful-apis
---

# RESTful APIs

As we learned earlier in the semester, a RESTful API is an API that uses HTTP methods and URLs to perform operations on a database. RESTful APIs can be created using most programming languages, such as PHP, C#, and Python.

In this unit we will learn how to create a RESTful API using JavaScript. We will have to design an ERD, create the database, and then write an application that will allow us to access the data in the database.

The first big decission to make... what kind of data should we store in our database?

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/k8L_ThWMRCc" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# Pokémon API

We're going to create a RESTful API that stores information about Pokémon and their types.

## Data Normalization

In the following videos we'll be designing the database for our Pokémon API. We'll start by creating an ERD. The Wikipedia page that we'll be using is [here](https://en.wikipedia.org/wiki/List_of_generation_I_Pok%C3%A9mon). We'll be using the first generation of Pokémon, so we'll be using the first table on the page.

In this video we'll go over the dependencies and normalization of the columns.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/A51l5ZnLcIE" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## ERD Creation

In this video we'll create the ERD for our Pokémon API.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/PnRV2UAanB8" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Building the Database

Now that we have our ERD, we can create the database. We'll be using MySQL Workbench to create the database.

You should go through the process of creating the database yourself, but if you get stuck, here is the script that we used to create the database.

```sql

DROP TABLE IF EXISTS `pokemon`;
CREATE TABLE `pokemon` (
	`ID` INT NOT NULL,
	`Name` VARCHAR(45) NOT NULL,
	`EvolvesFrom` INT NULL,
	`Notes` VARCHAR(255) NULL,
	PRIMARY KEY (`ID`)
);

INSERT INTO `pokemon` VALUES ('1', 'Bulbasaur', NULL, 'It uses the nutrients that are stored in the seed on its back in order to grow...');
INSERT INTO `pokemon` VALUES ('2', 'Ivysaur', '1', 'When it is exposed to sunlight, the seed, now a bud, grows so much that it apparently loses the ability to stand on its hind legs...');
INSERT INTO `pokemon` VALUES ('3', 'Ivysaur', '2', 'Its English name is a portmanteau of "Venus" (relating to the Venus flytrap) and "dinosaur"...');
INSERT INTO `pokemon` VALUES ('4', 'Charmander', NULL, 'Charmander is a bipedal, lizard-like Pokémon with a flame at the tip of its tail. Its English name is a portmanteau of "char" and "salamander"...');


DROP TABLE IF EXISTS `pokemontypes`;
CREATE TABLE `pokemontypes` (
	`PokemonID` INT NOT NULL,
	`TypeID` INT NOT NULL,
	PRIMARY KEY (`PokemonID`, `TypeID`)
);

INSERT INTO `pokemontypes` VALUES ('1', '1');
INSERT INTO `pokemontypes` VALUES ('1', '2');
INSERT INTO `pokemontypes` VALUES ('2', '1');
INSERT INTO `pokemontypes` VALUES ('2', '2');
INSERT INTO `pokemontypes` VALUES ('3', '1');
INSERT INTO `pokemontypes` VALUES ('3', '2');
INSERT INTO `pokemontypes` VALUES ('4', '3');


DROP TABLE IF EXISTS `types`;
CREATE TABLE `types` (
	`ID` INT NOT NULL,
	`Name` VARCHAR(45) NOT NULL,
	PRIMARY KEY (`ID`)
);

INSERT INTO `types` VALUES ('1', 'Grass');
INSERT INTO `types` VALUES ('2', 'Poison');
INSERT INTO `types` VALUES ('3', 'Fire');
INSERT INTO `types` VALUES ('4', 'Flying');
```

Here's the video of our database creation.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/kVUrX4no5Gw" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# Creating a RESTful Service

Everything up to this point should have been review from the previous couple of units. Now we're going to start creating our RESTful service. We'll be using Node.js and a couple of packages to create our service. We'll be using the Express framework to create our service, and we'll be using the mysql2 package to connect to our database.

You can learn more about Express [here](https://expressjs.com/), and you can learn more about mysql2 [here](https://www.npmjs.com/package/mysql2).

## Project Setup

In this video we'll create a new project and install the packages that we'll need.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/wUNe3206HTc" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

The commands that were executed in the video are:

```bash
npm init
npm i express mysql2
node index
```

## Writing our Server Code

Now that our project is setup, and we have an `index.js` file, we can start writing our server code.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/A-zl5U2n870" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here's the code in the video:

```javascript
const express = require('express')
const app = express()

express.json()

app.get('/', (request, response) => {
	response.send({ test: "test" })
})

app.listen(3000)
```

## Connecting to our Database

Now that our server is listening for a connection, we can have it connect to our pokemon database. This video will show you how to do that.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/uYLSJ9VgF3g" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here's the updated code from the video:

```javascript
const express = require('express')
const mysql = require('mysql2')

const app = express()

const connection = mysql.createConnection({
	host: "localhost",
	user: "root",
	password: "root",
	database: "pokemon"
})

console.log(connection)

express.json()

app.get('/', (request, response) => {
	console.log("user connected")
	response.send({ test: "test" })
})

app.listen(3000)
```

## Querying our Database

Now that we have connected our app to our database, we can start querying it. This video will show you how to insert SQL commands into our application.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/M5QgQg8QIBA" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here's the updated code from the video:

```javascript
const express = require('express')
const mysql = require('mysql2')

const app = express()

const connection = mysql.createConnection({
	host: "localhost",
	user: "root",
	password: "root",
	database: "pokemon"
})

express.json()

app.get('/', (request, response) => {
	
	const sql = "SELECT ID AS Number, Name FROM pokemon"
	connection.query(sql, (error, results) => {
		if (error) {
			console.log(error)
			response.send({ error: "There was an sql error."})
			}
		else {
			console.log(results)
			response.send(results)
		}
	})
})

app.listen(3000)
```

# Adding Endpoints

Previously we created an endpoint that returned all of the Pokémon in our database. Now we're going to add endpoints that will allow us to get a single Pokémon, and to get all of the types for a Pokémon.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/5CFfwPRgr2w" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code for the new endpoints:

```javascript
app.get('/pokemon', (request, response) => {
	
	const sql = "SELECT p.ID, p.Name, ef.Name AS EvolvesFrom, p.Notes FROM pokemon p LEFT OUTER JOIN pokemon ef ON p.EvolvesFrom = ef.ID"
	connection.query(sql, (error, results) => {
		if (error) {
			console.log(error)
			response.send({ error: "There was an sql error."})
		else {
			console.log(results)
			response.send(results)
		}
	})
})
```
## Endpoint that Calls a Proecedure

That last query was a little complicated, so we're going to create a stored procedure that will do the same thing. This video will show you how to create a stored procedure, and how to call it from our application.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/P0ikpd1LCHg" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the updated "/pokemon" endpoint:

```javascript
app.get('/pokemon', (request, response) => {
	
	const sql = "CALL sp_GetPokemon()"
	connection.query(sql, (error, results) => {
		if (error) {
			console.log(error)
			response.send({ error: "There was an sql error."})
		else {
			console.log(results)
			response.send(results[0])
		}
	})
})
```

And the new endpoint that retreives a single Pokémon:

```javascript
app.get('/pokemon/3', (request, response) => {
	
	const sql = "CALL sp_GetPokemonByID(3)"
	connection.query(sql, (error, results) => {
		if (error) {
			console.log(error)
			response.send({ error: "There was an sql error."})
		else {
			console.log(results)
			response.send(results[0])
		}
	})
})
```

## Request with Parameters

To avoid having to create an endpoint for every single pokémon, we're going to create an endpoint that takes a parameter. This video will show you how to do that.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/JJx6xncokoU" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Avoiding SQL Injection

In the previous video we created an endpoint that takes a parameter. This video will show you how to avoid SQL injection attacks.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/c1BGcY-aWOY" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the updated endpoint:

```javascript
app.get('/pokemon/:number', (request, response) => {
	const number = request.params.number
	
	const sql = `CALL sp_GetPokemonByID(?)` // stop sql injection attack
	connection.query(sql, [ number ], (error, results) => {
		if (error) {
			console.log(error)
			response.send({ error: "There was an sql error."})
		else {
			console.log(results)
			response.send(results[0])
		}
	})
})
```

# Exercise 1

Create an endpoint that returns all of the pokémon that match a given type.

Watch this video, it will help you get started.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/pClLW59qobg" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the SQL code for the stored procedure:

```sql
CREATE PROCEDURE sp_GetPokemonByType(IN typeName VARCHAR(45))
SELECT p.ID, p.Name, t.Name AS TypeName FROM pokemon p
JOIN pokemontypes pt ON p.ID = pt.PokemonID
JOIN types t ON pt.TypeID = t.ID
WHERE t.Name = typeName
```

<details>
	<summary>Show the Answer</summary>

```javascript
app.get('/type/:typeName', (request, response) => {
	const typeName = request.params.typeName
	
	const sql = `CALL sp_GetPokemonByType(?)` // stop sql injection attack
	connection.query(sql, [ typeName ], (error, results) => {
		if (error) {
			console.log(error)
			response.send({ error: "There was an sql error."})
		else {
			console.log(results)
			response.send(results[0])
		}
	})
})
```
</details>

# Review Questions

1. What is Express?

<details>
	<summary>Show the Answer</summary>

Express is a framework for creating web applications in Node.js.
</details>

2. What is mysql2?

<details>
	<summary>Show the Answer</summary>

Mysql2 is a package that allows us to connect to a MySQL database.
</details>

3. What is an API endpoint?

<details>
	<summary>Show the Answer</summary>

An API endpoint is a URL that we can use to access data in our database.
</details>

