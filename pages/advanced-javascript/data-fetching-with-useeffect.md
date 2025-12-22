---
title: Data Fetching with useEffect
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/data-fetching-with-useeffect
dev: http://localhost:3006/appel/advanced-javascript/data-fetching-with-useeffect
repo: https://github.com/rdappel/courses
---

# Fetching Data in React

One of the most common use cases for `useEffect` is fetching data from an API. In this lesson, we'll learn how to fetch data, handle loading states, and manage errors properly.

## Basic Data Fetching

Let's start with a simple example that fetches user data when the component mounts:

<div class="centering">
    <img src="https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/ajs/data-fetch-dark.svg" alt="" aria-hidden="true" class="adaptive dark">
    <img src="https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/ajs/data-fetch-light.svg" alt="" aria-hidden="true" class="adaptive light">
</div>

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

const UserList = () => {
	const [users, setUsers] = useState([])

	useEffect(() => {
		(async () => {
			const response = await fetch('/support-files/ajs/users.json')
			const data = await response.json()
			setUsers(data)
		})()
	}, [])

	return (
		<div>
			<h2>Users</h2>
			<ul>
				{users.map(user => (
					<li key={user.id}>{user.name} - {user.role}</li>
				))}
			</ul>
		</div>
	)
}

export default UserList
```

> [!NOTE] The empty dependency array `[]` ensures the fetch only happens once when the component mounts, not on every render.

## Adding Loading States

Users should know when data is being fetched. Let's add a loading indicator:

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

const UserList = () => {
	const [users, setUsers] = useState([])
	const [loading, setLoading] = useState(true)

	useEffect(() => {
		(async () => {
			const response = await fetch('/support-files/ajs/users.json')
			const data = await response.json()
			setUsers(data)
			setLoading(false)
		})()
	}, [])

	if (loading) {
		return <div>Loading users...</div>
	}

	return (
		<div>
			<h2>Users</h2>
			<ul>
				{users.map(user => (
					<li key={user.id}>
						{user.name} - {user.role}
					</li>
				))}
			</ul>
		</div>
	)
}

export default UserList
```

## Error Handling

Network requests can fail, so we need to handle errors gracefully:

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

const UserList = () => {
	const [users, setUsers] = useState([])
	const [loading, setLoading] = useState(true)
	const [error, setError] = useState(null)

	useEffect(() => {
		(async () => {
			try {
				const response = await fetch('/support-files/ajs/users.json')
				if (!response.ok) throw new Error('Failed to fetch users')
				const data = await response.json()
				setUsers(data)
			} catch (err) {
				setError(err.message)
			} finally {
				setLoading(false)
			}
		})()
	}, [])

	if (loading) return <div>Loading users...</div>
	if (error) return <div>Error: {error}</div>

	return (
		<div>
			<h2>Users</h2>
			<ul>
				{users.map(user => (
					<li key={user.id}>
						{user.name} - {user.role}
					</li>
				))}
			</ul>
		</div>
	)
}

export default UserList
```

> [!IMPORTANT] Always handle both the loading and error states. This provides a better user experience and helps with debugging.

> [!NOTE] We're using an async IIFE (Immediately Invoked Function Expression) inside the useEffect because the useEffect callback itself cannot be async. The `finally` block ensures loading is set to false whether the request succeeds or fails.

## Building a User Card Component

Let's create a more polished component that displays user information in cards:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

First, let's create the UserCard component:

```javascript
const UserCard = ({ user }) => {
	const cardStyle = {
		border: '1px solid #ddd',
		borderRadius: '8px',
		padding: '16px',
		margin: '8px',
		display: 'flex',
		alignItems: 'center',
		gap: '16px',
		backgroundColor: '#f9f9f9'
	}

	const avatarStyle = {
		width: '60px',
		height: '60px',
		borderRadius: '50%'
	}

	return (
		<div style={cardStyle}>
			<img src={user.avatar} alt={user.name} style={avatarStyle} />
			<div>
				<h3 style={{ margin: '0 0 4px 0' }}>{user.name}</h3>
				<p style={{ margin: '0', color: '#666' }}>{user.role}</p>
				<p style={{ margin: '4px 0 0 0', fontSize: '14px' }}>{user.email}</p>
			</div>
		</div>
	)
}

export default UserCard
```

Now, let's use it in our UserList component:

```javascript
import { useState, useEffect } from 'react'
import UserCard from './UserCard'

