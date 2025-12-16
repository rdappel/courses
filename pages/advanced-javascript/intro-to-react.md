---
title: Introduction to React
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/intro-to-react
dev: http://localhost:3006/appel/advanced-javascript/intro-to-react
repo: https://github.com/rdappel/courses
---

# What is React?

React is a JavaScript library for building user interfaces. It was created by Facebook (meta) and is now maintained by Facebook and the community. React allows you to build complex UIs from small, reusable pieces called components.

In this lesson, we'll set up a React project using Vite and create our first component.

# Setting Up a React Project with Vite

Let's create a new React project using Vite. Vite is a build tool that provides a fast development experience for modern web applications.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/LMx7wF6FmP8" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

To create a new React project, run the following command in your terminal:

```bash
npm create vite@latest .
```

or 
```bash
npm create vite@7.3.0 .
```

When prompted:
- Select **React** as the framework
- Select **JavaScript - SWC** as the variant

Then, install the dependencies and start the development server:

```bash
npm install
npm run dev
```

Your React application should now be running at `http://localhost:5173`.

## Code Cleanup

When you create a new Vite + React project, it comes with some boilerplate code that we don't need.

Let's clean it up by deleting the following files:

- `src/assets/` (folder and the file inside it)
- `src/App.css`
- `public/vite.svg`

We'll keep the following but delete the content from:

- `src/index.css`

Additionally, we modified `src/main.jsx`. Here is the updated code:

```javascript
const App = () => {
  return "hi"
}

export default App
```

# Understanding Functional Components

React components are functions that return JSX (JavaScript XML). JSX looks like HTML but it's actually JavaScript. Let's look at a simple functional component.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/uSe3blnwRd4" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is our Card component:

```javascript
const Card = () => {
	return <div className="card">Ryan</div>
}

export default Card
```

And then we use it in our App component:

```javascript
import Card from './components/Card.jsx'

const App = () => {
	return (
		<div>
			<Card />
		</div>
	)
}
```

> [!NOTE] I forgot to fix the "class" attribute to "className" in the video. I will update this in the next video.

# Styling with Inline Styles

In React, you can apply styles using the `style` attribute. Unlike HTML where you use a string, in React you use a JavaScript object.

To save you a bit of time, here is the css that we will use in the following video:

```javascript
const cardStyle = {
	fontFamily: 'sans-serif',
	backgroundColor: '#ccc',
	maxWidth: '400px',
	borderRadius: '8px',
	padding: '8px',
}
```

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/v5ee02vFfhQ" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here's the code example from the video:

```javascript
const Card = () => {
	return <div className="card" style={cardStyle}>Ryan</div>
}

export default Card
```
