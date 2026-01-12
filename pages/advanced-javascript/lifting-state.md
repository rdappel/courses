---
title: Lifting State & Component Communication
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/lifting-state
dev: http://localhost:3006/appel/advanced-javascript/lifting-state
repo: https://github.com/rdappel/courses
---

# What is Lifting State?

Lifting state is a pattern where you move state from a child component to a parent component so that multiple child components can share and access the same data. This is one of the core concepts in React for managing data flow in your application.

When multiple components need to reflect the same changing data, we lift the shared state up to their closest common ancestor. The parent component becomes the "source of truth" for that data.

<div class="centering">
    <img src="https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/ajs/lifting-state-dark.svg" alt="" aria-hidden="true" class="adaptive dark">
    <img src="https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/ajs/lifting-state-light.svg" alt="" aria-hidden="true" class="adaptive light">
</div>

# Component Communication Patterns

In React, data flows in one direction: from parent to child. There are two main ways components communicate:

**Parent → Child**: Pass data down through props
**Child → Parent**: Pass callback functions down as props, child calls them with data

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Parent to Child Communication

This is the most common pattern - passing data from parent to child via props:

```javascript
// Parent component
const App = () => {
	const userName = "Alex"
	
	return <Greeting name={userName} />
}

// Child component
const Greeting = ({ name }) => {
	return <h1>Hello, {name}!</h1>
}
```

> [!NOTE] This is the pattern you've been using throughout the course - props flow downward from parent to child.

## Child to Parent Communication

When a child needs to send data back to the parent, we pass a callback function as a prop:

```javascript
// Parent component
const App = () => {
	const handleNameChange = (newName) => {
		console.log('Name changed to:', newName)
	}
	
	return <NameInput onNameChange={handleNameChange} />
}

// Child component
const NameInput = ({ onNameChange }) => {
	const [name, setName] = useState('')
	
	const handleSubmit = (e) => {
		e.preventDefault()
		onNameChange(name) // Call parent's function
	}
	
	return (
		<form onSubmit={handleSubmit}>
			<input 
				value={name} 
				onChange={(e) => setName(e.target.value)} 
			/>
			<button type="submit">Submit</button>
		</form>
	)
}
```

> [!IMPORTANT] The child doesn't modify the parent's state directly. Instead, it calls a function that the parent provided, and the parent updates its own state.

# Why Lift State?

Consider a simple example: two components that need to stay in sync. Let's say we have a temperature converter with Celsius and Fahrenheit inputs.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

**Problem**: If each input has its own state, they can't stay synchronized:

```javascript
// ❌ Problem - Each has independent state
const CelsiusInput = () => {
	const [temp, setTemp] = useState('')
	return <input value={temp} onChange={(e) => setTemp(e.target.value)} />
}

const FahrenheitInput = () => {
	const [temp, setTemp] = useState('')
	return <input value={temp} onChange={(e) => setTemp(e.target.value)} />
}
```

**Solution**: Lift the state to a common parent:

```javascript
// ✅ Solution - Shared state in parent
const TemperatureConverter = () => {
	const [celsius, setCelsius] = useState('')
	
	const fahrenheit = celsius ? (celsius * 9/5 + 32).toFixed(1) : ''
	
	return (
		<div>
			<TemperatureInput 
				scale="Celsius"
				temperature={celsius}
				onTemperatureChange={setCelsius}
			/>
			<TemperatureInput 
				scale="Fahrenheit"
				temperature={fahrenheit}
				onTemperatureChange={(f) => setCelsius(((f - 32) * 5/9).toFixed(1))}
			/>
		</div>
	)
}

const TemperatureInput = ({ scale, temperature, onTemperatureChange }) => {
	return (
		<div>
			<label>{scale}:</label>
			<input 
				value={temperature}
				onChange={(e) => onTemperatureChange(e.target.value)}
			/>
		</div>
	)
}
```

# Practical Example: Shopping Cart

Let's build a more realistic example with a shopping cart where multiple components need to access and modify the same data.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
import { useState } from 'react'

// Parent component - holds the cart state
const ShoppingApp = () => {
	const [cart, setCart] = useState([])
	
	const addToCart = (item) => {
		setCart([...cart, item])
	}
	
	const removeFromCart = (itemId) => {
		setCart(cart.filter(item => item.id !== itemId))
	}
	
	return (
		<div>
			<CartSummary itemCount={cart.length} />
			<ProductList onAddToCart={addToCart} />
			<Cart items={cart} onRemove={removeFromCart} />
		</div>
	)
}

// Shows cart item count
const CartSummary = ({ itemCount }) => {
	return <div>Cart: {itemCount} items</div>
}

// Lists available products
const ProductList = ({ onAddToCart }) => {
	const products = [
		{ id: 1, name: 'Widget', price: 9.99 },
		{ id: 2, name: 'Gadget', price: 19.99 }
	]
	
	return (
		<div>
			<h2>Products</h2>
			{products.map(product => (
				<div key={product.id}>
					{product.name} - ${product.price}
					<button onClick={() => onAddToCart(product)}>
						Add to Cart
					</button>
				</div>
			))}
		</div>
	)
}

// Displays cart contents
const Cart = ({ items, onRemove }) => {
	return (
		<div>
			<h2>Your Cart</h2>
			{items.map(item => (
				<div key={item.id}>
					{item.name} - ${item.price}
					<button onClick={() => onRemove(item.id)}>Remove</button>
				</div>
			))}
		</div>
	)
}

