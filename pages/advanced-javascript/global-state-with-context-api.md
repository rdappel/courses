---
title: Global State with Context API
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/global-state-with-context-api
dev: http://localhost:3006/appel/advanced-javascript/global-state-with-context-api
repo: https://github.com/rdappel/courses
---

# What is the Context API?

The Context API is a React feature that allows you to share state between components without having to pass props down through every level of your component tree. This is often called "prop drilling" - passing props through intermediate components that don't need them.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Context API is ideal for managing global state such as:

- User authentication information
- User preferences (theme, language, etc.)
- Application settings
- Global UI state (modals, notifications)
- User profile data

# The Problem: Prop Drilling

Before we look at Context API, let's understand the problem it solves. Imagine you have a deeply nested component tree where a parent component has data that a deeply nested child needs.

With props, you'd have to pass the data through every component in between:

```javascript
// file: App.jsx

const App = () => {
	const [user, setUser] = useState({ name: 'John' })
	
	return <Layout user={user} setUser={setUser} />
}

// file: components/Layout.jsx
const Layout = ({ user, setUser }) => {
	return <Sidebar user={user} setUser={setUser} />
}

// file: components/Sidebar.jsx
const Sidebar = ({ user, setUser }) => {
	return <UserProfile user={user} setUser={setUser} />
}

// file: components/UserProfile.jsx
const UserProfile = ({ user, setUser }) => {
	return <h1>Hello, {user.name}!</h1>
}
```

This works, but it's tedious and makes the code harder to maintain. This is called "prop drilling."

# Follow Along: Context API Demo Site

To get hands-on experience with the Context API, you should follow along with a demo site built for this lesson. Please do the following:

1. **Fork the Repository**
	- Go to [https://github.com/fvtc/ajs-context-api-demo](https://github.com/fvtc/ajs-context-api-demo) and click the **Fork** button in the top right to create your own copy of the repository.

2. **Clone Your Fork**
	- On your forked repository page, click the **Code** button and copy the URL.
	- Open your terminal and run:

	  ```bash
	  git clone [your-fork-url]
	  ```

	- Replace `[your-fork-url]` with the URL you copied from your fork.

3. **Open the Project**
	- Navigate into the cloned folder:

	  ```bash
	  cd ajs-context-api-demo
	  ```

	- Open the project in VS Code or your preferred editor.

4. **Install Dependencies**
	- Run:

	  ```bash
	  npm install
	  ```

5. **Start the Development Server**
	- Run:

	  ```bash
	  npm run dev
	  ```

# Creating a Context

To use Context API, we first need to create a context using `React.createContext()`.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/o-pk15GkUjE" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Let's create a UserContext:

```javascript
// file: contexts/UserContext.js

import { createContext } from 'react'

export const UserContext = createContext()
```

This creates a context object that we can use to share data. The `createContext()` function takes an optional default value as an argument.

# Context Providers

A provider is a component that supplies the context value to its children. Any component inside the provider can access the context value.

Here's an example of a UserProvider component:

```javascript
// file: contexts/UserProvider.jsx

import { useState } from 'react'
import { UserContext } from './UserContext'

export const UserProvider = ({ children }) => {
	const [user, setUser] = useState({ name: 'Ryan' })

	return (
		<UserContext.Provider value={{ user, setUser }}>
			{children}
		</UserContext.Provider>
	)
}
```

Now wrap your App with the UserProvider:

```javascript
// file: main.jsx

import { UserProvider } from './contexts/UserProvider'
import App from './App'

export default function Root() {
	return (
		<UserProvider>
			<App />
		</UserProvider>
	)
}
```

## Combining Context and Provider

> [!CAUTION]  In the videos, I did end up combing the context and provider into a single file. However, I accidentally moved them into `UserProvider.jsx` instead of `UserContext.jsx`. Both approaches do work, but it did lead to some confusion. I would recommend calling the file `____Context.jsx` if you combine them. I.e., `UserContext.jsx`, `ThemeContext.jsx`, etc...

In the examples above, we created the context and provider as separate files for clarity. However, it's very common (and perfectly fine) to combine them in a single file:

```javascript
// file: contexts/UserContext.jsx

import { createContext, useState } from 'react'

export const UserContext = createContext()

export const UserProvider = ({ children }) => {
	const [user, setUser] = useState({ name: 'Ryan' })

	return (
		<UserContext.Provider value={{ user, setUser }}>
			{children}
		</UserContext.Provider>
	)
}
```

This approach keeps related code together and is easier to maintain. You can then import both from the same file:

```javascript
// file: main.jsx

import { UserProvider } from './contexts/UserContext'

export default function Root() {
	return (
		<UserProvider>
			<App />
		</UserProvider>
	)
}
```

Choose whichever approach feels cleaner to you. Both are valid patterns.

# Using Context with useContext

To access context values in a component, use the `useContext` hook.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/Pq9y7YhiRkw" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here's how to use context in a component:

```javascript
// file: components/UserProfile.jsx

import { useContext } from 'react'
import { UserContext } from '../contexts/UserProvider.jsx'

const UserProfile = () => {
	const { user, setUser } = useContext(UserContext)

	const updateName = newName => {
		setUser({ ...user, name: newName })
	}

	return (
		<div className="user-profile">
			<div className="avatar">{user.name[0]}</div>
			<h3>Hello, {user.name}!</h3>
			<button onClick={() => updateName('Jane')}>
				Change Name
			</button>
		</div>
	)
}

export default UserProfile
```

Now you can use `UserProfile` anywhere in your app without prop drilling:

```javascript
// file: App.jsx

const App = () => {
	return (
		<div>
			<Sidebar />
			<UserProfile />
		</div>
	)
}
```

The `UserProfile` component gets access to `user` and `setUser` directly from context, without needing them passed down as props.

# Multiple Contexts

Your app can have multiple contexts for different types of global state.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/OQsfGwVNJsw" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

For example, you might have a UserContext and a ThemeContext:

```javascript
// file: contexts/ThemeContext.js

import { createContext, useState } from 'react'

export const ThemeContext = createContext()

export const ThemeProvider = ({ children }) => {
	const [theme, setTheme] = useState('light')

	return (
		<ThemeContext.Provider value={{ theme, setTheme }}>
			{children}
		</ThemeContext.Provider>
	)
}

// file: main.jsx
import Root from './Root'
import { UserProvider } from './contexts/UserProvider'
import { ThemeProvider } from './contexts/ThemeProvider'

ReactDOM.createRoot(document.getElementById('root')).render(
	<UserProvider>
		<ThemeProvider>
			<Root />
		</ThemeProvider>
	</UserProvider>
)
```

# Context vs Props

Use context when:

- Data is needed by many components at different nesting levels
- Data is global or semi-global (themes, user info, authentication)
- You want to avoid prop drilling

Use props when:

- Data is only needed by a component and its direct children
- You want explicit data flow that's easy to trace
- Components should be reusable with different data

# Exercise 1

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Below is a copy/paste-ready single-file context + provider for notifications.

For this exercise, paste this file into `contexts/NotificationContext.jsx`, then update your app to use the context from your components (e.g., a `NotificationList` and a `NewNotification` component).

The exercise is to wire the components to the provided context.

```javascript
// contexts/NotificationContext.jsx
import { createContext, useState } from 'react'

export const NotificationContext = createContext()

export const NotificationProvider = ({ children }) => {
  const [notifications, setNotifications] = useState([])

  const addNotification = (message) => {
	const newNote = { id: Date.now(), message }
	setNotifications(prev => [...prev, newNote])
  }

  const removeNotification = id => {
	setNotifications(prev => prev.filter(n => n.id !== id))
  }

  return (
	<NotificationContext.Provider value={{ notifications, addNotification, removeNotification }}>
	  {children}
	</NotificationContext.Provider>
  )
}
```

Feel free to use this code to render the notifications:

```javascript
{notifications.map(n => (
	<div key={n.id} style={{ display: 'flex', gap: 8, alignItems: 'center' }}>
		<span>{n.message}</span>
		<button>Dismiss</button>
	</div>
))}
```

> [!NOTE] You will need to handle the `onClick` for the Dismiss button.


## Task

1. Paste the above file into `contexts/NotificationContext.jsx` in your project.
2. Wrap your application with `NotificationProvider`.
3. Build two small components that use the context:
   - `NotificationList` — reads `notifications` and renders them with a dismiss button that calls `removeNotification(id)`.
   - `NewNotification` — input + button that calls `addNotification(message)`.

## Hints

- Use `const { notifications, removeNotification } = useContext(NotificationContext)` in `NotificationList`.
- Use `const { addNotification } = useContext(NotificationContext)` in `NewNotification` and clear the input after adding.

## Solution {#exercise-1-solution}

<details>
	<summary>Show the Answer</summary>

```javascript
// components/NotificationList.jsx
import { useContext } from 'react'
import { NotificationContext } from '../contexts/NotificationContext'

const NotificationList = () => {
	const { notifications, removeNotification } = useContext(NotificationContext)

	if (!notifications.length) return <div>No notifications</div>

	return (
		<div>
			<h3>Notifications</h3>
			{notifications.map(({ id, message }) => (
				<div key={id} style={{ display: 'flex', gap: 8, alignItems: 'center' }}>
					<span>{message}</span>
					<button
						onClick={() => removeNotification(n.id)}
					>Dismiss</button>
				</div>
			))}
		</div>
	)
}

export default NotificationList
```

```javascript
// components/NewNotification.jsx
import { useState, useContext } from 'react'
import { NotificationContext } from '../contexts/NotificationContext'

const NewNotification = () => {
	const [text, setText] = useState('')
	const { addNotification } = useContext(NotificationContext)

	const submit = () => {
		if (!text) return
		addNotification(text)
		setText('')
	}

	return (
		<div>
			<input
				value={text}
				onChange={e => setText(e.target.value)}
				placeholder="Notification message"
			/>
			<button onClick={submit}>Add</button>
		</div>
	)
}

export default NewNotification
```

```javascript
// remember to wrap your layout/app with the provider
import { NotificationProvider } from './contexts/NotificationContext'
<NotificationProvider>
	<Layout /> {/* or <App /> */}
</NotificationProvider>

// somewhere in your app render the components
import NewNotification from './components/NewNotification'
import NotificationList from './components/NotificationList'
<NewNotification />
<NotificationList />
```

</details>

## Walkthrough Video

<details>
	<summary>Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0" allowfullscreen></iframe>
	</div>
</details>

# Performance Considerations

Context is convenient but has performance implications:

- When context value changes, ALL components using that context re-render
- If your context changes frequently, it can cause unnecessary re-renders

To optimize, split contexts by update frequency:

```javascript
// file: contexts/index.js
// Separate contexts for less frequent updates
export const UserInfoContext = createContext()  // Changes rarely
export const UserPrefsContext = createContext() // Changes more often

// Use them separately so changes don't trigger unnecessary re-renders
```

# Common Use Cases

## Theme Switcher

```javascript
// file: components/ThemeToggle.jsx

import { useContext } from 'react'
import { ThemeContext } from '../contexts/ThemeContext'

const ThemeToggle = () => {
	const { theme, setTheme } = useContext(ThemeContext)

	return (
		<button onClick={() => setTheme(theme === 'light' ? 'dark' : 'light')}>
			Current theme: {theme}
		</button>
	)
}
```

## Authentication

```javascript
// file: components/LoginButton.jsx
import { useContext } from 'react'
import { AuthContext } from '../contexts/AuthContext'

const LoginButton = () => {
	const { user, login, logout } = useContext(AuthContext)

	return (
		<div>
			{user ? (
				<button onClick={logout}>Logout {user.name}</button>
			) : (
				<button onClick={login}>Login</button>
			)}
		</div>
	)
}
```

## Language/Localization

```javascript
// file: components/LanguageSwitcher.jsx
import { useContext } from 'react'
import { LanguageContext } from '../contexts/LanguageContext'

const LanguageSwitcher = () => {
	const { language, setLanguage } = useContext(LanguageContext)

	return (
		<select value={language} onChange={(e) => setLanguage(e.target.value)}>
			<option value="en">English</option>
			<option value="es">Español</option>
			<option value="fr">Français</option>
		</select>
	)
}
```
