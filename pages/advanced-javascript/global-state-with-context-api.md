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
// App.js - has user data
const App = () => {
	const [user, setUser] = useState({ name: 'John' })
	
	return <Layout user={user} setUser={setUser} />
}

// Layout.js - doesn't need user, but passes it down
const Layout = ({ user, setUser }) => {
	return <Sidebar user={user} setUser={setUser} />
}

// Sidebar.js - doesn't need user, but passes it down
const Sidebar = ({ user, setUser }) => {
	return <UserProfile user={user} setUser={setUser} />
}

// UserProfile.js - finally uses user
const UserProfile = ({ user, setUser }) => {
	return <h1>Hello, {user.name}!</h1>
}
```

This works, but it's tedious and makes the code harder to maintain. This is called "prop drilling."

# Creating a Context

To use Context API, we first need to create a context using `React.createContext()`.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Let's create a UserContext:

```javascript
import { createContext } from 'react'

export const UserContext = createContext()
```

This creates a context object that we can use to share data. The `createContext()` function takes an optional default value as an argument.

# Context Providers

A provider is a component that supplies the context value to its children. Any component inside the provider can access the context value.

Here's an example of a UserProvider component:

```javascript
import { useState } from 'react'
import { UserContext } from './UserContext'

export const UserProvider = ({ children }) => {
	const [user, setUser] = useState({ name: 'John' })

	return (
		<UserContext.Provider value={{ user, setUser }}>
			{children}
		</UserContext.Provider>
	)
}
```

Now wrap your App with the UserProvider:

```javascript
import { UserProvider } from './UserProvider'
import App from './App'

export default function Root() {
	return (
		<UserProvider>
			<App />
		</UserProvider>
	)
}
```

# Using Context with useContext

To access context values in a component, use the `useContext` hook.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here's how to use context in a component:

```javascript
import { useContext } from 'react'
import { UserContext } from './UserContext'

const UserProfile = () => {
	const { user, setUser } = useContext(UserContext)

	const updateName = (newName) => {
		setUser({ ...user, name: newName })
	}

	return (
		<div>
			<h1>Hello, {user.name}!</h1>
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
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

For example, you might have a UserContext and a ThemeContext:

```javascript
// ThemeContext.js
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

// main.jsx - Wrap with multiple providers
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

# Performance Considerations

Context is convenient but has performance implications:

- When context value changes, ALL components using that context re-render
- If your context changes frequently, it can cause unnecessary re-renders

To optimize, split contexts by update frequency:

```javascript
// Separate contexts for less frequent updates
export const UserInfoContext = createContext()  // Changes rarely
export const UserPrefsContext = createContext() // Changes more often

// Use them separately so changes don't trigger unnecessary re-renders
```

# Common Use Cases

## Theme Switcher

```javascript
import { useContext } from 'react'
import { ThemeContext } from './ThemeContext'

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
import { useContext } from 'react'
import { AuthContext } from './AuthContext'

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
import { useContext } from 'react'
import { LanguageContext } from './LanguageContext'

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