export default ShoppingApp
```

> [!NOTE] Notice how `ShoppingApp` is the single source of truth for the cart data. All three child components receive either the data or functions to modify it through props.

# Sibling Communication

When two sibling components need to share data, lift the state to their common parent:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
import { useState } from 'react'

const MessageApp = () => {
	const [message, setMessage] = useState('')
	
	return (
		<div>
			<MessageInput onMessageChange={setMessage} />
			<MessageDisplay message={message} />
		</div>
	)
}

const MessageInput = ({ onMessageChange }) => {
	return (
		<input 
			type="text"
			onChange={(e) => onMessageChange(e.target.value)}
			placeholder="Type a message..."
		/>
	)
}

const MessageDisplay = ({ message }) => {
	return (
		<div>
			<h3>Live Preview:</h3>
			<p>{message || 'Start typing...'}</p>
		</div>
	)
}

export default MessageApp
```

The key insight: `MessageInput` and `MessageDisplay` are siblings. They can't communicate directly, so we lift the `message` state to their parent `MessageApp`.

> [!TIP] When you find yourself trying to access state from a sibling component, that's a sign you should lift the state to a common parent.

# Managing Complex State Updates

When lifting state, you often need to pass down functions that update state in specific ways:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
import { useState } from 'react'

const TodoApp = () => {
	const [todos, setTodos] = useState([])
	
	const addTodo = (text) => {
		const newTodo = {
			id: Date.now(),
			text,
			completed: false
		}
		setTodos([...todos, newTodo])
	}
	
	const toggleTodo = (id) => {
		setTodos(todos.map(todo =>
			todo.id === id 
				? { ...todo, completed: !todo.completed }
				: todo
		))
	}
	
	const deleteTodo = (id) => {
		setTodos(todos.filter(todo => todo.id !== id))
	}
	
	return (
		<div>
			<TodoInput onAdd={addTodo} />
			<TodoList 
				todos={todos}
				onToggle={toggleTodo}
				onDelete={deleteTodo}
			/>
		</div>
	)
}

const TodoInput = ({ onAdd }) => {
	const [text, setText] = useState('')
	
	const handleSubmit = (e) => {
		e.preventDefault()
		if (text.trim()) {
			onAdd(text)
			setText('')
		}
	}
	
	return (
		<form onSubmit={handleSubmit}>
			<input 
				value={text}
				onChange={(e) => setText(e.target.value)}
				placeholder="Add a todo..."
			/>
			<button type="submit">Add</button>
		</form>
	)
}

const TodoList = ({ todos, onToggle, onDelete }) => {
	return (
		<ul>
			{todos.map(todo => (
				<TodoItem 
					key={todo.id}
					todo={todo}
					onToggle={onToggle}
					onDelete={onDelete}
				/>
			))}
		</ul>
	)
}

const TodoItem = ({ todo, onToggle, onDelete }) => {
	return (
		<li>
			<input 
				type="checkbox"
				checked={todo.completed}
				onChange={() => onToggle(todo.id)}
			/>
			<span style={{ 
				textDecoration: todo.completed ? 'line-through' : 'none' 
			}}>
				{todo.text}
			</span>
			<button onClick={() => onDelete(todo.id)}>Delete</button>
		</li>
	)
}

export default TodoApp
```

> [!IMPORTANT] Notice how we pass down multiple functions (`onToggle`, `onDelete`) that encapsulate different ways to modify the state. This keeps the logic in the parent while allowing children to trigger changes.

# Avoiding Prop Drilling

As your component tree grows deeper, passing props through many levels can become cumbersome. This is called "prop drilling":

```javascript
// ❌ Prop drilling - passing props through components that don't use them
const App = () => {
	const [user, setUser] = useState({ name: 'Alex' })
	return <Layout user={user} />
}

const Layout = ({ user }) => {
	return <Sidebar user={user} /> // Just passing through
}

const Sidebar = ({ user }) => {
	return <UserProfile user={user} /> // Just passing through
}

const UserProfile = ({ user }) => {
	return <div>{user.name}</div> // Finally using it!
}
```

For now, prop drilling is acceptable for 2-3 levels. In future lessons, we'll learn about Context API and state management solutions that solve this problem.

> [!CAUTION] Don't prematurely optimize. Prop drilling through 2-3 levels is perfectly fine. Only reach for more complex solutions when prop drilling becomes genuinely painful.

# Best Practices

1. **Lift state to the lowest common ancestor** - Don't lift state higher than necessary
2. **Keep state as local as possible** - If only one component needs it, keep it there
3. **Name callback props clearly** - Use `onSomething` naming convention (e.g., `onUserChange`, `onSubmit`)
4. **Pass only what's needed** - Don't pass entire objects if a component only needs one property
5. **Use composition** - Sometimes you can avoid lifting state by restructuring your components

```javascript
// ✅ Good - Clear naming and minimal props
const Parent = () => {
	const [count, setCount] = useState(0)
	return <Counter count={count} onIncrement={() => setCount(count + 1)} />
}

// ❌ Less ideal - Unclear naming
const Parent = () => {
	const [count, setCount] = useState(0)
	return <Counter value={count} change={() => setCount(count + 1)} />
}
```

> [!TIP] Think of lifted state as a shared resource. Only lift it when multiple components truly need to read or modify the same data.

# When to Lift State

Lift state when:

- Multiple components need to display the same data
- Multiple components need to modify the same data
- Components need to stay synchronized
- A child component needs to trigger changes that affect siblings

Keep state local when:

- Only one component uses the data
- The data doesn't affect other components
- The component is self-contained

> [!NOTE] As your application grows, you'll develop intuition for when to lift state. Start by keeping state local, and lift it only when you need to share it.
