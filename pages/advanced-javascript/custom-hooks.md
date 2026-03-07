---
title: Creating Custom Hooks
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/custom-hooks
dev: http://localhost:3006/appel/advanced-javascript/custom-hooks
repo: https://github.com/rdappel/courses
---

# What are Custom Hooks?

Custom hooks are JavaScript functions that use React hooks internally and allow you to extract and reuse component logic. They follow the same rules as built-in hooks and always start with "use" (like `useAuth`, `useFetch`, `useLocalStorage`).

Custom hooks help you:

- Extract reusable logic from components
- Share stateful logic between components
- Organize and simplify complex components
- Create cleaner, more maintainable code

> [!NOTE] Custom hooks are just regular functions that can call other hooks. They're not a special React feature - they're a naming convention that tells React's linter to apply hook rules.

# Creating Your First Custom Hook

Let's look at a simple example of a custom hook that sets the document title based on the current page.

You don't have to follow along with the code, but if you want to, the repo is available here: [https://github.com/rdappel/ajs-portfolio-example](https://github.com/rdappel/ajs-portfolio-example).

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
// hooks/useDocumentTitle.js
import { useEffect } from 'react'

const useDocumentTitle = (title) => {
	useEffect(() => document.title = `Ryan's Website - ${title}`, [title])
}

export default useDocumentTitle
```

Now you can use it in any component:

```javascript
import useDocumentTitle from './hooks/useDocumentTitle'

const Home = () => {
	useDocumentTitle('Home')

	return <h1>Welcome Home</h1>
}

const Contact = () => {
	useDocumentTitle('Contact')

	return <h1>Contact Me</h1>
}

// etc...
```

Instead of repeating the `useEffect` logic in every component, we extracted it into a reusable custom hook.

# Custom Hook: useToggle

A common pattern is toggling boolean values (modals, menus, etc.). Let's create a hook for that:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
// hooks/useToggle.js
import { useState } from 'react'

const useToggle = (initialValue = false) => {
	const [value, setValue] = useState(initialValue)

	const toggle = () => setValue(prev => !prev)
	const setTrue = () => setValue(true)
	const setFalse = () => setValue(false)

	return [value, toggle, setTrue, setFalse]
}

export default useToggle
```

Using the hook:

```javascript
import useToggle from './hooks/useToggle'

const Modal = () => {
	const [isOpen, toggle, open, close] = useToggle(false)

	return (
		<div>
			<button onClick={open}>Open Modal</button>
			
			{isOpen && (
				<div className="modal">
					<h2>Modal Content</h2>
					<button onClick={close}>Close</button>
				</div>
			)}
		</div>
	)
}
```

# Custom Hook: useLocalStorage

Let's create a hook that syncs state with localStorage:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
// hooks/useLocalStorage.js
import { useState, useEffect } from 'react'

const useLocalStorage = (key, initialValue) => {
	// Get from localStorage or use initial value
	const [value, setValue] = useState(() => {
		try {
			const item = window.localStorage.getItem(key)
			return item ? JSON.parse(item) : initialValue
		} catch (error) {
			console.error(error)
			return initialValue
		}
	})

	// Update localStorage when value changes
	useEffect(() => {
		try {
			window.localStorage.setItem(key, JSON.stringify(value))
		} catch (error) {
			console.error(error)
		}
	}, [key, value])

	return [value, setValue]
}

export default useLocalStorage
```

Using it is just like `useState`:

```javascript
import useLocalStorage from './hooks/useLocalStorage'

