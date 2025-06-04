---
title: ES Modules and Bundling
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/esm-and-bundling
dev: http://localhost:3006/appel/advanced-javascript/esm-and-bundling
repo: https://github.com/rappel/courses
---

# ES Modules and Bundling

## CommonJS Modules

Originally, JavaScript did not have a built-in module system. Developers used various libraries and patterns to manage dependencies. One of the most popular patterns was CommonJS, which Node.js adopted. You probably recognize this pattern:

```javascript
// use express
const express = require('express')

// use a custom module
const myModule = require('./myModule')

// export a module
module.exports = {
    // your module here
}
```

CommonJS modules are synchronous and load dependencies on demand. This pattern works well for server-side applications, but have limited use in the browser.

## ES Modules

In 2015, ECMAScript 6 introduced a new module system called ECMAScript Modules (ESM). This system is asynchronous and allows for static analysis of dependencies. You can recognize ES modules by the `import` and `export` keywords:

```javascript
// import a module
import express from 'express'

// import a custom module
import myModule from './myModule'

// export a module
export default {
    // your module here
}
```

ES Modules are the standard for modern JavaScript applications, and as of around 2018, all major browsers support them, requiring only that you use the `type="module"` attribute in your script tags.

```html
<script type="module" src="app.js"></script>
```

Let's create a module.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

Here is the code for the main.js file:

```javascript
import { add, subtract } from './math.js'

console.log(add(5, 3)) // 8

console.log(subtract(5, 3)) // 2
```
Here is the code for the math.js file:

```javascript
export add = (a, b) => a + b

export subtract = (a, b) => a - b
```

And here is how we linked the JavaScript files in our HTML file:

```html
<script type="module" src="main.js"></script>
```

# Bundling

Bundling is the process of combining multiple JavaScript files into a single file. This is important for performance, as it reduces the number of HTTP requests made by the browser. Bundling also allows for minification, which reduces the size of the JavaScript file by removing whitespace and comments.

## Getting Started with Vite

In this class we will be using Vite, a modern build tool that is fast and easy to use. Vite uses Rollup under the hood for bundling, and it supports ES Modules out of the box.

Let's turn our JavaScript files into a bundle using Vite.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

Here is the command that I ran to initialize Vite in my project:

```bash
npm init vite@latest . --template vanilla
```

This command creates a new Vite project in the current directory using the vanilla JavaScript template. It also installs all the necessary dependencies.

After that, I ran the following command to start the development server:

```bash
npm run dev
```

This command starts the Vite development server, which serves the files in the `dist` directory and watches for changes to the source files.

After that, I ran the following command to build the project for production:

```bash
npm run build
```

# Exercise 1

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

In this exercise, you will create a simple ES Module that exports a function to calculate the area of a rectangle. You will then import this module into another file and use it to calculate the area of a rectangle with given width and height.

Call the module `rectangle.js` and create a function called `calculateArea` that takes two parameters: `width` and `height`. The function should return the area of the rectangle (width * height).

## Hints {#exercise-1-hints}

<details>
    <summary>How do I create a module?</summary>

You can create a module by creating a new JavaScript file (e.g., `rectangle.js`) and using the `export` keyword to export your function.

</details>

<details>
    <summary>How do I export a function from a module?</summary>
You can export a function from a module by using the `export` keyword before the function declaration. For example:

```javascript
export const myFunction = () => {
    // your code here
}
```
</details>

<details>
    <summary>How do I import a module?</summary>

You can import a module by using the `import` keyword followed by the name of the function you want to import and the path to the module. For example:
    
```javascript
import { myFunction } from './myModule.js'
```

</details>

## Submission {#exercise-1-submission}

Once you have completed the exercise, paste your `rectangle.js` code into the text area below and click the "Submit" button.

<div class="exercise-submission" data-language="javascript">
    <textarea placeholder="Paste your code here..."></textarea>
    <button type="button" class="submit-button">Submit</button>
</div>

## Solution {#exercise-1-solution}

> [!NOTE] Your instructor can see if you look at the answer before you finish the exercise. Please try to solve it on your own first.

<details>
    <summary>Show the Answer</summary>

Here is the code for the `rectangle.js` file:

```javascript
export const calculateArea = (width, height) => {
    return width * height
}
```

And here is how you would import and use this module in `main.js`:

```javascript
import { calculateArea } from './rectangle.js'

console.log(calculateArea(5, 10)) // 50
```

</details>

<details>
    <summary>Walkthrough Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>




