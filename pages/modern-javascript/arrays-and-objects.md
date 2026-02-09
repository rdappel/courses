---
title: Arrays and Objects
subtitle: Modern JavaScript
hideNav: false

live: https://fvtc.software/appel/modern-javascript/arrays-and-objects
---

# JavaScript Arrays

In programming, arrays are a way to store data in a structured way. We use arrays when we have multiple items (generally of the same type) that we want to store together.

Before we jump into arrays, let's take a minute to get a project setup from scratch.

I will also show you some shortcuts to make your life easier when writing HTML.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/dmKiDKHPIVo" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Now that our project is setup, let's take a look at arrays:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/NCgWWDnhe2I" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code from the video:

```javascript
const bookTitles = [
	'It Ends With Us',
	'Onyx Storm',
	'Ugly Love',
	'Hopeless',
]

for (let i = 0; i < bookTitles.length; i++) {
	console.log(bookTitles[i])
}
```

# JavaScript Objects

Objects are another way to store data in JavaScript. Objects are used when we have multiple pieces of data that we want to store together.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/0TEXxWiymWI" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code from the video:

```javascript
const book = {
	title: 'Atomic Habits',
	author: 'James Clear',
	released: '10/16/2018'
}

console.log(`${book.title} was written by ${book.author}`)
```

## Accessing Object Properties

To access the properties of an object, we use dot notation. For example, to access the `title` property of the `book` object, we would use `book.title`.

We can also access object properties using bracket notation. Accessing it this way would look like: `book['title']`. This is useful when the property name is stored in a variable.

This video explains how to do both:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/STrzGguCKKM" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code from the video:

```javascript
const part = 'title' // 'author' // 'released'

console.log(book.title)
console.log(book['title'])
console.log(book[part])
```

## Creating Objects from Existing Variables

If we already have variables that we want to use as properties in an object, we can simplify the process by using object shorthand notation.

This video explains how to do this:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/IGqZsAYmtfg" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code from the video:

```javascript
const title = 'Atomic Habits'
const author = 'James Clear'
const released = '10/16/2018'

const book = { title, author, released }
console.log(book)
```

# Combining Arrays and Objects

We can also combine arrays and objects to create more complex data structures. Take a look:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/7OEDcJQ5iqw" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code:

```javascript

// object with an array as a property
const book = {
	title: 'Atomic Habits',
	author: 'James Clear',
	released: '10/16/2018'
	sequels: [
		'Atomic Habits 2',
		'Atomic Behaviors',
		'Atomic Actions'
	]
}

console.log(book.sequels[1])

// array of objects
const books = [{
	title: 'Atomic Habits',
	author: 'James Clear',
	released: '10/16/2018',
}, {
	title: 'Onyx Storm',
	author: 'Rebecca Yarros',
	released: '9/9/202'
}, {
	title: 'Hopeless',
	author: 'Alison Moore',
	released: '9/9/202'	
}]

console.log(books)

```

# Creating and Appending Elements

Now that we have a good understanding of arrays and objects, let's put that knowledge to use by creating and appending elements to the DOM.

This video will show you how to create a list of books using the data we have stored in an array of objects:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/YcrJ-ZWzML8" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code from the video:

```javascript
const books = [{
	title: 'Atomic Habits',
	author: 'James Clear',
	released: '10/16/2018',
}, {
	title: 'Onyx Storm',
	author: 'Rebecca Yarros',
	released: '9/9/202'
}, {
	title: 'Hopeless',
	author: 'Alison Moore',
	released: '9/9/202'	
}]


// this is the ol element in the HTML
const booksList = document.querySelector('#books')

// iterate over the books array
books.forEach(book => {
	const li = document.createElement('li') // create a new li element
	booksList.append(li) // append the li element to the ol element

	const html = `
		<span class="title">${book.title}</span>
		<span class="author">${book.author}</span>
	`

	li.innerHTML = html
})
```

# Object Destructuring

Object destructuring is a way to extract multiple properties from an object and assign them to variables in a single statement.

This video explains how to use object destructuring:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/pjpyOH_baCs" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code from the video:

```javascript
// Note: book and bookList variables removed for brevity

books.forEach(book => {
	const li = document.createElement('li')
	booksList.append(li)

	const { title, author, released } = book // object destructuring

	const html = `
		<span class="title">${title}</span>
		<span class="author">${author}</span>
		<span class="released">${released}</span>
	`

	li.innerHTML = html
})
```

# Exercise 1

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/D-bvT6LNfqs" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

In this exercise, I want you to modify the project that we have been working on. You will add a 'genres' property to each book. Each book must have at least two genres. You don't need to use the "real" genres, just make them up.

