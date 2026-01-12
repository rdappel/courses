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

# Component Communication Patterns

In React, data flows in one direction: from parent to child. There are two main ways components communicate:

**Parent → Child**: Pass data down through props
**Child → Parent**: Pass callback functions down as props, child calls them with data

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

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
// Parent component
const App = () => {
	const onNameChange = (newName) => console.log(newName)
	
	return (
		<div>
			<NameInput onNameChange={onNameChange} />
		</div>
	)
}

// Child component
const NameInput = ({ onNameChange }) => {
	const [name, setName] = useState('')
	
	return (
		<input 
			type="text"
			style={{ fontSize: '16px', padding: '8px', width: '300px', margin: '10px 10px 20px' }}
			value={name} 
			onChange={e => setName(e.target.value)}
		/>
	)
}
```

# Lifting State

More commonly than the child-to-parent pattern, you'll need to lift state up when multiple sibling components need to share the same data.

Let's look at an example:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the App code from the example:

```javascript
import { useState } from 'react'

import NameInput from './components/NameInput'
import NameTag from './components/NameTag'

const App = () => {
	const [name, setName] = useState('John Snow')

	return (
		<div>
			<NameInput name={name} setName={setName} />
			<NameTag name={name} />
		</div>
	)
}

export default App
```

And here is the NameInput component:

```javascript
const NameInput = ({ name, setName }) => {
	return (
		<input 
			type="text"
			style={{ fontSize: '16px', padding: '8px', width: '300px', margin: '10px 10px 20px' }}
			value={name} 
			onChange={e => setName(e.target.value)}
		/>
	)
}

export default NameInput
```

## When to Lift State

Lift state when:

- Multiple components need to display the same data
- Multiple components need to modify the same data
- Components need to stay synchronized
- A child component needs to trigger changes that affect siblings

Keep state local when:

- Only one component uses the data
- The data doesn't affect other components
- The component is self-contained

> [!NOTE] As you progress, you'll develop intuition for when to lift state. Start by keeping state local, and lift it only when you need to share it.

# Exercise 1

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Hints {#exercise-1-hints}

<details>
	<summary>How do I start?</summary>

You will need to create two separate state variables in the parent component: one for the first name and one for the last name. Then, pass down the appropriate state and setter functions to each input component.

</details>

<details>
	<summary>How do I get the name into the NameTag?</summary>

You can use string interpolation to combine the first and last names into a single string when passing it to the NameTag component:

```javascript
<NameTag name={`${firstName} ${lastName}`} />
```

</details>

## Solution {#exercise-1-solution}

<details>
	<summary>Show the Answer</summary>

```javascript
import { useState } from 'react'

import NameInput from './components/NameInput'
import NameTag from './components/NameTag'

const App = () => {
	const [firstName, setFirstName] = useState('')
	const [lastName, setLastName] = useState('')

	return (
		<div>
			<NameInput firstName={firstName} setFirstName={setFirstName} />
			<NameInput lastName={lastName} setLastName={setLastName} />
			<NameTag name={`${firstName} ${lastName}`} />
		</div>
	)
}

export default App
```

# Avoiding Prop Drilling

As your component tree grows deeper, passing props through many levels can become cumbersome. This is called "prop drilling":

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

For now, prop drilling is acceptable for 2-3 levels. In future lessons, we'll learn about Context API and state management solutions that solve this problem.

> [!CAUTION] Don't prematurely optimize. Prop drilling through 2-3 levels is perfectly fine. Only reach for more complex solutions when prop drilling becomes genuinely painful.

# Best Practices

1. **Lift state to the lowest common ancestor** - Don't lift state higher than necessary
2. **Keep state as local as possible** - If only one component needs it, keep it there
3. **Name callback props clearly** - Use `onSomething` naming convention (e.g., `onUserChange`, `onSubmit`)
4. **Pass only what's needed** - Don't pass entire objects if a component only needs one property
5. **Use composition** - Sometimes you can avoid lifting state by restructuring your components

# Practical Example: Shopping Cart

Let's build a more realistic example with a shopping cart where multiple components need to access and modify the same data.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code for the ShoppingApp:

```javascript
import { useState } from 'react'

import Cart from './components/Cart'
import CartSummary from './components/CartSummary'
import ProductList from './components/ProductList'

const App = () => {
	const [ cart, setCart ] = useState([])

	const onAddToCart = product => {
		setCart([...cart, product])
	}

	const onRemoveFromCart = index => {
		setCart(cart.filter((item, i) => i !== index))
	}

	console.log('Cart:', cart)

	return (
		<div>
			<CartSummary itemCount={cart.length} />
			<ProductList
				onAddToCart={onAddToCart}
			/>
			<Cart
				items={cart}
				onRemove={onRemoveFromCart}
			/>
		</div>
	)
}

export default App
```

Here is the ProductList component:

```javascript
const ProductList = ({ onAddToCart}) => {
	const products = [
		{ id: 1, name: 'Laptop', price: 999.99 },
		{ id: 2, name: 'Smartphone', price: 499.99 },
		{ id: 3, name: 'Tablet', price: 299.99 },
	]

	return (
		<div>
			<h2>Product List</h2>
			{products.map(({ id, name, price }) => (
				<>
					<div key={id}>{name} - ${price}</div>
					<button
						onClick={() => onAddToCart({ id, name, price })}
					>Add to Cart</button>
				</>
			))}
		</div>
	)
}

export default ProductList
```

Here is the code for the Cart component:

```javascript
const Cart = ({ items, onRemove }) => {

	return (
		<div>
			<h2>Your Cart</h2>
			{items.map(({ id, name, price }, index) => (
				<div key={index}>
					{name} - ${price}
					<button onClick={() => onRemove(index)}>Remove</button>
				</div>
			))}
		</div>
	)
}

export default Cart
```

And here is the CartSummary component:

```javascript
const CartSummary = ({ itemCount }) => {
	return <span>Items in Cart: {itemCount}</span>
}

export default CartSummary
```
