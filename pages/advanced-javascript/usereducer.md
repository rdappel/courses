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

# Form State with useReducer

`useReducer` is especially useful for managing form state with many fields. Let's create a character creation form for our game.

Let's start with a component that uses `useState` to manage form state:

```javascript
import { useState } from 'react'

const initialState = {
    name: '',
    characterClass: ''
}

const CharacterCreationForm = () => {
    const [form, setForm] = useState(initialState)

    const updateField = (field, value) =>
        setForm(prev => ({ ...prev, [field]: value }))

    const handleSubmit = e => {
        e.preventDefault()
        if (!form.name || !form.characterClass) return

        console.log('Character created:', form)
        setForm(initialState)
    }

    return (
        <form onSubmit={handleSubmit}>
            <input
                type="text"
                name="name"
                value={form.name}
                onChange={e => updateField('name', e.target.value)}
                placeholder="Character Name"
            />

            <select
                name="characterClass"
                value={form.characterClass}
                onChange={e => updateField('characterClass', e.target.value)}
            >
                <option value="">Select Class</option>
                <option value="warrior">Warrior</option>
                <option value="mage">Mage</option>
                <option value="rogue">Rogue</option>
            </select>

            <button type="submit">Create Character</button>
        </form>
    )
}

export default CharacterCreationForm
```

Now let's refactor this to use `useReducer` instead:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here's a character creation form using `useReducer`:

```javascript
import { useReducer } from 'react'

const initialState = {
	name: '',
	characterClass: ''
}

const formReducer = (state, action) => {
	switch(action.type) {
		case 'UPDATE_FIELD':
			return { ...state, [action.field]: action.value }
		case 'RESET':
			return initialState
		default:
			return state
	}
}

const CharacterCreationForm = () => {
	const [form, dispatch] = useReducer(formReducer, initialState)

	const handleSubmit = (e) => {
		e.preventDefault()
		if (!form.name || !form.characterClass) return
		
		console.log('Character created:', form)
		dispatch({ type: 'RESET' })
	}

	return (
		<form onSubmit={handleSubmit}>
			<input
				type="text"
				name="name"
				value={form.name}
				onChange={(e) => dispatch({ 
					type: 'UPDATE_FIELD', 
					field: 'name', 
					value: e.target.value 
				})}
				placeholder="Character Name"
			/>

			<select
				name="characterClass"
				value={form.characterClass}
				onChange={(e) => dispatch({ 
					type: 'UPDATE_FIELD', 
					field: 'characterClass', 
					value: e.target.value 
				})}
			>
				<option value="">Select Class</option>
				<option value="warrior">Warrior</option>
				<option value="mage">Mage</option>
				<option value="rogue">Rogue</option>
			</select>

			<button type="submit">Create Character</button>
		</form>
	)
}

export default CharacterCreationForm
```

# Combining useReducer and Context API

For truly global state, you can combine `useReducer` with Context API to create a powerful state management solution. Let's bring together everything we've learned - character stats, gold, and inventory - into one comprehensive game state:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here's how to create a global game state provider with `useReducer`:

