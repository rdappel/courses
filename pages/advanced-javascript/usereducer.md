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

A reducer is a pure function that takes the current state and an action, then returns the new state. The concept comes from the `Array.reduce()` method you have used before.

> [!NOTE] If you would like to review `Array.reduce()`, please see the [Higher-Order Functions](https://fvtc.software/appel/modern-javascript/higher-order-functions#reduce) lesson.

Here's the basic pattern:

```javascript
(currentState, action) => newState
```

Let's look at a simple example using an action object - a gold counter for a game:

```javascript
// reducer function
const goldReducer = (state, action) => {
	switch(action.type) {
		case 'EARN_GOLD':
			return state + action.payload
		case 'SPEND_GOLD':
			return Math.max(0, state - action.payload)
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
{ type: 'LEVEL_UP' }

// Action with payload
{ type: 'EARN_GOLD', payload: 100 }

// Action with multiple properties
{ type: 'UPDATE_STATS', level: 5, experience: 1000 }
```

# Introduction to useReducer

The `useReducer` hook gives you a way to manage state using a reducer function. It returns the current state and a dispatch function to trigger state updates.

Here's a basic gold tracker component using `useReducer`:

```javascript
import { useReducer } from 'react'

const goldReducer = (state, action) => {
	switch(action.type) {
		case 'EARN_GOLD':
			return state + action.payload
		case 'SPEND_GOLD':
			return Math.max(0, state - action.payload)
		case 'RESET':
			return 0
		default:
			return state
	}
}

const GoldTracker = () => {
	const [gold, dispatch] = useReducer(goldReducer, 0)

	return (
		<div>
			<p>Gold: {gold}</p>
			<button onClick={() => dispatch({ type: 'EARN_GOLD', payload: 10 })}>Earn 10 Gold</button>
			<button onClick={() => dispatch({ type: 'SPEND_GOLD', payload: 5 })}>Spend 5 Gold</button>
			<button onClick={() => dispatch({ type: 'RESET' })}>Reset</button>
		</div>
	)
}

export default GoldTracker
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
	hp: 100,
	maxHP: 100,
	mp: 50,
	maxMP: 50
}

const characterReducer = (state, action) => {
	switch(action.type) {
		case 'LEVEL_UP':
			return {
				...state,
				level: state.level + 1,
				maxHP: state.maxHP + 10,
				maxMP: state.maxMP + 5,
				hp: state.hp + 10,
				mp: state.mp + 5
			}
		case 'TAKE_DAMAGE':
			return {
				...state,
				hp: Math.max(0, state.hp - action.payload)
			}
		case 'HEAL':
			return {
				...state,
				hp: Math.min(state.maxHP, state.hp + action.payload)
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
			<p>HP: {character.hp}/{character.maxHP}</p>
			<p>MP: {character.mp}/{character.maxMP}</p>

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

# Combining useReducer and Context API

For truly global state, you can combine `useReducer` with Context API to create a powerful state management solution. This allows you to share your character state across multiple components:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here's how to create a character context with `useReducer`:

```javascript
// contexts/CharacterContext.jsx
import { createContext, useReducer } from 'react'

export const CharacterContext = createContext()

const initialState = {
	name: 'Aragorn',
	level: 1,
	experience: 0,
	hp: 100,
	maxHP: 100,
	mp: 50,
	maxMP: 50
}

const characterReducer = (state, action) => {
	switch(action.type) {
		case 'LEVEL_UP':
			return {
				...state,
				level: state.level + 1,
				maxHP: state.maxHP + 10,
				maxMP: state.maxMP + 5,
				hp: state.hp + 10,
				mp: state.mp + 5
			}
		case 'TAKE_DAMAGE':
			return {
				...state,
				hp: Math.max(0, state.hp - action.payload)
			}
		case 'HEAL':
			return {
				...state,
				hp: Math.min(state.maxHP, state.hp + action.payload)
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

export const CharacterProvider = ({ children }) => {
	const [character, dispatch] = useReducer(characterReducer, initialState)

	return (
		<CharacterContext.Provider value={{ character, dispatch }}>
			{children}
		</CharacterContext.Provider>
	)
}
```

Now you can use the character state in any component:

```javascript
import { useContext } from 'react'
import { CharacterContext } from '../contexts/CharacterContext'

const Character = () => {
	const { character, dispatch } = useContext(CharacterContext)

    return (
        <div>
            <h2>{character.name}</h2>
            <p>Level: {character.level}</p>
            <p>Experience: {character.experience}</p>
            <p>HP: {character.hp}/{character.maxHP}</p>
            <p>MP: {character.mp}/{character.maxMP}</p>

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

This pattern scales well for large applications and makes state updates predictable and traceable.

# Exercise 1

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Complete the inventory manager by implementing the `inventoryReducer` function. 

Copy the component code below and fill in the reducer logic to handle `ADD_ITEM` and `REMOVE_ITEM` actions:

```javascript
import { useReducer, useState } from 'react'

// TODO: Implement this reducer function

const InventoryManager = () => {
	const [items, dispatch] = useReducer(inventoryReducer, [])
	const [itemName, setItemName] = useState('')

	const addItem = () => {
		if (!itemName.trim()) return
		dispatch({ type: 'ADD_ITEM', payload: itemName })
		setItemName('')
	}

	return (
		<div>
			<h2>Inventory</h2>
			
			<div>
				<input
					type="text"
					value={itemName}
					onChange={(e) => setItemName(e.target.value)}
					placeholder="Item name"
				/>
				<button onClick={addItem}>Add Item</button>
			</div>

			<ul>
				{items.map(item => (
					<li key={item.id}>
						{item.name}
						<button onClick={() => dispatch({ type: 'REMOVE_ITEM', payload: item.id })}>
							Remove
						</button>
					</li>
				))}
			</ul>

			<p>Total items: {items.length}</p>
		</div>
	)
}

export default InventoryManager
```

**Your Task:** Implement the `inventoryReducer` to:

- Handle `ADD_ITEM` action: add a new item with `{ id: Date.now(), name: action.payload }`
- Handle `REMOVE_ITEM` action: filter out the item matching `action.payload` (the id)
- Return the current state for any unknown action types

## Hints {#exercise-1-hints}

<details>
	<summary>How do I structure the reducer?</summary>

Use a switch statement to handle different action types:

```javascript
const inventoryReducer = (state, action) => {
	switch(action.type) {
		case 'ADD_ITEM':
			// return new array with item added
		case 'REMOVE_ITEM':
			// return new array with item filtered out
		default:
			return state
	}
}
```

</details>

<details>
	<summary>How do I add an item?</summary>

Create a new object with `id` and `name`, then return a new array with the item added:

```javascript
case 'ADD_ITEM':
	return [...state, { id: Date.now(), name: action.payload }]
```

</details>

<details>
	<summary>How do I remove an item?</summary>

Use `filter` to create a new array without the item matching the given id:

```javascript
case 'REMOVE_ITEM':
	return state.filter(item => item.id !== action.payload)
```

</details>

## Solution {#exercise-1-solution}

<details>
	<summary>Show the Answer</summary>

```javascript
const inventoryReducer = (state, action) => {
	switch(action.type) {
		case 'ADD_ITEM':
			return [...state, { id: Date.now(), name: action.payload }]
		case 'REMOVE_ITEM':
			return state.filter(item => item.id !== action.payload)
		default:
			return state
	}
}
```

</details>

<details>
	<summary>Walkthrough Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# Key Takeaways

- Use `useReducer` when you have complex state logic or multiple related state values
- Reducer functions are pure functions that return new state based on actions
- Actions are plain objects that describe what should happen
- `useReducer` returns `[state, dispatch]` where dispatch sends actions to the reducer
- Combine `useReducer` with Context API for global state management
- Reducers make state transitions explicit and easier to debug
