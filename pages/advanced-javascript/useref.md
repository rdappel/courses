---
title: The useRef Hook
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/useref
dev: http://localhost:3006/appel/advanced-javascript/useref
repo: https://github.com/rdappel/courses
---

# What is useRef?

The `useRef` hook creates a mutable reference that persists across component re-renders. Unlike state, updating a ref does not trigger a re-render. This makes `useRef` perfect for:

- Accessing DOM elements directly
- Storing values that need to persist but shouldn't cause re-renders
- Keeping track of previous values
- Storing timers or intervals

<div class="centering">
    <img src="https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/ajs/useref-vs-usestate-dark.svg" alt="" aria-hidden="true" class="adaptive dark">
    <img src="https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/ajs/useref-vs-usestate-light.svg" alt="" aria-hidden="true" class="adaptive light">
</div>

# Basic useRef Syntax

The `useRef` hook returns a mutable object with a `current` property. This object persists for the entire lifetime of the component:

```javascript
import { useRef } from 'react'

const myRef = useRef(initialValue)
// myRef.current = initialValue
```

> [!NOTE] The `current` property is where the actual value is stored. You can read and write to it directly without causing re-renders.

# Accessing DOM Elements

One of the most common uses of `useRef` is to access DOM elements directly, similar to `document.getElementById()` in vanilla JavaScript:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
import { useRef } from 'react'

const FocusInput = () => {
	const inputRef = useRef(null)

	const handleFocus = () => {
		inputRef.current.focus()
	}

	return (
		<div>
			<input ref={inputRef} type="text" placeholder="Click the button to focus me" />
			<button onClick={handleFocus}>Focus Input</button>
		</div>
	)
}

export default FocusInput
```

> [!IMPORTANT] Attach the ref to a DOM element using the `ref` attribute. After the component mounts, `inputRef.current` will reference the actual DOM node.

## Common DOM Manipulations

Here are some common things you can do with DOM refs:

```javascript
// Focus an input
inputRef.current.focus()

// Select text in an input
inputRef.current.select()

// Scroll to an element
elementRef.current.scrollIntoView()

// Get element dimensions
const width = elementRef.current.offsetWidth
const height = elementRef.current.offsetHeight

// Play/pause a video
videoRef.current.play()
videoRef.current.pause()
```

# useRef vs useState

Understanding when to use `useRef` vs `useState` is important:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
import { useState, useRef } from 'react'

const RefVsState = () => {
	const [stateCount, setStateCount] = useState(0)
	const refCount = useRef(0)

	const incrementState = () => {
		setStateCount(stateCount + 1)
		console.log('State count:', stateCount + 1)
	}

	const incrementRef = () => {
		refCount.current++
		console.log('Ref count:', refCount.current)
	}

	return (
		<div>
			<h3>State Count: {stateCount}</h3>
			<h3>Ref Count: {refCount.current}</h3>
			<button onClick={incrementState}>Increment State (Re-renders)</button>
			<button onClick={incrementRef}>Increment Ref (No Re-render)</button>
		</div>
	)
}

export default RefVsState
```

> [!CAUTION] In the example above, clicking "Increment Ref" won't update the displayed count until the component re-renders for another reason. This is because changing a ref doesn't trigger a re-render.

**Use useState when:**
- The value should trigger a re-render when it changes
- You need to display the value in the UI
- React needs to track the value for proper rendering

**Use useRef when:**
- You need to store a value that persists between renders but doesn't affect the UI
- You're working with DOM elements directly
- You're storing timers, intervals, or other mutable values

# Storing Previous Values

A clever use of `useRef` is to keep track of a previous value of a prop or state:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
import { useState, useRef, useEffect } from 'react'

const PreviousValue = () => {
	const [count, setCount] = useState(0)
	const prevCountRef = useRef()

	useEffect(() => {
		prevCountRef.current = count
	}, [count])

	const prevCount = prevCountRef.current

	return (
		<div>
			<h3>Current: {count}</h3>
			<h3>Previous: {prevCount}</h3>
			<button onClick={() => setCount(count + 1)}>Increment</button>
		</div>
	)
}

