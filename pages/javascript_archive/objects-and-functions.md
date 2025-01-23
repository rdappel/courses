---
title: Objects and Functions
subtitle: Modern JavaScript
hideNav: false

live: https://fvtc.software/appel/javascirpt_archive/objects-and-functions
---

# Objects in JavaScript

Objects are a way to group related data together. They are similar to objects in C#, but since JavaScript is a dynamic language, they are more flexible.

## Getting the Starter Code

Before we get started, let's fork and clone down some starter code.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/ZTguyiACw1k" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

You can find the starter code [here](https://github.com/RDAppel/example-website2).

## Looking at the Starter Code Objects

Let's take a look at the starter code that we just cloned down.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/WOOPFgqyLtQ" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code that we added to our JavaScript file:

```javascript
const title = "Adidas"
const text = "Lorem ipsum dolor sit amet, consectetur adipiscing elit."
const image = "https://images.pexels.com/photos/2529148/pexels-photo-2529148.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"
const color = "#deaf01"

const cardInfo4 = { title, text, image, color }
```

> [!NOTE] GitHub Copilot created the image url for us. It actually just used the image for the Nike shoes from cardInfo1.

## Printing Objects to the Console

Let's print the cardInfo objects to the console to see what they look like.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/s6yrF5FmwNo" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# Functions

Similar to Methods in C#, functions are a way to group code together to perform a specific task. Usually we assign a name to a function, and then call that function by name when we want to run the code inside of it.

## Defining and Calling Functions

Let's look at how to create and call a function in JavaScript.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/5XaS9A_kKEQ" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is an example of a function:

```javascript
function createCard() {
	console.log("hi")
}
```

When we want to run the code inside of the function, we call it by name:

```javascript
createCard()
```

## Returning Values from Functions

Functions can also return values. When a function returns a value, we can assign that value to a variable, or use it in other ways.

Here is an example of a function that returns a value:

```javascript
function createCard() {
	return 5
}
```

When we call the function, we can assign the return value to a variable:

```javascript
const x = createCard() // x will be 5
```

Here is the finished code from the video:

```javascript
function createCard() {
	const card = document.querySelector('.card')
	const h1 = card.querySelector('h1')
	h1.textContent = cardInfo1.title
}

createCard()
```

## Parameters and Arguments

Functions can also accept parameters. Parameters are variables that are passed into the function. The values that are passed into the function are called arguments.

> [!NOTE] The terms "parameter" and "argument" are often used interchangeably, but there is a difference. A parameter is a variable that is part of the function definition. An argument is the value that is passed into the function when it is called.

Here is an example of a function that accepts a parameter:

```javascript
function sayHello(name) {
	console.log(`Hello ${name}!`)
}
```

In this example, the `name` variable is a parameter. When we call the function, we pass in the argument "John":

```javascript
sayHello("John")
```

In this video we will make our createCard function accept a card element and the card info as parameters:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/m6A5wXUYF1I" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the finished code from the video:

```javascript
function createCard(card, info) {
	card.style.backgroundImage = `url(${info.image})`
	card.style.color = info.color

	const h1 = card.querySelector('h1')
	h1.textContent = cardInfo.title

	const p = card.querySelector('p')
	p.textContent = cardInfo.text
}

const cards = document.querySelectorAll('.card')
createCard(cards[0], cardInfo1)
createCard(cards[1], cardInfo2)
createCard(cards[2], cardInfo3)
```

# Functions as Data and Arrow Functions

Remember that function is a data type, just like a string or a number. This video shows how we can assign a function to a variable, and then call that function by using the variable name, and then we turn the createCard function into an arrow function:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/Q76SPkXuU_4" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the `createCard` function as an arrow function:

```javascript
const createCard = (card, info) => {
	card.style.backgroundImage = `url(${info.image})`
	card.style.color = info.color

	const h1 = card.querySelector('h1')
	h1.textContent = cardInfo.title

	const p = card.querySelector('p')
	p.textContent = cardInfo.text
}
```

## Why Use Arrow Functions?

Arrow functions are a newer feature of JavaScript. They are a little bit shorter than regular functions. This doesn't seem like a big deal, but when you are passing functions into other functions, it can make your code a lot easier to read.

Let's take a look:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/ZhFn3IxC6mU" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the finished code from the video:

```javascript
const cards = document.querySelectorAll('.card')
//createCard(cards[0], cardInfo1)
createCard(cards[1], cardInfo2)
createCard(cards[2], cardInfo3)

setTimeout(() => createCard(cards[0], cardInfo1), 1000)
```

# Functions that Return Objects

The syntax for functions that return objects can be a bit challenging, since they both use curly braces. Let's take a closer look:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/4sIKaBCwMY0" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

In the video, we wrapped the cardInfo objects into a function that returns an object:

```javascript
const getCardInfo = index => {
	if (index === 0) return {
		"title": "Nike",
		"text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
		"image": "https://images.pexels.com/photos/2529148/pexels-photo-2529148.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
		"color": "#deaf01"
	}

	if (index === 1) return {
		"title": "Independent",
		"text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
		"image": "https://images.pexels.com/photos/5657417/pexels-photo-5657417.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
		"color": "#554a33"
	}

	if (index === 2) return {
		"title": "Michael Kors",
		"text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
		"image": "https://images.pexels.com/photos/2783873/pexels-photo-2783873.jpeg",
		"color": "#01322f"
	}
}
```

That allows us to use a loop to create our cards:

```javascript
const cards = document.querySelectorAll('.card')
for (let i = 0; i < cards.length; i++) {
	createCard(cards[i], cardInfo[i])
}
```

## Object Destructuring

Object destructuring is a way to extract properties from an object and assign them to variables. This video shows how to use object destructuring to make our createCard function a little bit shorter:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/OjjvdcjRwRA" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

After we use object destructuring, our createCard function looks like this:

```javascript
const createCard = (card, { title, text, image, color }) => {
	card.style.backgroundImage = `url(${image})`
	card.style.color = color

	const h1 = card.querySelector('h1')
	h1.textContent = title

	const p = card.querySelector('p')
	p.textContent = text
}
```

# Real World Example

Let's take a minute to look at a real world example of some code that is running live on a website. In fact, it's part of the site that you're looking at right now!

Take a peek:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/4b_BVHUrVeE" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# Exercises

[Objects and Functions Exercises](/appel/javascript/objects-and-functions-exercises)
