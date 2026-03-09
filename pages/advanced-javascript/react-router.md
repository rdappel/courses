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
		<iframe src="https://www.youtube.com/embed/aWnDd8CFVE4" width="100%" height="100%" frameborder="0"
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

const App = () => {
	return (
		<Routes>
			<Route path="/" element={<h1>Home</h1>} />
			<Route path="/about" element={<h1>About</h1>} />
			<Route path="/contact" element={<h1>Contact</h1>} />
		</Routes>
	)
}

export default App
```

# Page Components

Next, we will create separate components for each page instead of inline elements:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/IcKOuh6er_A" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code for the Home page. I will omit the About and Contact pages since they are similar:

```javascript
// pages/Home.jsx
const Home = () => (
	<div>
		<h1>Home</h1>
		<p>This is the Home page.</p>
	</div>
)

export default Home
```

Now import the page components in your App and use them in the routes:

```javascript
import { Routes, Route } from 'react-router-dom'
import Home from './pages/Home.jsx'
import About from './pages/About.jsx'
import Contact from './pages/Contact.jsx'

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

Now when you navigate to `/`, `/about` or `/contact`, React Router will render the corresponding component.

# Navigation with Link

Use the `Link` component to navigate between pages without full page reloads:

```javascript
import { Link } from 'react-router-dom'

const Nav = () => {
	return (
		<nav>
			<Link to="/">Home</Link>
			<Link to="/about">About</Link>
			<Link to="/contact">Contact</Link>
		</nav>
	)
}

export default Nav
```

> [!NOTE] Use `Link` instead of `<a>` tags. The `Link` component prevents full page reloads and uses client-side routing instead.

# Layouts with Outlet

Layouts let you create a shared structure (like headers and footers) that wraps around your pages. React Router provides the `Outlet` component for this purpose.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/LFpNqjQsAIw" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Create a layout component:

```javascript
// layouts/MainLayout.jsx
import { Outlet } from 'react-router-dom'
import Nav from '../components/Nav.jsx'
import Footer from '../components/Footer.jsx'

const MainLayout = () => (
	<div>
		<h1>Ryan's homepage</h1>
		<Nav />
		<Outlet />
		<Footer />
	</div>
)

export default MainLayout
```

In our App:

```javascript
// import MainLayout
import MainLayout from './layouts/MainLayout.jsx'

// Wrap routes with the layout
<Routes>
	<Route path="/" element={<MainLayout />}>
		<Route index element={<Home />} />
		<Route path="about" element={<About />} />
		<Route path="contact" element={<Contact />} />
	</Route>
</Routes>
```

Here is the code for the footer component:

```javascript
// components/Footer.jsx
const Footer = () => (
	<footer>
		<p>&copy; 2024 My SPA. All rights reserved.</p>
	</footer>
)
```

> [!NOTE] The `<Outlet />` component renders the child route's element. When you visit `/about`, the Layout renders with the About component appearing where the Outlet is.

## Index Routes

Notice the `index` prop on the home route. This tells React Router to render that element when the parent route path is matched exactly:

```javascript
<Route path="/" element={<Layout />}>
	<Route index element={<Home />} />
	<Route path="about" element={<About />} />
	<Route path="contact" element={<Contact />} />
</Route>
```

## Multiple Layouts

You can have different layouts for different sections of your app:

```javascript
const App = () => {
	return (
		<Routes>
			{/* Public pages with main layout */}
			<Route path="/" element={<Layout />}>
				<Route index element={<Home />} />
				<Route path="about" element={<About />} />
				<Route path="contact" element={<Contact />} />
			</Route>
			
			{/* Dashboard with different layout */}
			<Route path="/dashboard" element={<DashboardLayout />}>
				<Route index element={<DashboardHome />} />
				<Route path="settings" element={<Settings />} />
				<Route path="profile" element={<Profile />} />
			</Route>
		</Routes>
	)
}
```

# Active Link Styling with NavLink

`NavLink` is like `Link`, but it adds an `active` class to the current link:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/PZ1u_2be0qg" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the updated Nav component and CSS:

```javascript
import { NavLink } from 'react-router-dom'

import './Nav.css'

const Nav = () => (
	<nav>
		<NavLink to="/">Home</NavLink>
		<NavLink to="/about">About</NavLink>
		<NavLink to="/contact">Contact</NavLink>
	</nav>
)

export default Nav
```

Then style the active link in your CSS:

```css
/* components/Nav.css */
nav a {
	color: blue;
	text-decoration: none;
	margin: 0 10px;
}

nav a.active {
	color: red;
	text-decoration: underline;
}
```

# URL Parameters

URL parameters let you pass data through the URL:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/QTFWgAWHbaI" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Define a route with parameters:

```javascript
// App.jsx
import UserProfile from './pages/UserProfile'

<Route path="/user-profile/:id" element={<UserProfile />} />
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
<Link to="/user-profile/123">View User 123</Link>
<Link to="/user-profile/456">View User 456</Link>
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
		<iframe src="https://www.youtube.com/embed/M56Lshc4CDg" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Use the `useNavigate` hook:

```javascript
import { useNavigate } from 'react-router-dom'

const Contact = () => {
	const navigate = useNavigate()

	const handleSubmit = e => {
		e.preventDefault()
		navigate('/dashboard')
	}

	return (
		<div>
			<h1>Contact</h1>
			<form onSubmit={handleSubmit}>
				<input type="email" placeholder="Your email" />
				<textarea placeholder="Your message"></textarea>
				<button type="submit">Send</button>
			</form>
		</div>
	)
}

export default Contact
```

You can also navigate with options:

```javascript
// Navigate to Contact page
navigate('/contact')

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
		<iframe src="https://www.youtube.com/embed/4E6Qkta7MgE" width="100%" height="100%" frameborder="0"
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

const NotFound = () => (
	<div>
		<h1>Not Found</h1>
		<p>The page you are looking for does not exist.</p>
		<Link to="/">Go back to Home</Link>
	</div>
)

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
