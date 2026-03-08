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
		<iframe src="https://www.youtube.com/embed/fDSI1BNxzH0" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## The Problem: Expensive Calculations on Every Render

```javascript
const App = () => {
	const [searchTerm, setSearchTerm] = useState('')
	const [cartCount, setCartCount] = useState(0)

	// This calculation runs on every render, even if searchTerm hasn't changed
	const filteredProducts = filterProducts(products, searchTerm)

	// etc...
}
```

**The Problem**: The `filterProducts` function is called on every render, even if `searchTerm` hasn't changed. If `filterProducts` is expensive (e.g., it loops through a large list), this can cause performance issues.

## The Solution: useMemo

`useMemo` returns a memoized value that only recalculates when dependencies change:

```javascript
const App = () => {
	const [searchTerm, setSearchTerm] = useState('')
	const [cartCount, setCartCount] = useState(0)

	// This calculation only runs when searchTerm changes
	const filteredProducts = useMemo(() => filterProducts(products, searchTerm), [searchTerm])

	// etc...
}
```

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

In this video I will extract the filtering logic into a custom hook and use `useMemo` inside it:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/f5uACqn4998" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
// hooks/useFilteredProducts.js
import { useMemo } from 'react'
import filterProducts from '../utils/filterProducts'

function useFilteredProducts(products, searchTerm) {
	return useMemo(() => filterProducts(products, searchTerm),
		[products, searchTerm]
	)
}

export default useFilteredProducts

// Usage
import useFilteredProducts from './hooks/useFilteredProducts'

// In your component:
const filteredProducts = useFilteredProducts(products, searchTerm) // useMemo is used inside the hook
```

> [!NOTE] The completed source code for this app is available here: [useMemo Example](https://github.com/rdappel/ajs-usememo-example).

# Key Takeaways

- `useMemo` caches expensive calculation results to avoid recalculation
- Only use it when you have actual performance problems
- Memoization adds complexity and memory overhead
- Measure before and after optimizing
- Best for expensive computations with stable dependencies
