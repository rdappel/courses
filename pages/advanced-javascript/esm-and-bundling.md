---
title: ES Modules and Bundling
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/esm-and-bundling
dev: http://localhost:3006/appel/advanced-javascript/esm-and-bundling
repo: https://github.com/rdappel/courses
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

In 2015, ECMAScript 6 introduced a new module system called ECMAScript Modules (ESM). This system is asynchronous and allows for static analysis of dependencies. You can recognize ES modules by the `import` and `export` keywords.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>


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
npm create vite@latest .
```

This command creates a new Vite project in the current directory. It also installs all the necessary dependencies.

After that, I ran the following command to start the development server:

```bash
npm run dev
```

This command starts the Vite development server, which serves the files in the `dist` directory and watches for changes to the source files.

After that, I ran the following command to build the project for production:

```bash
npm run build
```

