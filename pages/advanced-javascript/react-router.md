---
title: React Router
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/react-router
dev: http://localhost:3006/appel/advanced-javascript/react-router
repo: https://github.com/rdappel/courses
---

# What is React Router?

React Router is the standard library for routing in React applications. It enables navigation between different views or pages in a single-page application (SPA) without full page reloads.

With React Router, you can:

- Create multiple pages in your React app
- Navigate between pages without page refreshes
- Use URL parameters to pass data
- Handle 404 pages
- Navigate programmatically after user actions

> [!NOTE] React Router keeps the URL in sync with what the user sees. When you click a link, the URL changes and React Router renders the appropriate component - all without reloading the page.

# Installing React Router

First, install React Router in your project:

```bash
npm install react-router-dom
```

> [!IMPORTANT] Make sure to install `react-router-dom`, not just `react-router`. The `-dom` version is specifically designed for web applications.

# Basic Setup

Let's create a simple multi-page application with a home page, about page, and contact page:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

First, wrap your app with `BrowserRouter`:

```javascript
// main.jsx
import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'
import { BrowserRouter } from 'react-router-dom'
import App from './App.jsx'

createRoot(document.getElementById('root')).render(
	<StrictMode>
		<BrowserRouter>
			<App />
		</BrowserRouter>
	</StrictMode>
)
```

Now create routes in your App component:

```javascript
// App.jsx
import { Routes, Route } from 'react-router-dom'
import Home from './pages/Home'
import About from './pages/About'
import Contact from './pages/Contact'

const App = () => {
	return (
		<Routes>
			<Route path="/" element={<Home />} />
			<Route path="/about" element={<About />} />
			<Route path="/contact" element={<Contact />} />
		</Routes>
	)
}

export default App
```

Create the page components:

```javascript
// pages/Home.jsx
const Home = () => {
	return (
		<div>
			<h1>Home Page</h1>
			<p>Welcome to our website!</p>
		</div>
	)
}

export default Home
```

Now when you navigate to `/about` or `/contact`, React Router will render the corresponding component.

# Navigation with Link

Use the `Link` component to navigate between pages without full page reloads:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
import { Link } from 'react-router-dom'

const Navigation = () => {
	return (
		<nav>
			<Link to="/">Home</Link>
			<Link to="/about">About</Link>
			<Link to="/contact">Contact</Link>
		</nav>
	)
}

export default Navigation
```

Add the navigation to your App:

```javascript
import { Routes, Route } from 'react-router-dom'
import Navigation from './components/Navigation'
import Home from './pages/Home'
import About from './pages/About'
import Contact from './pages/Contact'

const App = () => {
	return (
		<div>
			<Navigation />
			<Routes>
				<Route path="/" element={<Home />} />
				<Route path="/about" element={<About />} />
				<Route path="/contact" element={<Contact />} />
			</Routes>
		</div>
	)
}

export default App
```

> [!NOTE] Use `Link` instead of `<a>` tags. The `Link` component prevents full page reloads and uses client-side routing instead.

# Active Link Styling with NavLink

`NavLink` is like `Link`, but it adds an `active` class to the current link:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
import { NavLink } from 'react-router-dom'
import './Navigation.css'

const Navigation = () => {
	return (
		<nav>
			<NavLink to="/">Home</NavLink>
			<NavLink to="/about">About</NavLink>
			<NavLink to="/contact">Contact</NavLink>
		</nav>
	)
}

export default Navigation
```

Then style the active link in your CSS:

```css
/* Navigation.css */
nav a {
	margin: 0 10px;
	color: #333;
	text-decoration: none;
}

nav a.active {
	color: #007bff;
	font-weight: bold;
	border-bottom: 2px solid #007bff;
}
```

# URL Parameters

URL parameters let you pass data through the URL:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Define a route with parameters:

```javascript
// App.jsx
import UserProfile from './pages/UserProfile'

<Route path="/user/:id" element={<UserProfile />} />
```

Access parameters with `useParams`:

```javascript
// pages/UserProfile.jsx
import { useParams } from 'react-router-dom'

const UserProfile = () => {
	const { id } = useParams()

	return (
		<div>
			<h1>User Profile</h1>
			<p>User ID: {id}</p>
		</div>
	)
}

export default UserProfile
```

Link to routes with parameters:

```javascript
<Link to="/user/123">View User 123</Link>
<Link to="/user/456">View User 456</Link>
```

## Multiple Parameters

You can have multiple parameters in one route:

```javascript
<Route path="/post/:category/:postId" element={<Post />} />
```

```javascript
const Post = () => {
	const { category, postId } = useParams()

	return (
		<div>
			<p>Category: {category}</p>
			<p>Post ID: {postId}</p>
		</div>
	)
}
```

# Programmatic Navigation

Sometimes you need to navigate programmatically (after form submission, authentication, etc.):

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Use the `useNavigate` hook:

```javascript
import { useNavigate } from 'react-router-dom'

const LoginForm = () => {
	const navigate = useNavigate()

	const handleSubmit = (e) => {
		e.preventDefault()
		// Perform login logic...
		
		// Navigate to dashboard after successful login
		navigate('/dashboard')
	}

	return (
		<form onSubmit={handleSubmit}>
			<input type="email" placeholder="Email" />
			<input type="password" placeholder="Password" />
			<button type="submit">Login</button>
		</form>
	)
}

export default LoginForm
```

You can also navigate with options:

```javascript
// Navigate and replace current entry in history
navigate('/home', { replace: true })

// Navigate backwards
navigate(-1)

// Navigate forward
navigate(1)

// Navigate back 2 pages
navigate(-2)
```

# 404 Not Found Pages

Handle routes that don't exist with a catch-all route:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
import NotFound from './pages/NotFound'

const App = () => {
	return (
		<Routes>
			<Route path="/" element={<Home />} />
			<Route path="/about" element={<About />} />
			<Route path="/contact" element={<Contact />} />
			
			{/* Catch-all route for 404 */}
			<Route path="*" element={<NotFound />} />
		</Routes>
	)
}
```

Create a 404 page:

```javascript
// pages/NotFound.jsx
import { Link } from 'react-router-dom'

const NotFound = () => {
	return (
		<div>
			<h1>404 - Page Not Found</h1>
			<p>The page you're looking for doesn't exist.</p>
			<Link to="/">Go back to home</Link>
		</div>
	)
}

export default NotFound
```

> [!IMPORTANT] The `*` route must come last in your Routes. It matches any path that hasn't been matched by previous routes.

# Key Takeaways

- React Router enables client-side routing without page reloads
- Wrap your app with `BrowserRouter` to enable routing
- Use `Routes` and `Route` to define your application's routes
- Use `Link` and `NavLink` for navigation instead of `<a>` tags
- `NavLink` automatically adds an `active` class for styling the current page
- `useParams` extracts URL parameters from the route
- `useNavigate` enables programmatic navigation (redirects, back/forward)
- Handle 404s with a catch-all `*` route
