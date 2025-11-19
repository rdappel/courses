---
title: Selecting DOM Elements
subtitle: Modern JavaScript
hideNav: false

live: https://fvtc.software/appel/modern-javascript/selecting-dom-elements
---

# Selecting DOM Elements

In this unit, we will learn how to select DOM elements using the `querySelector`, `querySelectorAll`, and `getElementById` methods. We will also learn how to attach a JavaScript file to an HTML page.

## Getting the Example Website

Before we get started, let's clone down some starter code.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/LrX_aqDzScQ" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the link to fork the [starter code repo](https://github.com/fvtc/js-ryans-webpage). Feel free to change the name of the repo. Once you have forked the repo, you can clone it down to your local machine using `git clone <repo-url-from-github>`.

# The Document Object Model (DOM)

The Document Object Model (DOM) is a programming interface for HTML documents. It represents the page so that programs can change the document structure, style, and content. The DOM represents the document as nodes and objects. That way, programming languages can connect to the page.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/Ko8cqxtMM_s" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# Creating and Attaching our JavaScript File

Now that we have our starter code, let's create a JavaScript file and attach it to our HTML page.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/VFA7MnRLcn4" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code that we added to our HTML:

```html
<script src="site.js" defer></script>
```

The `defer` attribute tells the browser to wait until the HTML has been parsed before executing the JavaScript. This is important because we want to make sure that the JavaScript has access to the DOM before it tries to select any elements.

Here is the code that we ended up with in our JavaScript file:

```javascript
console.log(document.querySelector('h1'))
```

# Selecting Elements by Tag

As you saw in the video above, we can select DOM elements using the `querySelector` method. This method takes a CSS selector as an argument and returns the first element that matches the selector.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/DFH5pZcOU10" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# Exercise 1

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/MBofviwr960" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

In this exercise, you will modify the example that we've been working on, to change the text "Main Content Section" color to red.

I want you to store the element in a variable called `mainContentSection` and then use that variable to change the color.

## Hints {#exercise-1-hints}

<details>
	<summary>How do I get the element and store it into a variable?</summary>

Since the element is the first `h2` tag on the page, you can use the `querySelector` method to get it and store it in a variable.

```javascript
const mainContentSection = document.querySelector('h2')
```

</details>

<details>
	<summary>How do I change the color of the text to red?</summary>

You can use the `style` property of the element to change the color.

```javascript
mainContentSection.style.color = 'red'
```

Or using the HEX value:

```javascript
mainContentSection.style.color = '#ff0000'
```


</details>

## Solution {#exercise-1-solution}

<details>
	<summary>Show the Answer</summary>


```javascript
const mainContentSection = document.querySelector('h2')
mainContentSection.style.color = 'red'
// or
// mainContentSection.style.color = '#ff0000'
```

</details>

<details>
	<summary>Walkthrough Video</summary>
		<div class="video-container">
		<iframe src="https://www.youtube.com/embed/zFBywMC9-og" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		></iframe>
	</div>
</details>

# Selecting Elements by ID and Class

In addition to selecting elements by tag, we can also select elements by ID and class. Take a look:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/f2iTTieiV14" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code from the video:

```javascript
const about = document.querySelector('#about') // id="about"
about.style.color = 'orange'

const active = document.querySelector('.active') // class="active"
active.style.color = 'blue'
```

# Combining Selectors

We can also combine selectors to get more specific elements. Take a look:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/tQ1hiAY5do0" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# Selecting Multiple Elements

In addition to selecting a single element, we can also select multiple elements using the `querySelectorAll` method. This method takes a CSS selector as an argument and returns a NodeList of elements that match the selector.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/GcNWAsREhIY" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code from the video:

```javascript
const activeElements = document.querySelectorAll('.active')

//activeElements.forEach(el => el.style.border = '1px solid red')

for (let i = 0; i < activeElements.length; i++)
{
	activeElements[i].style.border = '1px solid red'
}
```

# Exercise 2

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/FuFd4qPmZ14" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>




## Hints {#exercise-2-hints}

<details>
	<summary>How do I get select the link without using a class or id?</summary>

If you notice that it's the only link (anchor tag) in the footer, you can use the `querySelector` method to get it.

```javascript
const link = document.querySelector('footer a')
```

</details>

<details>
	<summary>How do I select the link using an id (or class)?</summary>

You will need to add an id (or class) to the link in the HTML file and then use the `querySelector` method to get it.

Here I added an id to the link:

```html
<a id="fork" href="https://github.com/fvtc/js-ryans-webpage">Fork this project on GitHub.</a>
```

```javascript
const link = document.querySelector('#fork')
```

</details>

<details>
	<summary>How do I add an underline to the link?</summary>

You can use the `style` property of the element to change the text decoration.

```javascript
link.style.textDecoration = 'underline'
```

</details>


## Solution {#exercise-2-solution}

<details>
	<summary>Show the Answer</summary>


```javascript
//const link = document.querySelector('footer a')

const link = document.querySelector('#fork')
link.style.textDecoration = 'underline'
```

</details>

<details>
	<summary>Walkthrough Video</summary>
		<div class="video-container">
		<iframe src="https://www.youtube.com/embed/ezmt96JrW6I" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		></iframe>
	</div>
</details>

# Selecting the Body and Title Elements

In addition to selecting elements within the body of the page, we can also select the body and title elements themselves. Take a look:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/1KtzP8TvKKM" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code from the video:

```javascript
document.body.style.backgroundColor = 'lightgray'
document.title = "Ryan's website"
```

# Selecting Parent and Ancestor Elements

Sometimes we have access to an element and we want to select its parent element, or an ancestor element. We can do this using the `parentElement` property, and the `closest` method.

A common use case for this is when the user interacts with an element and we want to change the style of the parent element. Take a look:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/Tp9Lu7gzfh4" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code from the video:

```javascript
const contact = document.querySelector('#contact')

contact.addEventListener('mouseover', () => {
	//contact.parentElement.style.backgroundColor = 'lightblue'
	contact.closest('nav').style.backgroundColor = 'lightblue'
})
```

# Pushing Changes to GitHub

We can run git commands in the terminal to push our changes to GitHub. If you're not sure how to push your changes to GitHub, check out the video below:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/uDzciIcvbMU" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Remember, you can always refer back to the [Getting Started with Version Control](/appel/version-control-essentials/getting-started) unit if you need a refresher.