export default PreviousValue
```

> [!NOTE] The useEffect runs after the render, so during render, `prevCountRef.current` still holds the old value. After rendering, it gets updated to the current value.

# Managing Timers and Intervals

`useRef` is perfect for storing timer IDs that need to persist across renders and be cleaned up:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
import { useState, useRef } from 'react'

const Stopwatch = () => {
	const [seconds, setSeconds] = useState(0)
	const [isRunning, setIsRunning] = useState(false)
	const intervalRef = useRef(null)

	const start = () => {
		if (isRunning) return
		
		setIsRunning(true)
		intervalRef.current = setInterval(() => {
			setSeconds(prev => prev + 1)
		}, 1000)
	}

	const stop = () => {
		if (intervalRef.current) {
			clearInterval(intervalRef.current)
			intervalRef.current = null
			setIsRunning(false)
		}
	}

	const reset = () => {
		stop()
		setSeconds(0)
	}

	return (
		<div>
			<h2>Stopwatch</h2>
			<p>Time: {seconds} seconds</p>
			<button onClick={start} disabled={isRunning}>Start</button>
			<button onClick={stop} disabled={!isRunning}>Stop</button>
			<button onClick={reset}>Reset</button>
		</div>
	)
}

export default Stopwatch
```

> [!IMPORTANT] Always clean up intervals and timers to prevent memory leaks. Store the timer ID in a ref so you can clear it later.

# Combining useRef with Controlled Components

You can combine `useRef` with controlled components to add additional functionality without managing extra state:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
import { useState, useRef } from 'react'

const SearchForm = () => {
	const [searchTerm, setSearchTerm] = useState('')
	const inputRef = useRef(null)

	const handleSubmit = (e) => {
		e.preventDefault()
		console.log('Searching for:', searchTerm)
		setSearchTerm('')
		inputRef.current.focus()
	}

	const handleClear = () => {
		setSearchTerm('')
		inputRef.current.focus()
	}

	return (
		<form onSubmit={handleSubmit}>
			<input
				ref={inputRef}
				type="text"
				value={searchTerm}
				onChange={(e) => setSearchTerm(e.target.value)}
				placeholder="Search..."
			/>
			<button type="submit">Search</button>
			<button type="button" onClick={handleClear}>Clear</button>
		</form>
	)
}

export default SearchForm
```

# Forwarding Refs to Child Components

Sometimes you need to pass a ref from a parent component to a child component. React provides `forwardRef` for this:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
import { useRef, forwardRef } from 'react'

// Child component that accepts a ref
const CustomInput = forwardRef((props, ref) => {
	return (
		<input
			ref={ref}
			{...props}
			style={{ padding: '8px', fontSize: '16px' }}
		/>
	)
})

// Parent component
const ParentComponent = () => {
	const inputRef = useRef(null)

	const handleFocus = () => {
		inputRef.current.focus()
	}

	return (
		<div>
			<CustomInput ref={inputRef} placeholder="Custom input" />
			<button onClick={handleFocus}>Focus Custom Input</button>
		</div>
	)
}

export default ParentComponent
```

> [!NOTE] `forwardRef` is necessary because refs are not passed as regular props. Without it, the ref would be undefined in the child component.

# Practical Example: Auto-Scroll Chat

Here's a practical example that combines multiple concepts - using `useRef` to auto-scroll a chat window:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
import { useState, useRef, useEffect } from 'react'

const Chat = () => {
	const [messages, setMessages] = useState(['Hello!', 'How are you?'])
	const [input, setInput] = useState('')
	const messagesEndRef = useRef(null)

	const scrollToBottom = () => {
		messagesEndRef.current?.scrollIntoView({ behavior: 'smooth' })
	}

	useEffect(() => {
		scrollToBottom()
	}, [messages])

	const handleSend = (e) => {
		e.preventDefault()
		if (input.trim()) {
			setMessages([...messages, input])
			setInput('')
		}
	}

	return (
		<div>
			<div style={{ height: '300px', overflowY: 'scroll', border: '1px solid #ccc', padding: '10px' }}>
				{messages.map((msg, index) => (
					<div key={index} style={{ marginBottom: '8px' }}>
						{msg}
					</div>
				))}
				<div ref={messagesEndRef} />
			</div>
			<form onSubmit={handleSend}>
				<input
					type="text"
					value={input}
					onChange={(e) => setInput(e.target.value)}
					placeholder="Type a message..."
				/>
				<button type="submit">Send</button>
			</form>
		</div>
	)
}

export default Chat
```

> [!TIP] The `?.` optional chaining operator prevents errors if the ref isn't attached yet. This is good practice when calling methods on refs.

# Best Practices

1. **Don't overuse refs** - Prefer declarative React patterns with state and props
2. **Clean up side effects** - Always clear timers and intervals stored in refs
3. **Use refs for imperative actions** - Focus, scroll, animations, third-party libraries
4. **Avoid reading/writing refs during render** - Do this in event handlers or useEffect instead
5. **Initialize refs properly** - Start with `null` for DOM refs or an appropriate initial value for data refs

> [!CAUTION] Modifying refs during render can lead to inconsistent behavior. Always update refs in event handlers or useEffect callbacks, not during the render phase.
