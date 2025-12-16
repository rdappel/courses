---
title: Props in React
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/props
dev: http://localhost:3006/appel/advanced-javascript/props
repo: https://github.com/rdappel/courses

todo: add video links: https://www.youtube.com/watch?v=8dvMeKm1WB4
a: https://www.youtube.com/watch?v=bUlK2SBXMfw
c: https://www.youtube.com/watch?v=bgSMKyT_PJw
dist: https://www.youtube.com/watch?v=Dbyhnd0gQH8
---

# Understanding Props

```css
:root {
	--bg-color: #f9f9f9;
	--card-bg-color: #e9e9e9;
	--card-border-color: #9e9e9e;
	--card-shadow-color: rgba(0, 0, 0, 0.3);
}

body {
	background-color: var(--bg-color);
	margin: 0;
	font-family: Arial, sans-serif;
}
```

```javascript
const cardStyle = {
	fontFamily: "Sans-serif",
	backgroundColor: "var(--card-bg-color)",
	border: "1px solid var(--card-border-color)",
	boxShadow: "0 2px 2px var(--card-shadow-color)",
	borderRadius: "8px",
	maxWidth: "400px",
	margin: "8px",
    	cursor: 'pointer',
}

const headerStyle = {
	textAlign: "center",
	margin: "0",
	padding: "4px",
	borderBottom: "1px solid var(--card-border-color)",
}
```

Props (short for "properties") are how we pass data from one component to another in React. Think of props as arguments to a function - they allow you to customize what a component displays or how it behaves.

Props are read-only, which means a component cannot modify its own props. This makes React components predictable and easier to debug.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here's a simple example of using props:

```javascript
// Code example placeholder
```

# The Children Prop

The `children` prop is a special prop in React that allows you to pass components or elements between the opening and closing tags of a component. This is useful when you want to create wrapper components.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here's an example of using the children prop:

```javascript
// Code example placeholder
```

# Keys for Lists

When rendering lists in React, you need to provide a `key` prop for each item. Keys help React identify which items have changed, been added, or been removed. This is important for performance and proper rendering.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here's an example of rendering a list with keys:

```javascript
// Code example placeholder
```

## Best Practices for Keys

- Keys should be unique among siblings (not globally unique)
- Use a stable identifier from your data (like an ID) rather than the array index
- Avoid using the array index as a key if the list can be reordered
- Keys don't need to be globally unique, only unique within a particular list

> [!IMPORTANT] Never use randomly generated values as keys! Keys need to be stable across re-renders.

# Installing React Icons

To add icons to our React application, we'll use the `react-icons` library. This library provides access to popular icon sets like Font Awesome, Material Design, and more.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Install react-icons with npm:

```bash
npm i react-icons
```

You can then import icons from different icon sets:

```javascript
import { FaStar, FaRegStar } from 'react-icons/fa'
import { MdEmail } from 'react-icons/md'
import { AiFillHeart } from 'react-icons/ai'
```

# Creating a Star Rating Component

Let's create a reusable star rating component using Font Awesome icons from react-icons. This component will display a visual rating using filled and outlined stars.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the finished StarRating component:

```javascript
import { FaStar, FaRegStar } from 'react-icons/fa'

const StarRating = ({ rating, color }) => {
	return (
		<div>
			{[1, 2, 3, 4, 5].map((star) =>
				star <= rating 
					? <FaStar key={star} color={color || "black"} />
					: <FaRegStar key={star} color={color || "black"} />
			)}
		</div>
	)
}

export default StarRating
```

## How the StarRating Component Works

Let's break down how this component works:

1. **Props**: The component accepts two props:
   - `rating`: A number (typically 1-5) representing the rating
   - `color`: An optional color for the stars (defaults to "black")

2. **Array Iteration**: We create an array `[1, 2, 3, 4, 5]` and use `map` to render each star

3. **Conditional Rendering**: For each star number, we check if it's less than or equal to the rating:
   - If yes: render a filled star (`<FaStar />`)
   - If no: render an outlined star (`<FaRegStar />`)

4. **Keys**: Each star has a `key` prop set to the star number for proper React rendering

5. **Default Color**: We use the logical OR operator (`||`) to provide a default color if none is specified

## Using the StarRating Component

You can use the StarRating component like this:

```javascript
import StarRating from './components/StarRating'

const App = () => {
	return (
		<div>
			<h2>Product Rating</h2>
			<StarRating rating={4} color="gold" />
			
			<h2>Movie Rating</h2>
			<StarRating rating={5} color="red" />
			
			<h2>Default Color</h2>
			<StarRating rating={3} />
		</div>
	)
}
```

> [!TIP] You can extend this component to support half-stars or make it interactive by adding click handlers!
