---
title: React Props
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/props
dev: http://localhost:3006/appel/advanced-javascript/props
repo: https://github.com/rdappel/courses

todo: update code and video for children and keys
---

# React Props

Props (short for "properties") are how we pass data from one component to another in React. Think of props as arguments to a function - they allow you to customize what a component displays or how it behaves.

Props are read-only, which means a component cannot modify its own props. This makes React components predictable and easier to debug.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/8dvMeKm1WB4" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here's the updated Card component:

```javascript
const Card = ({ title, }) => {
	return <div className="card" style={cardStyle}>
		<h3>{title}</h3>
		<p>{text || "This is default text"}</p>
	</div>
}
```

And the updated App.jsx code:

```javascript
import Card from './components/Card.jsx'

const App = () => {
	return (
		<div>
			<Card title="Ryan" text="Hello, this is Ryan's card." />
			<Card title="Jim" />
		</div>
	)
}
```

# The Children Prop

The `children` prop is a special prop in React that allows you to pass components or elements between the opening and closing tags of a component. This is useful when you want to create wrapper components.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/fsbMyaJs3FY" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the updated Card component code from the video:

```javascript
const Card = ({ title, children }) => {
	return <div className="card" style={cardStyle}>
		<h3>{title}</h3>
		{children}
	</div>
}
```

> The updated App component code is in the next section.

# Keys for Lists

When rendering lists in React, you need to provide a `key` prop for each item. Keys help React identify which items have changed, been added, or been removed. This is important for performance and proper rendering.

Here is the updated App component that renders a list:

```javascript
import Card from './components/Card.jsx'

const App = () => {

	return (
	)
}
```

## Best Practices for Keys

- Keys should be unique among siblings (not globally unique)
- Use a stable identifier from your data (like an ID)
- Keys don't need to be globally unique, only unique within a particular list

> [!IMPORTANT] Never use randomly generated values as keys! Keys need to be stable across re-renders.

# Style Update

Let's add some basic styles to our Card component to make it look better.

The following CSS can be added to `src/index.css`:

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

> [!TIP] Use CSS variables (custom properties) to make it easy to manage colors and styles across your application. These can be used in your component styles as shown in the upcoming video.

Replace the existing `cardStyle` object in `Card.jsx` with the following:

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

This video walks through the style updates:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/bgSMKyT_PJw" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the updated Card component code with the new styles:

```javascript
const Card = ({ title, children }) => {
	return <div className="card" style={cardStyle}>
		<h3 style={headerStyle}>{title}</h3>
		{children}
	</div>
}
```

# Installing React Icons

To add icons to our React application, we'll use the `react-icons` library. This library provides access to popular icon sets like Font Awesome, Material Design, and more.

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

# Rating Component

Let's create a reusable star rating component using Font Awesome icons from react-icons. This component will display a visual rating using filled and outlined stars.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/bUlK2SBXMfw" width="100%" height="100%" frameborder="0"
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

Here is the code for the updated Card component that uses the StarRating component:

```javascript
import StarRating from './StarRating.jsx'

const Card = ({ title, children, rating }) => {
	return <div className="card" style={cardStyle}>
		<h3 style={headerStyle}>{title}</h3>
		<div>
			{children}
			<StarRating rating={rating} color="gold" />
		</div>
	</div>
}
```

> [!CAUTION] Passing the rating value to the Card component as a prop is called "prop drilling". In larger applications, this can become cumbersome. In future lessons, we'll explore state management solutions to handle this more elegantly.