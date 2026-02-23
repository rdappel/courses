---
title: Memoization with useMemo
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/memoization
dev: http://localhost:3006/appel/advanced-javascript/memoization
repo: https://github.com/rdappel/courses
---

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

- `useMemo` caches expensive calculation results to avoid recalculation
- Only use it when you have actual performance problems
- Memoization adds complexity and memory overhead
- Measure before and after optimizing
- Best for expensive computations with stable dependencies