const UserList = () => {
	const [users, setUsers] = useState([])
	const [loading, setLoading] = useState(true)
	const [error, setError] = useState(null)

	useEffect(() => {
		const fetchUsers = async () => {
			try {
				const response = await fetch('/support-files/ajs/users.json')
				if (!response.ok) {
					throw new Error('Failed to fetch users')
				}
				const data = await response.json()
				setUsers(data)
			} catch (err) {
				setError(err.message)
			} finally {
				setLoading(false)
			}
		}

		fetchUsers()
	}, [])

	if (loading) return <div>Loading users...</div>
	if (error) return <div>Error: {error}</div>

	return (
		<div>
			<h2>Team Members</h2>
			{users.map(user => (
				<UserCard key={user.id} user={user} />
			))}
		</div>
	)
}

export default UserList
```

> [!TIP] The `finally` block in try/catch is perfect for setting loading to false, as it runs whether the request succeeds or fails.

## Filtering Fetched Data

Let's add filtering capability to our product list:

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

const ProductList = () => {
	const [products, setProducts] = useState([])
	const [loading, setLoading] = useState(true)
	const [error, setError] = useState(null)
	const [filter, setFilter] = useState('all')

	useEffect(() => {
		const fetchProducts = async () => {
			try {
				const response = await fetch('/support-files/ajs/products.json')
				if (!response.ok) throw new Error('Failed to fetch products')
				const data = await response.json()
				setProducts(data)
			} catch (err) {
				setError(err.message)
			} finally {
				setLoading(false)
			}
		}

		fetchProducts()
	}, [])

	if (loading) return <div>Loading products...</div>
	if (error) return <div>Error: {error}</div>

	const filteredProducts = filter === 'all' 
		? products 
		: products.filter(p => p.category === filter)

	return (
		<div>
			<h2>Products</h2>
			<div>
				<button onClick={() => setFilter('all')}>All</button>
				<button onClick={() => setFilter('Electronics')}>Electronics</button>
				<button onClick={() => setFilter('Accessories')}>Accessories</button>
			</div>
			<ul>
				{filteredProducts.map(product => (
					<li key={product.id}>
						{product.name} - ${product.price}
						{!product.inStock && ' (Out of Stock)'}
					</li>
				))}
			</ul>
		</div>
	)
}

export default ProductList
```

## Refetching Data

Sometimes you need to refetch data based on user actions or changing conditions:

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

const RefreshableUserList = () => {
	const [users, setUsers] = useState([])
	const [loading, setLoading] = useState(true)
	const [error, setError] = useState(null)
	const [refreshKey, setRefreshKey] = useState(0)

	useEffect(() => {
		const fetchUsers = async () => {
			setLoading(true)
			setError(null)
			try {
				const response = await fetch('/support-files/ajs/users.json')
				if (!response.ok) throw new Error('Failed to fetch users')
				const data = await response.json()
				setUsers(data)
			} catch (err) {
				setError(err.message)
			} finally {
				setLoading(false)
			}
		}

		fetchUsers()
	}, [refreshKey])

	const handleRefresh = () => {
		setRefreshKey(prev => prev + 1)
	}

	if (loading) return <div>Loading users...</div>
	if (error) return <div>Error: {error}</div>

	return (
		<div>
			<div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center' }}>
				<h2>Team Members</h2>
				<button onClick={handleRefresh}>Refresh</button>
			</div>
			<ul>
				{users.map(user => (
					<li key={user.id}>{user.name} - {user.role}</li>
				))}
			</ul>
		</div>
	)
}

export default RefreshableUserList
```

> [!NOTE] By adding `refreshKey` to the dependency array, we can trigger a refetch by changing its value. This is a common pattern for refreshing data.

# Best Practices for Data Fetching

1. **Always handle loading and error states** - Never assume requests will succeed
2. **Use try/catch with async/await** - This makes error handling cleaner
3. **Set loading to false in finally** - Ensures it updates regardless of success or failure
4. **Check response.ok** - The fetch API doesn't reject on HTTP errors
5. **Keep the dependency array accurate** - Include all values used in the effect
6. **Consider using a data fetching library** - For larger apps, libraries like React Query or SWR can simplify data fetching

> [!TIP] For production applications, consider using a dedicated data fetching library like React Query or SWR. These libraries handle caching, refetching, and state management automatically, reducing boilerplate code significantly.
