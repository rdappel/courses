---
title: useReducer for Complex State
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/usereducer-for-complex-state
dev: http://localhost:3006/appel/advanced-javascript/usereducer-for-complex-state
repo: https://github.com/rdappel/courses
---

# When to Use useReducer

As your React applications grow more complex, managing state with multiple `useState` calls can become difficult. When you have:

- Complex state logic with many related values
- State that depends on previous state
- Multiple sub-values that need to be updated together
- State transitions that involve conditional logic

The `useReducer` hook is a better choice than `useState`.

# Understanding Reducers

A reducer is a pure function that takes the current state and an action, then returns the new state. The concept comes from the `Array.reduce()` method you may have used before.

> [!NOTE] If you would like to review `Array.reduce()`, please see the [Higher-Order Functions](https://fvtc.software/appel/modern-javascript/higher-order-functions#reduce) lesson.

Here's the basic pattern:

```javascript
(currentState, action) => newState
```

Let's look at a simple example using an action object:

```javascript
// reducer function
const counterReducer = (state, action) => {
	switch(action.type) {
		case 'INCREMENT':
			return state + 1
		case 'DECREMENT':
			return state - 1
		case 'RESET':
			return 0
		default:
			return state
	}
}
```

## Action Objects

Actions are plain objects that describe what should happen. They typically have a `type` property and can include a `payload` with additional data:

```javascript
// Simple action
{ type: 'INCREMENT' }

// Action with payload
{ type: 'SET_USER', payload: { name: 'Alice', age: 25 } }

// Action with multiple properties
{ type: 'UPDATE_STATS', level: 5, experience: 1000 }
```

# Introduction to useReducer

The `useReducer` hook gives you a way to manage state using a reducer function. It returns the current state and a dispatch function to trigger state updates.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here's a basic counter component using `useReducer`:

```javascript
import { useReducer } from 'react'

const counterReducer = (state, action) => {
	switch(action.type) {
		case 'INCREMENT':
			return state + 1
		case 'DECREMENT':
			return state - 1
		case 'RESET':
			return 0
		default:
			return state
	}
}

const Counter = () => {
	const [count, dispatch] = useReducer(counterReducer, 0)

	return (
		<div>
			<p>Count: {count}</p>
			<button onClick={() => dispatch({ type: 'INCREMENT' })}>+</button>
			<button onClick={() => dispatch({ type: 'DECREMENT' })}>-</button>
			<button onClick={() => dispatch({ type: 'RESET' })}>Reset</button>
		</div>
	)
}

export default Counter
```

## How useReducer Works

The `useReducer` hook takes two required arguments:

1. **reducer function** - The function that determines how state updates happen
2. **initial state** - The starting value for your state

```javascript
const [state, dispatch] = useReducer(reducerFunction, initialState)
```

It returns:

- **state** - The current state value
- **dispatch** - A function to trigger state updates by sending actions to the reducer

# Managing Complex State

The true power of `useReducer` comes when managing state with multiple related values. Let's build a character management system:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here's a more complex example with an object state:

```javascript
import { useReducer } from 'react'

const initialState = {
	name: 'Aragorn',
	level: 1,
	experience: 0,
	health: 100,
	maxHealth: 100,
	mana: 50,
	maxMana: 50
}

const characterReducer = (state, action) => {
	switch(action.type) {
		case 'LEVEL_UP':
			return {
				...state,
				level: state.level + 1,
				maxHealth: state.maxHealth + 10,
				maxMana: state.maxMana + 5,
				health: state.health + 10,
				mana: state.mana + 5
			}
		case 'TAKE_DAMAGE':
			return {
				...state,
				health: Math.max(0, state.health - action.payload)
			}
		case 'HEAL':
			return {
				...state,
				health: Math.min(state.maxHealth, state.health + action.payload)
			}
		case 'GAIN_EXPERIENCE':
			return {
				...state,
				experience: state.experience + action.payload
			}
		case 'RESET':
			return initialState
		default:
			return state
	}
}

const Character = () => {
	const [character, dispatch] = useReducer(characterReducer, initialState)

	return (
		<div>
			<h2>{character.name}</h2>
			<p>Level: {character.level}</p>
			<p>Experience: {character.experience}</p>
			<p>Health: {character.health}/{character.maxHealth}</p>
			<p>Mana: {character.mana}/{character.maxMana}</p>

			<button onClick={() => dispatch({ type: 'LEVEL_UP' })}>Level Up</button>
			<button onClick={() => dispatch({ type: 'TAKE_DAMAGE', payload: 10 })}>Take Damage</button>
			<button onClick={() => dispatch({ type: 'HEAL', payload: 15 })}>Heal</button>
			<button onClick={() => dispatch({ type: 'GAIN_EXPERIENCE', payload: 50 })}>Gain XP</button>
			<button onClick={() => dispatch({ type: 'RESET' })}>Reset</button>
		</div>
	)
}

export default Character
```

Notice how all the state is kept together and updates are predictable. Each action clearly defines what changes happen.

# Form State with useReducer

`useReducer` is especially useful for managing form state with many fields:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here's a form using `useReducer`:

```javascript
import { useReducer } from 'react'

const initialState = {
	username: '',
	email: '',
	password: '',
	confirmPassword: '',
	errors: {}
}

const formReducer = (state, action) => {
	switch(action.type) {
		case 'FIELD_CHANGE':
			return {
				...state,
				[action.field]: action.value,
				errors: { ...state.errors, [action.field]: '' }
			}
		case 'SET_ERROR':
			return {
				...state,
				errors: { ...state.errors, [action.field]: action.message }
			}
		case 'RESET':
			return initialState
		default:
			return state
	}
}

const SignupForm = () => {
	const [form, dispatch] = useReducer(formReducer, initialState)

	const handleChange = (e) => {
		dispatch({
			type: 'FIELD_CHANGE',
			field: e.target.name,
			value: e.target.value
		})
	}

	const handleSubmit = (e) => {
		e.preventDefault()

		// Validate passwords match
		if (form.password !== form.confirmPassword) {
			dispatch({
				type: 'SET_ERROR',
				field: 'confirmPassword',
				message: 'Passwords do not match'
			})
			return
		}

		// Form is valid - submit
		console.log('Form submitted:', form)
		dispatch({ type: 'RESET' })
	}

	return (
		<form onSubmit={handleSubmit}>
			<div>
				<input
					type="text"
					name="username"
					value={form.username}
					onChange={handleChange}
					placeholder="Username"
				/>
				{form.errors.username && <span>{form.errors.username}</span>}
			</div>

			<div>
				<input
					type="email"
					name="email"
					value={form.email}
					onChange={handleChange}
					placeholder="Email"
				/>
				{form.errors.email && <span>{form.errors.email}</span>}
			</div>

			<div>
				<input
					type="password"
					name="password"
					value={form.password}
					onChange={handleChange}
					placeholder="Password"
				/>
				{form.errors.password && <span>{form.errors.password}</span>}
			</div>

			<div>
				<input
					type="password"
					name="confirmPassword"
					value={form.confirmPassword}
					onChange={handleChange}
					placeholder="Confirm Password"
				/>
				{form.errors.confirmPassword && <span>{form.errors.confirmPassword}</span>}
			</div>

			<button type="submit">Sign Up</button>
			<button type="button" onClick={() => dispatch({ type: 'RESET' })}>Clear</button>
		</form>
	)
}

export default SignupForm
```

# Combining useReducer and Context API

For truly global state, you can combine `useReducer` with Context API to create a powerful state management solution:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here's how to create a global state provider with `useReducer`:

```javascript
// contexts/GameContext.jsx
import { createContext, useReducer } from 'react'

export const GameContext = createContext()

const initialState = {
	player: {
		name: 'Hero',
		level: 1,
		health: 100,
		experience: 0
	},
	inventory: [],
	settings: {
		difficulty: 'normal',
		volume: 50
	}
}

const gameReducer = (state, action) => {
	switch(action.type) {
		case 'UPDATE_PLAYER':
			return {
				...state,
				player: { ...state.player, ...action.payload }
			}
		case 'ADD_ITEM':
			return {
				...state,
				inventory: [...state.inventory, action.payload]
			}
		case 'REMOVE_ITEM':
			return {
				...state,
				inventory: state.inventory.filter(item => item.id !== action.payload)
			}
		case 'UPDATE_SETTINGS':
			return {
				...state,
				settings: { ...state.settings, ...action.payload }
			}
		default:
			return state
	}
}

export const GameProvider = ({ children }) => {
	const [state, dispatch] = useReducer(gameReducer, initialState)

	return (
		<GameContext.Provider value={{ state, dispatch }}>
			{children}
		</GameContext.Provider>
	)
}
```

Then use it in your components:

```javascript
import { useContext } from 'react'
import { GameContext } from '../contexts/GameContext'

const PlayerStats = () => {
	const { state, dispatch } = useContext(GameContext)

	return (
		<div>
			<h2>{state.player.name}</h2>
			<p>Level: {state.player.level}</p>
			<p>Health: {state.player.health}</p>
			<p>Experience: {state.player.experience}</p>

			<button onClick={() => dispatch({
				type: 'UPDATE_PLAYER',
				payload: { level: state.player.level + 1 }
			})}>Level Up</button>
		</div>
	)
}

export default PlayerStats
```

This pattern scales well for large applications and makes state updates predictable and traceable.

# Key Takeaways

- Use `useReducer` when you have complex state logic or multiple related state values
- Reducer functions are pure functions that return new state based on actions
- Actions are plain objects that describe what should happen
- `useReducer` returns `[state, dispatch]` where dispatch sends actions to the reducer
- Combine `useReducer` with Context API for global state management
- Reducers make state transitions explicit and easier to debug
