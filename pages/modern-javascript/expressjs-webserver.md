---
title: ExpressJS Webserver
subtitle: Modern JavaScript
hideNav: false

live: https://fvtc.software/appel/modern-javascript/expressjs-webserver
dev: http://localhost:3006/appel/modern-javascript/expressjs-webserver

---

# ExpressJS Webserver

In this unit, we will create a simple web server and API using ExpressJS. Express is a fast, web framework for Node.js. It is designed for building web applications and APIs. This video will walk you through getting started:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/5KBDK2jbd0U" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code for our app.js file:

```javascript
const express = require('express')
const app = express()
const port = 3000

app.listen(port, () => console.log(`Listening on port: ${port}`))
```

# Handling Requests

Express allows us to handle different types of requests. We can use the `app.get()` method to handle GET requests. Take a look:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/E8VEfuJixGg" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here are the routes that we added in the video:

```javascript
app.get('/', (request, response) => {
	response.send('hello world')
})

app.get('/test', (request, response) => {
	response.send('hello from test route')
})
```

## Responding with JSON

We can also respond with JSON data. Take a look:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/XxYLeFjIK8I" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the pokemon data that we added in the video:

```javascript
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
```

Here is the code from the video:

```javascript
// allow us to send json
app.use(express.json())

// and the two new routes
app.get('/api/v1/random', (request, response) => {
	const randomNumber = Math.floor(Math.random() * 100) + 1
	response.send({ randomNumber })
})

app.get('/api/v1/random-pokemon', (request, response) => {
	const r = Math.floor(Math.random() * 9)
	response.send(pokemon[r])
})
```

## Responding with HTML

We can also respond with HTML. Take a look:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/NQZacxfimVY" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code from the video:

```javascript
// add path module and root of the static files
const path = require('path')
const root = path.join(__dirname, 'public')

// added middleware to serve static files
app.use(express.static('public'))

// updated the root route to serve an html file
app.get('/', (request, response) => {
	response.sendFile('index.html', { root })
})
```

# Front and Back End Communication

Next, we will look at how to communicate between the front-end and back-end of our application. We will use the `fetch` API to make requests from the front-end to the back-end.

First we need to add a route to our back-end that will accept a parameter. Take a look:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/eOQp71t7W3c" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the endpoint that we added in the video:

```javascript
app.get('/api/v1/pokemon/:id', (request, response) => {
	const { id } = request.params
	const found = pokemon.find(p => p.id.toString() === id)
	if (found) response.send(found)
	else response.send({ error: { message: `Could not find pokemon with id: ${id}` }})
})
```

Now that our back-end is ready, we can make a request from the front-end. Take a look:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/xF9A6_Bn_Vg" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code from the video:

Our new route for getting a specific pokemon:

```javascript
app.get('/pokemon/:id', (request, response) => {
	response.sendFile('index.html', { root })
})
```

And here is our front-end code:

```javascript
(async () => {
	const h2 = document.querySelector('h2')
	const h3 = document.querySelector('h3')

	const { pathname } = window.location
	const [, searchType, id ] = pathname.split('/')

	const url = searchType === 'pokemon'
		? `/api/v1/pokemon/${id}`
		: '/api/v1/random-pokemon'
	
	const result = await fetch(url)
	const { name, type } = await result.json()

	h2.textContent = name
	h3.textContent = type
})()
```

# Exercise 1

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/0TnBvngaCyM" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

For this exercise, create a new back end route that will return a random pokemon based on the type. You should be able to pass the type as a parameter in the URL. For example, `/api/v1/random-pokemon/grass` should return a random grass type pokemon.

Then create a new front end route that will display the name and type of the random pokemon that is returned. The route should be `/type/:type`.

## Hints {#exercise-1-hints}

<details>
	<summary>How do I figure out which back-end point to call?</summary>

Before we used this code:

```javascript
const url = searchType === 'pokemon'
	? `/api/v1/pokemon/${id}`
	: '/api/v1/random-pokemon'
```

Now that we have a new route, you will need to update this code to call the correct route based on the type that is passed in the URL.

One way to do this is to add a new condition to the ternary operator that checks for the type route. You can then use the type to build the URL for the fetch request.

```javascript
const url = searchType === 'pokemon'
	? `/api/v1/pokemon/${id}`
	: searchType === 'type'
		? `/api/v1/random-pokemon/${id}`
		: '/api/v1/random-pokemon'
```

That's pretty hard to read! So you might want to move it into a separate function to make it easier to understand.

```javascript
const getUrl = (searchType, id) => {
	if (searchType === 'pokemon') return `/api/v1/pokemon/${id}`
	if (searchType === 'type') return `/api/v1/random-pokemon/${id}`
	return '/api/v1/random-pokemon'
}
```

</details>

## Solution {#exercise-1-solution}

<details>
	<summary>Show the Answer</summary>

Here is the back-end code for the new route:

```javascript
app.get('/api/v1/random-pokemon/type/:type', (request, response) => {
	const { type } = request.params
	const found = pokemon.filter(p => p.type.toLowerCase() === type.toLowerCase())
	const r = Math.floor(Math.random() * found.length)
	if (found.length > 0) response.send(found[r])
	else response.send({ error: { message: `Could not find pokemon with type: ${type}` }})
})
```

And here is the front-end code for the new route:

```javascript
(async () => {
	const h2 = document.querySelector('h2')
	const h3 = document.querySelector('h3')

	const { pathname } = window.location
	const [, searchType, id ] = pathname.split('/')

	const url = (() => {
		if (searchType === 'pokemon') return `/api/v1/pokemon/${id}`
		if (searchType === 'type') return `/api/v1/random-pokemon/${id}`
		return '/api/v1/random-pokemon'
	})()
	
	const result = await fetch(url)
	const { name, type } = await result.json()

	h2.textContent = name
	h3.textContent = type
})()
```

</details>

<details>
	<summary>Walkthrough Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/Gk3sV9vk8VY" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# Rest Client

I want to show you a tool that I use to test my back-end routes. It's called REST Client. You can install it in Visual Studio Code. Here is a video that shows you how to use it:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/wYtrOn42tJY" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code that we used in the video:

```http
### Variables
@url = http://localhost:3010/api/v1
@type = water


### Random Pokemon
GET {{url}}/random-pokemon


### Specific Pokemon
GET {{url}}/pokemon/5


### Random with type
GET {{url}}/random-pokemon/{{type}}
```

# Post Requests

Finally, we will add a new endpoint that allows us to add a new pokemon to our list of pokemon. We'll use REST Client to test our new endpoint.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/UYvmsRdYOcQ" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code we added to our `app.js` file:

```javascript
app.post('/api/v1/add', (request, response) => {
	const { id, name, type } = request.body
	const found = pokemon.find(p => p.id.toString() === id.toString())
	if (found) response.send({ error: { message: `Pokemon with id: ${id}, already exists`} })
	else pokemon.push({ id, name, type })
})
```

And here is the REST Client code we used to test our new endpoint:

```http
### Add new pokemon
POST {{url}}/add
Content-Type: application/json

{ 
	"id": 10,
	"name": "Caterpie",
	"type": "Bug"
}
```