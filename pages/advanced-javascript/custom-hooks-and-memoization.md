---
title: Custom Hooks & Memoization
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/custom-hooks-and-memoization
dev: http://localhost:3006/appel/advanced-javascript/custom-hooks-and-memoization
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

Let's create a simple hook that tracks whether a component is mounted:

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
	useEffect(() => {
		document.title = title
	}, [title])
}

export default useDocumentTitle
```

Now you can use it in any component:

```javascript
import useDocumentTitle from './hooks/useDocumentTitle'

const HomePage = () => {
	useDocumentTitle('Home - My App')

	return <h1>Welcome Home</h1>
}

const AboutPage = () => {
	useDocumentTitle('About - My App')

	return <h1>About Us</h1>
}
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

# Introduction to Memoization

Memoization is an optimization technique that caches the results of expensive calculations. React provides the `useMemo` hook to memoize values and prevent unnecessary recalculations.

> [!WARNING] Don't optimize prematurely. Only use memoization when you have actual performance problems. Memoization adds complexity and memory overhead.

# useMemo Hook

Let's first look at a performance problem without `useMemo`:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## The Problem: Expensive Calculations on Every Render

```javascript
import { useState } from 'react'

const ExpensiveComponent = () => {
	const [count, setCount] = useState(0)
	const [items, setItems] = useState([])

	// This runs on EVERY render, even when items don't change
	const total = items.reduce((sum, item) => sum + item.price, 0)
	console.log('Calculating total...') // This logs every time count changes!

	return (
		<div>
			<p>Total: ${total}</p>
			<p>Count: {count}</p>
			<button onClick={() => setCount(count + 1)}>Increment Count</button>
			<button onClick={() => setItems([...items, { price: 10 }])}>Add Item</button>
		</div>
	)
}
```

**The Problem**: Every time you click "Increment Count", the component re-renders and recalculates `total`, even though `items` hasn't changed. If this calculation was expensive (imagine filtering thousands of items), it would cause unnecessary slowdowns.

## The Solution: useMemo

`useMemo` returns a memoized value that only recalculates when dependencies change:

```javascript
import { useState, useMemo } from 'react'

const ExpensiveComponent = () => {
	const [count, setCount] = useState(0)
	const [items, setItems] = useState([])

	// This expensive calculation only runs when 'items' changes
	const total = useMemo(() => {
		console.log('Calculating total...') // Only logs when items change!
		return items.reduce((sum, item) => sum + item.price, 0)
	}, [items])

	return (
		<div>
			<p>Total: ${total}</p>
			<p>Count: {count}</p>
			<button onClick={() => setCount(count + 1)}>Increment Count</button>
			<button onClick={() => setItems([...items, { price: 10 }])}>Add Item</button>
		</div>
	)
}
```

Now when you click "Increment Count", the total is NOT recalculated because `items` hasn't changed. The cached value is reused instead.

## When to Use useMemo

Use `useMemo` when:

- You have expensive calculations (loops, complex computations)
- The calculation result is used in rendering
- The inputs (dependencies) don't change often

Don't use `useMemo` for:

- Simple calculations (addition, string concatenation)
- Values that change on every render anyway
- Premature optimization

# Combining Custom Hooks with Memoization

You can use memoization within custom hooks:

```javascript
import { useState, useMemo } from 'react'

const useFilteredList = (items, searchTerm) => {
	const filteredItems = useMemo(() => {
		console.log('Filtering items...')
		return items.filter(item =>
			item.name.toLowerCase().includes(searchTerm.toLowerCase())
		)
	}, [items, searchTerm])

	return filteredItems
}

// Usage
const SearchList = ({ items }) => {
	const [searchTerm, setSearchTerm] = useState('')
	const filteredItems = useFilteredList(items, searchTerm)

	return (
		<div>
			<input
				value={searchTerm}
				onChange={e => setSearchTerm(e.target.value)}
				placeholder="Search..."
			/>
			<ul>
				{filteredItems.map(item => (
					<li key={item.id}>{item.name}</li>
				))}
			</ul>
		</div>
	)
}
```

# Key Takeaways

**Custom Hooks:**
- Custom hooks extract and reuse component logic
- Must start with "use" and follow hook rules
- Can use other hooks internally
- Make code more maintainable and testable
- Common patterns: `useToggle`, `useLocalStorage`, `useFetch`

**Memoization:**
- `useMemo` caches expensive calculation results to avoid recalculation
- Only use when you have actual performance problems
- Adds complexity and memory overhead
- Measure before and after optimizing
- Best for expensive computations with stable dependencies
