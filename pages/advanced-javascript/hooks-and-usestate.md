---
title: React Hooks and useState
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/hooks-and-usestate
dev: http://localhost:3006/appel/advanced-javascript/hooks-and-usestate
repo: https://github.com/rdappel/courses
---

# What are React Hooks?

React Hooks are functions that let you "hook into" React features from functional components. Hooks allow you to use state and other React features without writing a class.

Hooks always start with the word "use" (like `useState`, `useEffect`, `useContext`, etc.). In this lesson, we'll focus on `useState`, which is the most fundamental hook for managing state in React components.

This video covers project setup and an introduction to React Hooks:

> [!NOTE] In the video, I will be importing `styles/shared-styles.js` for some basic styling used in the examples. You can copy the code from [this gist](https://gist.github.com/rdappel/a7f2d1659d37b7a9fb3c1e95844e0536).

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/aaYKyEHKyso" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# What is State?

State is data that changes over time in your application. When state changes, React automatically re-renders the component to reflect those changes in the UI. This is what makes React applications interactive and dynamic.

<div class="centering">
    <img src="https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/ajs/react-state-mgt-cycle-dark.svg" alt="State Management" aria-hidden="true" class="adaptive dark">
    <img src="https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/ajs/react-state-mgt-cycle-light.svg" alt="State Management" aria-hidden="true" class="adaptive light">
</div>

Examples of state include:

- A counter value that increases when you click a button
- Form input values that change as the user types
- A boolean that tracks whether a modal is open or closed
- An array of items in a shopping cart

# The useState Hook

The `useState` hook allows you to add state to functional components. It returns an array with two elements: the current state value and a function to update that state.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/SbsmY_Igekw" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here's a character stat example:

```javascript
import { useState } from 'react'

import { containerStyle, buttonStyle } from '../styles/shared-styles'

const CharacterStats = () => {
	const [strength, setStrength] = useState(10)

    const updateStrength = amount => {
        if (strength + amount >= 0) setStrength(strength + amount)
    }

    const isDisabled = () => strength <= 0

    return (
        <div className="character-stats" style={containerStyle}>
            <h2>Character Stats</h2>
            <div>
                <button
					style={buttonStyle}
					onClick={() => updateStrength(-1)}
					disabled={isDisabled()}
				>-</button>
                <span>Strength: {strength}</span>
                <button
					style={buttonStyle}
					onClick={() => updateStrength(1)}
				>+</button>
            </div>
        </div>
    )
}

export default CharacterStats
```

## How useState Works

Let's break down the syntax:

```javascript
const [strength, setStrength] = useState(10)
```

- `useState(10)` - This initializes state with a value of `10`
- `strength` - This is the current state value
- `setStrength` - This is the function we call to update the state
- The naming convention is `[value, setValue]`

> [!IMPORTANT] When you call the setter function (like `setStrength`), React will re-render the component with the new state value.

> [!NOTE] This demo illustrates Vite's HMR (Hot Module Replacement) feature. When you make changes to the code, the component updates in real-time without losing its state.

# Multiple State Variables

You can use `useState` multiple times in a single component to manage different pieces of state. Let's build on our previous example by adding skill points that limit how many stats you can increase.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/XAFetWrnPJ4" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here's the updated CharacterStats component:

```javascript
import { useState } from 'react'
import { containerStyle, buttonStyle } from '../styles/shared-styles'

const CharacterStats = () => {
    const [strength, setStrength] = useState(10)
    const [skillPoints, setSkillPoints] = useState(5)

    const increaseStat = () => {
        if (skillPoints <= 0) return

        setStrength(strength + 1)
        setSkillPoints(skillPoints - 1)
    }

    const decreaseStat = () => {
        if (strength <= 0) return

        setStrength(strength - 1)
        setSkillPoints(skillPoints + 1)
    }

    const isDisabled = () => strength <= 0

    return (
        <div className="character-stats" style={containerStyle}>
            <h2>Character Stats</h2>
            <div>Skill Points: {skillPoints}</div>
            <div>
                <button
					style={buttonStyle}
					onClick={() => decreaseStat()}
					disabled={isDisabled()}
				>-</button>
                <span>Strength: {strength}</span>
                <button
					style={buttonStyle}
					onClick={() => increaseStat()}
				>+</button>
            </div>
        </div>
    )
}

export default CharacterStats
```

Now we're tracking two separate pieces of state: `strength` and `skillPoints`. Notice how we can update them independently, and use conditional logic to prevent invalid actions.

# Form Inputs with State

Another common use case for multiple state variables is managing form inputs. Let's create a character creation form.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/YEQxS2othuI" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here's a character creation form:

```javascript
import { useState } from 'react'
import { containerStyle, inputStyle } from '../styles/shared-styles'

const CharacterCreation = () => {
    const [characterName, setCharacterName] = useState('')
    const [level, setLevel] = useState(1)
    const [isWarrior, setIsWarrior] = useState(false)

    return (
        <div className="character-creation" style={containerStyle}>
            <h2>Create Your Character</h2>
            <input 
                type="text"
                style={inputStyle}
                value={characterName} 
                onChange={({ target }) => setCharacterName(target.value)}
                placeholder="Enter character name"
            />
            <input 
                type="number"
                style={inputStyle}
                value={level} 
                onChange={({ target }) => setLevel(parseInt(target.value))}
                placeholder="Starting level"
            />
            <label style={inputStyle}>
                <input 
                    type="checkbox"
                    checked={isWarrior}
                    onChange={({ target }) => setIsWarrior(target.checked)}
                />
                Warrior Class
            </label>
            <p>Preview: {characterName || 'Unknown'} (Level {level}) - {isWarrior ? 'Warrior' : 'Mage'}</p>
        </div>
    )
}

export default CharacterCreation
```

# State with Objects

You can also store objects in state. However, when updating object state, you need to create a new object rather than modifying the existing one. Let's create a character with multiple stats.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/3M_2Dt1y-Hs" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here's an example using an object in state:

```javascript
import { useState } from 'react'
import { containerStyle, inputStyle } from '../styles/shared-styles'

const CharacterSheet = () => {
	const [character, setCharacter] = useState({
		name: 'Hero',
		health: 100,
		mana: 50
	})

	const updateName = (newName) => {
		setCharacter({
			...character,
			name: newName
		})
	}

	const takeDamage = () => {
		setCharacter({
			...character,
			health: character.health - 10
		})
	}

	return (
		<div>
			<input 
				type="text" 
				value={character.name}
				onChange={({ target }) updateName(e.target.value)}
				placeholder="Character Name"
			/>
			<p>Name: {character.name}</p>
			<p>Health: {character.health}</p>
			<p>Mana: {character.mana}</p>
			<button onClick={takeDamage}>Take Damage</button>
		</div>
	)
}

export default CharacterSheet
```

> [!TIP] The spread operator (`...character`) creates a copy of the existing character object, and then we override the specific property we want to update. This is important because React uses object reference comparison to detect changes.

# State with Arrays

When working with arrays in state, you also need to create new arrays rather than modifying the existing ones. This is important for React to properly detect changes. Let's create an inventory system.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/bCBw5QeLC-E" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here's an inventory system example:

```javascript
import { useState } from 'react'
import { containerStyle, inputStyle, buttonStyle } from '../styles/shared-styles'

const Inventory = () => {
    const [items, setItems] = useState([])
    const [itemName, setItemName] = useState('')

    const addItem = () => {
        if (itemName.trim() === '') return
        setItems([...items, itemName.trim()])
        setItemName('')
    }

    const handleKeyDown = ({ key }) => {
        if (key === 'Enter') addItem()
    }

    const removeItem = index => {
        setItems(items.filter((_, i) => i !== index))
    }

    return (
		<div style={containerStyle}>
			<h3>Inventory ({items.length} items)</h3>
			<input 
				type="text"
                style={inputStyle}
				value={itemName}
				onChange={({ target }) => setItemName(target.value)}
				onKeyDown={handleKeyDown}
				placeholder="Enter item name"
			/>
			<button onClick={addItem} style={buttonStyle}>+</button>
			<ul>
				{items.map((item, index) => (
					<li key={index}>
						{item}
						<button
                            onClick={() => removeItem(index)}
                            style={buttonStyle}
                        >-</button>
					</li>
				))}
			</ul>
		</div>
	)
}

export default Inventory
```

## Common Array Operations

Here are some common ways to update arrays in state:

```javascript
// Add an item to the end
setItems([...items, newItem])

// Add an item to the beginning
setItems([newItem, ...items])

// Remove an item by index
setItems(items.filter((_, i) => i !== indexToRemove))

// Update an item by index
setItems(items.map((item, i) => 
	i === indexToUpdate ? newValue : item
))

// Replace the entire array
setItems([item1, item2, item3])
```

> [!IMPORTANT] Never use array methods like `push`, `pop`, `splice`, or `sort` directly on state. These methods modify the array in place, which can cause React to miss updates. Always create a new array.

# Rules of Hooks

There are two important rules you must follow when using hooks:

1. **Only call hooks at the top level** - Don't call hooks inside loops, conditions, or nested functions. This ensures hooks are called in the same order each time a component renders.

2. **Only call hooks from React functions** - Call hooks from functional components or custom hooks, not from regular JavaScript functions.

```javascript
// ❌ Wrong - Don't use hooks inside conditions
const Component = () => {
	if (someCondition) {
		const [state, setState] = useState(0) // This will cause errors!
	}
}

// ✅ Correct - Use hooks at the top level
const Component = () => {
	const [state, setState] = useState(0)
	
	if (someCondition) {
		// Use the state here
	}
}
```

# Best Practices

Here are some best practices when working with `useState`:

- **Initialize with the correct type** - If you're storing a number, initialize with `0`, not an empty string
- **Keep state minimal** - Don't store values that can be computed from other state or props
- **Use multiple state variables** - It's better to have multiple simple state variables than one complex object
- **Name your state clearly** - Use descriptive names like `isLoading`, `userEmail`, `itemCount`
- **Batch related updates** - If multiple pieces of data change together, consider using an object or `useReducer`

```javascript
// ✅ Good - Clear naming and appropriate initial values
const [isInCombat, setIsInCombat] = useState(false)
const [enemyCount, setEnemyCount] = useState(0)
const [questName, setQuestName] = useState('')

// ❌ Less ideal - Vague names and wrong initial types
const [combat, setCombat] = useState(0)
const [data, setData] = useState(null)
```

# Setting Up a React Project with AI

As you've seen, after creating a new Vite + React project with `npm create vite@latest .`, we often need to clean up boilerplate code and set up our project structure. I have created a Markdown file that will allow chat-based AI tools to complete this process for you.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/5jIpUOSdjmM" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

You can download the file from [this gist](https://gist.github.com/rdappel/2f331c2e2c0085d825ec100f2e45c9a5).
