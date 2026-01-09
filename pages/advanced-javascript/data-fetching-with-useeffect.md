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

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/bNCUjYzOSIQ" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the url to `users.json` that we used as a mock API in the video: 

```plaintext
https://raw.githubusercontent.com/rdappel/courses/master/support-files/ajs/users.json
```

Here is a link to the code-snippet that I created in the video:

[Code snippet for Basic React Component](https://gist.github.com/rdappel/a0e3fb75061ed55fceda4a0b42b58ae8).

And here is the UserList component code:

```javascript
import { useState, useEffect } from 'react'

const UserList = () => {
	const [ users, setUsers ] = useState([])

	useEffect(() => {
		(async () => {
			const url = 'https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/ajs/users.json'
			const response = await fetch(url)
			const data = await response.json()
			setUsers(data)
		})()
	}, [])

	return (
		<div>
			<h2>Users</h2>
			<ul>
				{users.map(({ id, name, role }) => {
					return <li key={id}>{name} - {role}</li>
				})}
			</ul>
		</div>
	)
}

export default UserList
```

<div class="centering">
    <img src="https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/ajs/data-fetch-dark.svg" alt="" aria-hidden="true" class="adaptive dark">
    <img src="https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/ajs/data-fetch-light.svg" alt="" aria-hidden="true" class="adaptive light">
</div>

## Adding Loading States

Users should know when data is being fetched. Let's add a loading indicator:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/99PUJ5PaD-E" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
import { useState, useEffect } from 'react'

const UserList = () => {
	const [users, setUsers] = useState([])
	const [ isLoading, setIsLoading ] = useState(true)

	useEffect(() => {
		(async () => {
			const response = await fetch('/support-files/ajs/users.json')
			const data = await response.json()
			setUsers(data)
			setIsLoading(false)
		})()
	}, [])

	if (isLoading) return <div>Loading users...</div>

	return (
		<div>
			<h2>Users</h2>
			<ul>
				{users.map(({ id, name, role }) => {
					return <li key={id}>{name} - {role}</li>
				})}
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
		<iframe src="https://www.youtube.com/embed/5jl6uGAY_rM" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
import { useState, useEffect } from 'react'

const UserList = () => {
	const [users, setUsers] = useState([])
	const [isLoading, setIsLoading] = useState(true)
	const [error, setError] = useState(null)

	useEffect(() => {
		(async () => {
			try {
				const response = await fetch('/support-files/ajs/users.json')
				const data = await response.json()
				setUsers(data)
			} catch (err) {
				setError(err.message)
			} finally {
				setIsLoading(false)
			}
		})()
	}, [])

	if (isLoading) return <div>Loading users...</div>
	if (error) return <div>Error: {error}</div>

	return (
		<div>
			<h2>Users</h2>
			<ul>
				{users.map(({ id, name, role }) => {
					return <li key={id}>{name} - {role}</li>
				})}
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
		<iframe src="https://www.youtube.com/embed/uBQjqXVCXWg" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

First, let's create the Card component:

```javascript
const Card = ({ user }) => {
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

export default Card
```

Now, let's use it in our UserList component:

```javascript
import { useState, useEffect } from 'react'
import Card from './Card.jsx'

const UserList = () => {
	const [ users, setUsers ] = useState([])
	const [ isLoading, setIsLoading ] = useState(true)
	const [ error, setError ] = useState(null)

	useEffect(() => {
		(async () => {
			try {
				const url = 'https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/ajs/users.json'
				const response = await fetch(url)
				if (!response.ok) throw new Error('Failed to fetch users')
				const data = await response.json()
				setUsers(data)
			}
			catch (err) {
				setError(err.message)
			}
			finally {
				setIsLoading(false)
			}
		})()
	}, [])

	if (isLoading) return <div>Loading users...</div>
	if (error) return <div>Error: {error}</div>

	return (
		<div>
			<h2>Users</h2>
			<ul>
				{users.map(user => (
					<Card key={user.id} user={user} />
				))}
			</ul>
		</div>
	)
}

export default UserList
```