```javascript
// contexts/GameContext.jsx
import { createContext, useReducer } from 'react'

export const GameContext = createContext()

const initialState = {
	character: {
		name: 'Aragorn',
		level: 1,
		hp: 100,
		maxHP: 100,
		mp: 50,
		maxMP: 50,
		experience: 0
	},
	gold: 0,
	inventory: [],
	settings: {
		difficulty: 'normal',
		volume: 50
	}
}

const gameReducer = (state, action) => {
	switch(action.type) {
		// Character actions
		case 'LEVEL_UP':
			return {
				...state,
				character: {
					...state.character,
					level: state.character.level + 1,
					maxHP: state.character.maxHP + 10,
					maxMP: state.character.maxMP + 5,
					hp: state.character.hp + 10,
					mp: state.character.mp + 5
				}
			}
		case 'TAKE_DAMAGE':
			return {
				...state,
				character: {
					...state.character,
					hp: Math.max(0, state.character.hp - action.payload)
				}
			}
		case 'HEAL':
			return {
				...state,
				character: {
					...state.character,
					hp: Math.min(state.character.maxHP, state.character.hp + action.payload)
				}
			}
		case 'GAIN_EXPERIENCE':
			return {
				...state,
				character: {
					...state.character,
					experience: state.character.experience + action.payload
				}
			}
		
		// Gold actions
		case 'EARN_GOLD':
			return {
				...state,
				gold: state.gold + action.payload
			}
		case 'SPEND_GOLD':
			return {
				...state,
				gold: Math.max(0, state.gold - action.payload)
			}
		
		// Inventory actions
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
		
		// Settings actions
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

Now you can use this comprehensive game state in any component:

```javascript
import { useContext } from 'react'
import { GameContext } from '../contexts/GameContext'

const GameDashboard = () => {
	const { state, dispatch } = useContext(GameContext)

	const buyPotion = () => {
		if (state.gold >= 20) {
			dispatch({ type: 'SPEND_GOLD', payload: 20 })
			dispatch({ type: 'ADD_ITEM', payload: { id: Date.now(), name: 'Health Potion', type: 'consumable' } })
		}
	}

	return (
		<div>
			{/* Character Stats */}
			<div>
				<h2>{state.character.name}</h2>
				<p>Level: {state.character.level}</p>
				<p>HP: {state.character.hp}/{state.character.maxHP}</p>
				<p>MP: {state.character.mp}/{state.character.maxMP}</p>
				<p>Experience: {state.character.experience}</p>
			</div>

			{/* Gold */}
			<div>
				<p>Gold: {state.gold}</p>
				<button onClick={() => dispatch({ type: 'EARN_GOLD', payload: 10 })}>Earn Gold</button>
			</div>

			{/* Actions */}
			<div>
				<button onClick={() => dispatch({ type: 'TAKE_DAMAGE', payload: 15 })}>Take Damage</button>
				<button onClick={() => dispatch({ type: 'HEAL', payload: 20 })}>Heal</button>
				<button onClick={() => dispatch({ type: 'GAIN_EXPERIENCE', payload: 50 })}>Gain XP</button>
				<button onClick={() => dispatch({ type: 'LEVEL_UP' })}>Level Up</button>
			</div>

			{/* Shop */}
			<div>
				<button onClick={buyPotion} disabled={state.gold < 20}>
					Buy Health Potion (20 gold)
				</button>
			</div>

			{/* Inventory */}
			<div>
				<h3>Inventory ({state.inventory.length})</h3>
				<ul>
					{state.inventory.map(item => (
						<li key={item.id}>{item.name}</li>
					))}
				</ul>
			</div>
		</div>
	)
}

export default GameDashboard
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

Create a simple inventory manager using `useReducer`. Your component should:

1. Track an array of items in state (each item has an `id` and `name`)
2. Have an input field and "Add Item" button
3. Display the list of items with a "Remove" button next to each item
4. Use a reducer with `ADD_ITEM` and `REMOVE_ITEM` actions

Start with an empty array as your initial state.

## Hints {#exercise-1-hints}

<details>
	<summary>How do I structure the reducer?</summary>

Your reducer should handle two action types:

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

When adding an item, create a new object with a unique `id` (you can use `Date.now()`) and the `name` from your input:

```javascript
case 'ADD_ITEM':
	return [...state, { id: Date.now(), name: action.payload }]
```

</details>

<details>
	<summary>How do I remove an item?</summary>

Use `filter` to remove the item with the matching id:

```javascript
case 'REMOVE_ITEM':
	return state.filter(item => item.id !== action.payload)
```

</details>

## Solution {#exercise-1-solution}

<details>
	<summary>Show the Answer</summary>

```javascript
import { useReducer, useState } from 'react'

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