const Settings = () => {
	const [theme, setTheme] = useLocalStorage('theme', 'light')
	const [fontSize, setFontSize] = useLocalStorage('fontSize', 16)

	return (
		<div>
			<select value={theme} onChange={e => setTheme(e.target.value)}>
				<option value="light">Light</option>
				<option value="dark">Dark</option>
			</select>

			<input
				type="range"
				min="12"
				max="24"
				value={fontSize}
				onChange={e => setFontSize(Number(e.target.value))}
			/>
		</div>
	)
}
```

The settings persist across page refreshes automatically!

# Custom Hook: useFetch

Data fetching is a common operation. Let's create a reusable hook for it:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
// hooks/useFetch.js
import { useState, useEffect } from 'react'

const useFetch = (url) => {
	const [data, setData] = useState(null)
	const [loading, setLoading] = useState(true)
	const [error, setError] = useState(null)

	useEffect(() => {
		const fetchData = async () => {
			try {
				setLoading(true)
				const response = await fetch(url)
				
				if (!response.ok) {
					throw new Error(`HTTP error! status: ${response.status}`)
				}
				
				const json = await response.json()
				setData(json)
				setError(null)
			} catch (err) {
				setError(err.message)
				setData(null)
			} finally {
				setLoading(false)
			}
		}

		fetchData()
	}, [url])

	return { data, loading, error }
}

export default useFetch
```

Using the hook:

```javascript
import useFetch from './hooks/useFetch'

const UserList = () => {
	const { data, loading, error } = useFetch('https://api.example.com/users')

	if (loading) return <p>Loading...</p>
	if (error) return <p>Error: {error}</p>

	return (
		<ul>
			{data.map(user => (
				<li key={user.id}>{user.name}</li>
			))}
		</ul>
	)
}
```

# Rules for Custom Hooks

Custom hooks must follow the same rules as built-in hooks:

1. **Name must start with "use"** - This lets React know it's a hook
2. **Only call at the top level** - Don't call inside loops, conditions, or nested functions
3. **Only call from React functions** - Call from components or other custom hooks

```javascript
// ✅ Good - starts with "use"
const useFormInput = (initialValue) => { ... }

// ❌ Bad - doesn't follow naming convention
const formInput = (initialValue) => { ... }

// ✅ Good - called at top level
const MyComponent = () => {
	const [name, setName] = useFormInput('')
	return <input value={name} onChange={setName} />
}

// ❌ Bad - called conditionally
const MyComponent = () => {
	if (someCondition) {
		const [name, setName] = useFormInput('') // ❌ Don't do this
	}
}
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

Create a custom hook called `useOnlineStatus` and use it in a component.

Your hook should:

1. Track whether the browser is online (`navigator.onLine`)
2. Listen for `online` and `offline` events
3. Return a boolean like `isOnline`
4. Clean up event listeners when unmounted

Then create a component that uses the hook and renders:

- `Status: Online` when connected
- `Status: Offline` when disconnected

## Hints {#exercise-1-hints}

<details>
	<summary>How do I initialize state?</summary>

Use `navigator.onLine` as the initial state value.

```javascript
const [isOnline, setIsOnline] = useState(navigator.onLine)
```

</details>

<details>
	<summary>How do I listen for connection changes?</summary>

Inside `useEffect`, add event listeners for both events and remove them in the cleanup function.

```javascript
window.addEventListener('online', handleOnline)
window.addEventListener('offline', handleOffline)
```

</details>

## Solution {#exercise-1-solution}

<details>
	<summary>Show the Answer</summary>

```javascript
// hooks/useOnlineStatus.js
import { useEffect, useState } from 'react'

const useOnlineStatus = () => {
	const [isOnline, setIsOnline] = useState(navigator.onLine)

	useEffect(() => {
		const handleOnline = () => setIsOnline(true)
		const handleOffline = () => setIsOnline(false)

		window.addEventListener('online', handleOnline)
		window.addEventListener('offline', handleOffline)

		return () => {
			window.removeEventListener('online', handleOnline)
			window.removeEventListener('offline', handleOffline)
		}
	}, [])

	return isOnline
}

export default useOnlineStatus
```

```javascript
// components/ConnectionStatus.jsx
import useOnlineStatus from '../hooks/useOnlineStatus'

const ConnectionStatus = () => {
	const isOnline = useOnlineStatus()

	return <p>Status: {isOnline ? 'Online' : 'Offline'}</p>
}

export default ConnectionStatus
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

# Key Takeaways

- Custom hooks extract and reuse component logic
- Must start with "use" and follow hook rules
- Can use other hooks internally
- Make code more maintainable and testable
- Common patterns: `useToggle`, `useLocalStorage`, `useFetch`
