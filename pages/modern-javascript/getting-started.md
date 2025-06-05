---
title: Getting Started
subtitle: Modern JavaScript
hideNav: false

live: https://fvtc.software/appel/modern-javascript/getting-started
---

# Getting Started

JavaScript is a programming language that was created to make web pages interactive. It is also used in many other environments, such as Node.js, which is used to create server-side applications. In this course, we will be doing both!

## Software Used in this Course

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/m5JbppYDn80" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

All of the software used in this course is free. Installing them on your computer will probably be the best experience. If you don't want to (or can't) install them on your computer, contact your instructor and they can have a virtual machine set up for you.

The software we will be using is:

1. **Visual Studio Code (VS Code)** as our code editor. VS Code is a free, open-source code editor that is available for Windows, Mac, and Linux. You can download it here: [https://code.visualstudio.com/](https://code.visualstudio.com/)

2. **Node.js**, which is a JavaScript runtime environment. Node.js allows us to run JavaScript code outside of a web browser. You can download it here: [https://nodejs.org/en/](https://nodejs.org/en/). I would recommend downloading the LTS version, which is the most stable version.

3. **Git**, which is a version control system. Git allows us to keep track of changes to our code. Some of you have probably used Git before, but if you haven't, I have a series of videos that will walk you through installing Git, and get you started with the basics. You can watch them here: [https://fvtc.software/appel/version-control-essentials/getting-started](https://fvtc.software/appel/version-control-essentials/getting-started)

4. **A web browser**. Any modern web browser will work, but I recommend using Google Chrome: [https://www.google.com/chrome/](https://www.google.com/chrome/). This is the browser that will be used in the videos.

# A Brief History of JavaScript

JavaScript was created in 1995, and was designed to be a simple scripting language to make web pages more interactive. It has evolved into a full-fledged programming language.

In the early days of JavaScript, it was used primarily for simple tasks like form validation, and since every browser had its own implementation of JavaScript, it was difficult to write cross-browser code. However, in 2015, the ECMAScript 2015 (ES6) specification was released, which standardized JavaScript and added many new features. Since then, JavaScript has become a very popular language for both front-end and back-end development.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/U0aCrHZYrks" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

> [!NOTE] The video above mentions a VS Code extension called "Live Server". If you had any difficulty installing it, there is an installation link here: [https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)

> [!CAUTION] New students often confuse JavaScript with Java. They are two completely different languages. JavaScript was created by Netscape in 1995, while Java was created by Sun Microsystems in 1991. The only thing they have in common is the word "Java" in their names.

# Writing JavaScript Code

Let's start by creating a simple webpage and writing some JavaScript code.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/beEIte8U09w" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code that we wrote in the video:

```html
<!DOCTYPE html>
<html lang="en">

<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Document</title>
</head>

<body>
	<h1>Hi</h1>
	<p>My name is Ryan.</p>
	<article>Hello</article>
</body>
<script>

console.log('Hello World')

</script>

</html>
```

> [!TIP] Even thouhg I will give you the code in the video, you should be following along and typing it out yourself. I am posting the code here incase your copy doesn't work for some reason. Again, make sure that you are typing the code yourself, and completing the exercises as they come up.

## Playing around with our Webpage

Continuing from the previous video, let's modify our webpage and see what happens.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/TNAMTdReE6o" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code that we wrote in the video:

```html
<!DOCTYPE html>
<html lang="en">

<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Document</title>
</head>

<body>
	<h1>Hi</h1>
	<p>My name is Ryan.</p>
	<article>Hello</article>
</body>
<script>

const article = document.querySelector('article')
const now = new Date().toLocaleTimeString()

if (now.includes('PM')) {
	article.textContent = 'Good Evening'
} else if (now.includes('AM')) {
	article.textContent = 'Good Morning'
}

</script>

</html>
```
