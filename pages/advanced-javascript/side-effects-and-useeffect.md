---
title: Side Effects and useEffect
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/side-effects-and-useeffect
dev: http://localhost:3006/appel/advanced-javascript/side-effects-and-useeffect
repo: https://github.com/rdappel/courses
---

# What are Side Effects?

In React, a side effect is any operation that affects something outside the scope of the current component function. Common examples include:

- Fetching data from an API
- Subscribing to a service
- Manually changing the DOM
- Setting up timers or intervals
- Logging to the console


<div class="centering">
    <img src="https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/ajs/side-effects-dark.svg" alt="" aria-hidden="true" class="adaptive dark">
    <img src="https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/ajs/side-effects-light.svg" alt="" aria-hidden="true" class="adaptive light">
</div>

Since React components should be pure functions (same input = same output), we need a special way to handle these side effects. That's where the `useEffect` hook comes in.

# Introduction to useEffect

The `useEffect` hook allows you to perform side effects in functional components. It runs after React updates the DOM, making it perfect for operations that need to happen after rendering.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here's a basic example that updates the document title:

```javascript
import { useState, useEffect } from 'react'

const Counter = () => {
	const [count, setCount] = useState(0)

	useEffect(() => {
		document.title = `Count: ${count}`
	})

	return (
		<div>
			<p>Current count: {count}</p>
			<button onClick={() => setCount(count + 1)}>Increment</button>
		</div>
	)
}

export default Counter
```

> [!NOTE] Without a dependency array, useEffect runs after every render. This is usually not what you want, which brings us to dependency arrays.

# The Dependency Array

The dependency array is the second argument to `useEffect`. It controls when the effect runs:

<div class="centering">
    <img src="https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/ajs/useeffect-dependencies-dark.svg" alt="" aria-hidden="true" class="adaptive dark">
    <img src="https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/ajs/useeffect-dependencies-light.svg" alt="" aria-hidden="true" class="adaptive light">
</div>

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here are the three ways to use the dependency array:

## 1. No Dependency Array

Runs after every render (usually not recommended):

```javascript
useEffect(() => {
	console.log('Runs after every render')
})
```

## 2. Empty Dependency Array

Runs only once after the initial render:

```javascript
useEffect(() => {
	console.log('Runs only once on mount')
}, [])
```

## 3. With Dependencies

Runs when any dependency value changes:

```javascript
useEffect(() => {
	console.log('Runs when count changes')
}, [count])
```

> [!IMPORTANT] Always include all values from the component scope that change over time and are used by the effect in the dependency array. ESLint can help catch missing dependencies.

# Practical Example: Multiple Dependencies

Let's create a component that demonstrates how dependencies work:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
import { useState, useEffect } from 'react'

const MessageDisplay = () => {
	const [count, setCount] = useState(0)
	const [name, setName] = useState('Guest')

	// Runs only once on mount
	useEffect(() => {
		console.log('Component mounted')
	}, [])

	// Runs whenever count changes
	useEffect(() => {
		console.log(`Count changed to: ${count}`)
	}, [count])

	// Runs whenever name changes
	useEffect(() => {
		console.log(`Name changed to: ${name}`)
	}, [name])

	return (
		<div>
			<h2>Hello, {name}!</h2>
			<p>Count: {count}</p>
			<button onClick={() => setCount(count + 1)}>Increment</button>
			<input 
				type="text" 
				value={name} 
				onChange={(e) => setName(e.target.value)} 
				placeholder="Enter your name"
			/>
		</div>
	)
}

export default MessageDisplay
```

# Cleanup Functions

Sometimes effects need to clean up after themselves. For example, if you set up a timer or subscribe to a service, you need to clean it up when the component unmounts or before the effect runs again.

<div class="centering">
    <img src="https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/ajs/component-lifecycle-dark.svg" alt="" aria-hidden="true" class="adaptive dark">
    <img src="https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/ajs/component-lifecycle-light.svg" alt="" aria-hidden="true" class="adaptive light">
</div>

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

To add cleanup, return a function from your effect:

```javascript
import { useState, useEffect } from 'react'

const Timer = () => {
	const [seconds, setSeconds] = useState(0)
	const [isRunning, setIsRunning] = useState(true)

	useEffect(() => {
		if (!isRunning) return

		const interval = setInterval(() => {
			setSeconds(prev => prev + 1)
		}, 1000)

		// Cleanup function
		return () => {
			clearInterval(interval)
			console.log('Timer cleaned up')
		}
	}, [isRunning])

	return (
		<div>
			<h2>Timer: {seconds} seconds</h2>
			<button onClick={() => setIsRunning(!isRunning)}>
				{isRunning ? 'Pause' : 'Resume'}
			</button>
			<button onClick={() => setSeconds(0)}>Reset</button>
		</div>
	)
}

export default Timer
```

> [!IMPORTANT] The cleanup function runs before the component unmounts and before the effect runs again (if dependencies change). This prevents memory leaks and unexpected behavior.

# Common Use Cases

Here are some common patterns for using useEffect:

## Setting Up Event Listeners

```javascript
useEffect(() => {
	const handleResize = () => {
		console.log('Window resized')
	}

	window.addEventListener('resize', handleResize)

	return () => {
		window.removeEventListener('resize', handleResize)
	}
}, [])
```

## Working with Local Storage

```javascript
const [theme, setTheme] = useState('light')

useEffect(() => {
	const savedTheme = localStorage.getItem('theme')
	if (savedTheme) {
		setTheme(savedTheme)
	}
}, [])

useEffect(() => {
	localStorage.setItem('theme', theme)
}, [theme])
```

## Syncing with External Systems

```javascript
useEffect(() => {
	const connection = createConnection()
	connection.connect()

	return () => {
		connection.disconnect()
	}
}, [])
```

> [!TIP] Keep effects focused on a single concern. If you need to do multiple unrelated things, use multiple useEffect hooks instead of combining them into one.

# Best Practices

1. **Keep effects simple** - Each effect should handle one concern
2. **Always specify dependencies** - Avoid the temptation to omit dependencies
3. **Clean up properly** - Always clean up subscriptions, timers, and listeners
4. **Don't forget the dependency array** - Forgetting it causes the effect to run on every render
5. **Use multiple effects** - Separate unrelated logic into different useEffect calls

> [!CAUTION] Avoid setting state inside useEffect without proper dependencies, as this can cause infinite loops. Always ensure your effect has appropriate dependencies or conditions to prevent continuous re-renders.