Additionally, you can use [this stylesheet](https://gist.githubusercontent.com/rdappel/4d8361c008d10b7fcc0cd966f4538d76/raw/ee16e1c6398fee450b4653692ac3c4f4549c0062/style.css) to make your page look better.

Here are some common book genres to get you started:

- Fiction
- Non-Fiction
- Fantasy
- Mystery
- Science Fiction
- Romance
- Thriller
- Historical Fiction

## Hints {#exercise-1-hints}

<details>
	<summary>How do I create a new property in an object?</summary>

You can create a new property in an object by bracket notation. For example:

```javascript
const book = {
	title: 'Atomic Habits',
	genres: [ 'Self-Help', 'Non-Fiction' ]
}
```

</details>

## Solution {#exercise-1-solution}

<details>
	<summary>Show Solution</summary>

> [!NOTE] Remember that you might have chosen different genres for your books. The solution below is just an example.

```javascript
const books = [{
	title: 'Atomic Habits',
	author: 'James Clear',
	released: '10/16/2018',
	genres: [ 'Self-Help', 'Non-Fiction' ]
}, {
	title: 'Onyx Storm',
	author: 'Rebecca Yarros',
	released: '9/9/202',
	genres: [ 'Romance', 'Fiction', 'Fantasy' ]
}, {
	title: 'Hopeless',
	author: 'Alison Moore',
	released: '9/9/202',
	genres: [ 'Mystery', 'Thriller' ]
}]
```

</details>

<details>
	<summary>Walkthrough Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/a_fieu3ygmI" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		></iframe>
			</iframe>
	</div>
</details>

# Exercise 2

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/MYJbiG90lQQ" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

For this exercise, I want you to modify the project again. Now you will get the genres from each book and display them in the list of books.

You will need to add a `ul` element to each `li` element that will contain the genres. You can use the following HTML structure:

```html

<li>
	<span class="title">Atomic Habits</span>
	<span class="author">James Clear</span>
	<span class="released">10/16/2018</span>
	<ul>
		<li>Self-Help</li>
		<li>Non-Fiction</li>
	</ul>
</li>

```

> [!NOTE] You can add the `ul` element to the `html` variable that you are creating in the `forEach` loop. You cannot add the `li` elements because each book could have a different number of genres.

## Hints {#exercise-2-hints}

<details>
	<summary>How do I add the 'ul' element?</summary>

You can simply add it to the `html` variable that you are creating in the `forEach` loop:

```javascript
	const html = `
		<span class="title">${title}</span>
		<span class="author">${author}</span>
		<span class="released">${released}</span>
		<ul class="genres"></ul> // here's where the genre li's will go
	`
```

</details>

<details>
	<summary>How do I add the 'li' elements to the 'ul' element?</summary>

You will first have to get the `ul` element from the `li` element. You can do this by using the `querySelector` method:

```javascript
const ul = li.querySelector('.genres')
```

Then you can iterate over the genres array and create a new `li` element for each genre:

```javascript
genres.forEach(genre => {
	const genreLi = document.createElement('li')
	genreLi.textContent = genre
	ul.append(genreLi)
})
```

</details>

## Solution {#exercise-2-solution}

<details>
	<summary>Show Solution</summary>

```javascript
const booksList = document.querySelector('#books')

books.forEach(book => {
	const li = document.createElement('li')
	booksList.append(li)

	const { title, author, released, genres } = book

	li.innerHTML = `
		<span class="title">${title}</span>
		<span class="author">${author}</span>
		<span class="released">${released}</span>
		<ul class="genres"></ul>
	`

	const ul = li.querySelector('ul')
	genres.forEach(genre => {
		const genreLi = document.createElement('li')
		ul.append(genreLi)
		genreLi.textContent = genre
	})
})
```

</details>

<details>
	<summary>Walkthrough Video</summary>
		<div class="video-container">
		<iframe src="https://www.youtube.com/embed/HXU5FZkDEzE" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		></iframe>
	</div>
</details>

# Object Entries, Values, and Keys

Sometimes when we have an object, we want to get an array of its properties, values, or keys. There are three methods that we can use to do this:

- `Object.entries()`: Returns an array of a given object's own enumerable string-keyed property `[key, value]` pairs.

- `Object.values()`: Returns an array of a given object's own enumerable property values.

- `Object.keys()`: Returns an array of a given object's own enumerable property names.

This video shows how to use these methods:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/iKsNnw81J8E" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code from the video:

```javascript
const [ firstBook ] = books // get the first book in the array

//console.log(firstBook)
console.log(Object.values(firstBook))
console.log(Object.keys(firstBook))
console.log(Object.entries(firstBook))
```
