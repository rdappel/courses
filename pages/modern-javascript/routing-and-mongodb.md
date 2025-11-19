---
title: Advanced Routing and MongoDB
subtitle: Modern JavaScript
hideNav: false

live: https://fvtc.software/appel/modern-javascript/routing-and-mongodb
---

# Advanced Routing and MongoDB

As ExpressJS applications grow in complexity, it becomes necessary to organize your routes into separate files. This allows you to break your application into smaller, more manageable pieces, and makes it easier to maintain and update your code.

In this unit, we will learn how to create a modular ExpressJS application that uses MongoDB to store and retrieve data.

# Modular Routing

In the previous unit, we created a simple ExpressJS application that contained all of our routes in a single file. This works fine for small applications, but as your application grows, it can become difficult to manage all of your routes in a single file.

To solve this problem, we can break our routes into separate files and organize them into a folder structure that makes sense for our application. Take a look:

## Moving Static Routes

In this video we will move our static (front-end) routes to a separate file and folder.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/_-sNlNgtTR0" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is our new folder structure:

```plaintext
.
├── public
|   ├── scripts
│   │   └── site.js
│   ├── styles
│   │   └── site.css
│   └── index.html
├── routes
│   └── static.js
├── app.js
├── endpoints.rest
└── package.json
```

And here is our new `static.js` file:

```javascript
const path = require('path')
const router = require('express').Router()

const root = path.join(__dirname, '..', 'public')

router.get('/', (request, response) => {
	response.sendFile('index.html', { root })
})

router.get('/pokemon/:id', (request, response) => {
	response.sendFile('index.html', { root })
})

router.get('/type/:type', (request, response) => {
	response.sendFile('index.html', { root })
})

module.exports = router
```

And here is the code that we added to our `app.js` file:

```javascript
// attach endpoints
app.use(require('./routes/static'))
```

## Moving API Routes

In this video we will move our API routes to a separate file and folder.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/_M6wy5aeivE" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is our new folder structure for the routes:

```plaintext
└── routes
	├── api
	│   └── v1
	│       └── pokemon.js
	└── static.js
```

Here is the code that we added to our `pokemon.js` file:

```javascript
const router = require('express').Router()

const pokemon = [
	{ id: 1, name: 'Bulbasaur', type: 'Grass' },
	{ id: 2, name: 'Ivysaur', type: 'Grass' },
	{ id: 3, name: 'Venusaur', type: 'Grass' },
	{ id: 4, name: 'Charmander', type: 'Fire' },
	{ id: 5, name: 'Charmeleon', type: 'Fire' },
	{ id: 6, name: 'Charizard', type: 'Fire' },
	{ id: 7, name: 'Squirtle', type: 'Water' },
	{ id: 8, name: 'Wartortle', type: 'Water' },
	{ id: 9, name: 'Blastoise', type: 'Water' },
]

router.get('/random', (request, response) => {
	const r = Math.floor(Math.random() * 9)
	response.send(pokemon[r])
})

router.post('/add', (request, response) => {
	const { id, name, type } = request.body
	console.log({ id, name, type })

	const found = pokemon.find(p => p.id.toString() === id.toString())
	if (found) response.send({ error: { message: `Pokemon with id: ${id}, already exists`} })
	else pokemon.push({ id, name, type })
})

router.get('/:id', (request, response) => {
	const { id } = request.params
	const found = pokemon.find(p => p.id.toString() === id)
	if (found) response.send(found)
	else response.send({ error: { message: `Could not find pokemon with id: ${id}` }})
})

router.get('/random/:type', (request, response) => {
	const { type } = request.params
	const found = pokemon.filter(p => p.type.toLowerCase() === type.toLowerCase())
	const r = Math.floor(Math.random() * found.length)
	if (found.length > 0) response.send(found[r])
	else response.send({ error: { message: `Could not find pokemon with type: ${type}` }})
})

module.exports = router
```

And here is the code that we added to our `app.js` file:

```javascript
app.use('/api/v1/pokemon', require('./routes/api/v1/pokemon'))
```

> [!NOTE] The more specific routes should be placed before the more general routes. This is because ExpressJS will match the first route that it finds that matches the request.

# MongoDB

MongoDB is a popular NoSQL database that is used by many developers to store and retrieve data.

## Register and Create a Database

In this video, we will register for a free MongoDB Atlas account and create a new project and database.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/QmvpMH24Xoo" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the link to [Register for MongoDB Atlas](https://www.mongodb.com/cloud/atlas/register).

## Adding Data to the Database

Next we will add a few pokemon to our database, and then install the `mongodb` package using npm.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/U8ynFmU2EwQ" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

To install the `mongodb` package, run the following command:

```bash
npm install mongodb@6.3.0
```

## Connection Setup

Next let's setup our project to connect to our MongoDB database.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/eMKvLPl1P9M" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code for the `dbconnect.js` file:

```javascript
const { MongoClient, ObjectId } = require('mongodb')

const { uri } = require('./secrets/mongodb.json')

const client = new MongoClient(uri)
```

## Retrieving Data from MongoDB

In this video, we will retrieve data from our MongoDB database and display it in our ExpressJS application.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/ot8pR2TFSRc" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the updated `dbconnect.js` file:

```javascript
const { MongoClient, ObjectId } = require('mongodb')

const { uri } = require('./secrets/mongodb.json')

const client = new MongoClient(uri)

const getCollection = async (dbName, collectionName) => {
	await client.connect()
	return client.db(dbName).collection(collectionName)
}

module.exports = { getCollection, ObjectId }
```

And here is the updated endpoint in our `pokemon.js` file:

```javascript
router.get('/:number', async (request, response) => {
	const { number } = request.params
	const collection = await getCollection('PokemonAPI', 'Pokemon')
	console.log(await collection.findOne({ "number": parseInt(number) }))
	response.send('done')
})
```

## Updating our GET endpoints

In this video, we will update our GET endpoints to retrieve data from our MongoDB database.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/uKQbrd-coL4" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here are the updated endpoints in our `pokemon.js` file:

```javascript
router.get('/random', async (_, response) => {
	const collection = await getCollection('PokemonAPI', 'Pokemon')
	const count = await collection.countDocuments()
	const number = Math.floor(Math.random() * count) + 1
	const found = await collection.findOne({ "number": parseInt(number) })
	if (found) response.send(found)
	else response.send({ error: { message: `Could not find pokemon with number: ${number}` }})
})

router.get('/:number', async (request, response) => {
	const { number } = request.params
	const collection = await getCollection('PokemonAPI', 'Pokemon')
	const found = await collection.findOne({ "number": parseInt(number) })
	if (found) response.send(found)
	else response.send({ error: { message: `Could not find pokemon with number: ${number}` }})
})

router.get('/random/:type', async (request, response) => {
	const { type } = request.params
	const collection = await getCollection('PokemonAPI', 'Pokemon')
	const foundOfType = await collection.find({ "type": type }).toArray()
	const count = foundOfType.length
	if (count === 0) response.send({ error: { message: `Could not find pokemon with type: ${type}` }})
	const number = Math.floor(Math.random() * count)// + 1 <-- error in the video
	//console.log(number, foundOfType)
	response.send(foundOfType[number])
})
```

> [!NOTE] There was a small error in the video regarding the calculation for the random number. The "+ 1" should be removed from the calculation.

## Updating our POST endpoint

In this video, we will update our POST endpoint to add data to our MongoDB database.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/S6jEhjbExo8" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

First we made a change to how we got the connection:

```javascript
let collection = null
const getPokemon = async () => {
	if (!collection) collection = await getCollection('PokemonAPI', 'Pokemon')
	return collection
}
```

Then we updated our POST endpoint:

```javascript
router.post('/add', async (request, response) => {
	const { number, name, type } = request.body
	const collection = await getPokemon()
	const { acknowledged, insertedId } = await collection.insertOne({ number, name, type })
	response.send({ acknowledged, insertedId })
})
```

## Getting an Item by ID

In this video, we will update our GET endpoint to retrieve data from our MongoDB database by ID.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/hHr4HnPLW-g" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the new endpoint in our `pokemon.js` file:

```javascript
router.get('/byId/:id', async (request, response) => {
	const { id } = request.params
	const collection = await getPokemon()
	const found = await collection.findOne({ _id: new ObjectId(id) })
	if (found) response.send(found)
	else response.send({ error: { message: `Could not find pokemon with id: ${id}` }})
})
```

# Exercise 1

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/rKa_VDQoNLY" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

For this exercise, you will create and test two new endpoints:

1. `GET /api/v1/pokemon/` - This endpoint should retrieve all of the pokemon from the database.

	- Hint: Use the `find` method without any parameters to retrieve all of the pokemon.

2. `GET /api/v1/pokemon/byName/:name` - This endpoint should retrieve a pokemon from the database by name. Additionally, I want you to use the following query parameters, to make the search case-insensitive:

```javascript
const regexp = new RegExp(`^${name}`, 'i')
const found = await collection.findOne({ name: regexp })
```

Then test your endpoints using the `endpoints.rest` file.


## Hints {#exercise-1-hints}

<details>
	<summary>How do I use the `find` method to retrieve all of the pokemon?</summary>

You can use the `find` method without any parameters like this:

```javascript
const found = await collection.find().toArray()
```

</details>

## Solution {#exercise-1-solution}

<details>
	<summary>Show the Answer</summary>

The "GET /api/v1/pokemon/" endpoint should look like this:

```javascript
router.get('/', async (_, response) => {
	const collection = await getPokemon()
	const found = await collection.find().toArray()
	response.send(found)
})
```

The "GET /api/v1/pokemon/byName/:name" endpoint should look like this:

```javascript
router.get('/byName/:name', async (request, response) => {
	const { name } = request.params
	const collection = await getPokemon()
	const regexp = new RegExp(`^${name}`, 'i')
	const found = await collection.findOne({ name: regexp })
	if (found) response.send(found)
	else response.send({ error: { message: `Could not find pokemon with name: ${name}` }})
})
```

Here are the tests that you can use in the `endpoints.rest` file:

```plaintext
### Get all pokemon
GET {{url}}/pokemon/

### Get pokemon by name
GET {{url}}/pokemon/byName/ivysaur
```

</details>

<details>
	<summary>Walkthrough Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/x-SD0EDfpFw" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>