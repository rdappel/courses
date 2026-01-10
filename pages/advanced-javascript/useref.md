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

	return (
		<div>
			<input type="text" ref={inputRef} />
			<button onClick={() => inputRef.current.select() }>Focus Input</button>
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

> [!NOTE] In the example above, clicking "Increment Ref" won't update the displayed count until the component re-renders for another reason. This is because changing a ref doesn't trigger a re-render.

**Use useState when:**

- The value should trigger a re-render when it changes
- You need to display the value in the UI
- React needs to track the value for proper rendering

**Use useRef when:**

- You need to store a value that persists between renders but doesn't affect the UI
- You're working with DOM elements directly
- You're storing timers, intervals, or other mutable values

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

const SearchableList = () => {
	const [ searchTerm, setSearchTerm ] = useState('')
	const inputRef = useRef(null)

	const items = [
		'Apple', 'Banana', 'Cherry', 'Date', 'Elderberry',
		'Fig', 'Grape', 'Honeydew', 'Kiwi', 'Lemon'
	]

	const filteredItems = searchTerm.trim() === '' ? items
		: items.filter(item => item.toLowerCase().includes(searchTerm.toLowerCase()))

	return (
		<div>
			<input
				ref={inputRef}
				type="text"
				value={searchTerm}
				onChange={({ target }) => setSearchTerm(target.value)}
				placeholder='Search fruits...'
			/>
			{
				filteredItems.length === 0 ? <div>'No items match search...'</div>
					: (<ul>
						{filteredItems.map((item, index) => <li key={index}>{item}</li>)}
					</ul>)
			}
		</div>
	)
}

export default SearchableList
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

// Custom input component that accepts a ref
const FancyInput = forwardRef((props, ref) => {
	return (
		<input
			ref={ref}
			{...props}
			style={{
				padding: '10px',
				fontSize: '18px',
				border: '2px solid #4CAF50',
				borderRadius: '5px'
			}}
		/>
	)
})

// Parent component
const App = () => {
	const inputRef = useRef(null)

	const handleFocus = () => {
		inputRef.current.focus()
	}

	const handleClear = () => {
		inputRef.current.value = ''
		inputRef.current.focus()
	}

	return (
		<div>
			<FancyInput ref={inputRef} placeholder="Type something..." />
			<button onClick={handleFocus}>Focus</button>
			<button onClick={handleClear}>Clear</button>
		</div>
	)
}

export default App
```

> [!NOTE] `forwardRef` is necessary because refs are not passed as regular props. Without it, the ref would be undefined in the child component.

# Best Practices

1. **Don't overuse refs** - Prefer declarative React patterns with state and props
2. **Clean up side effects** - Always clear timers and intervals stored in refs
3. **Use refs for imperative actions** - Focus, scroll, animations, third-party libraries
4. **Avoid reading/writing refs during render** - Do this in event handlers or useEffect instead
5. **Initialize refs properly** - Start with `null` for DOM refs or an appropriate initial value for data refs

> [!CAUTION] Modifying refs during render can lead to inconsistent behavior. Always update refs in event handlers or useEffect callbacks, not during the render phase.
