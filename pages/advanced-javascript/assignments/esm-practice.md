---
title: Assignment 1 - ES Modules Practice
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/assignments/esm-practice
dev: http://localhost:3006/appel/advanced-javascript/assignments/esm-practice
repo: https://github.com/rdappel/courses
---

# Assignment 1 - ES Modules Practice

In this assignment, you will practice using ES Module syntax in Node.js. You will create a custom module with both named and default exports, then import and use them in your main application.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Specifications

### 1. Project Setup

Create a new Node.js project by creating a new directory and running `npm init.`

> [!IMPORTANT] You're going to push your code up to GitHub later, so now is a good time to add a `.gitignore` file and include `node_modules/` in it.

### 2. Configure ES Modules

Modify your `package.json` file to enable ES Modules by adding the `"type": "module"` field:

```json
{
  "name": "esm-practice",
  "version": "1.0.0",
  "type": "module",
  "main": "app.js"
}
```

### 3. Create a Custom Module

Create a file called `rpg-utils.js` that exports the following:

- A **default export**: A function that creates a character with a name and class, returning a character object
- Two **named exports**: 
  - A function that calculates attack damage based on attack power and defense
  - A function that calculates spell mana cost based on spell level

Use the following code as a starting point:

```javascript
// todo: make this your default export
const createCharacter = (name, characterClass) => {
  return {
    name: name,
    class: characterClass,
    level: 1,
    hp: 100
  }
}

// todo: make these your named exports
const calculateDamage = (attackPower, defense) => {
  const damage = attackPower - defense
  return damage > 0 ? damage : 0
}

const calculateManaCost = (spellLevel) => {
  return spellLevel * 10
}
```

### 4. Create Your Main Application

Create a file called `app.js` that:

1. Imports the default export and named exports from `utils.js`
2. Uses each function
3. Logs the results to the console to prove they work

Use the following code as a starting point:

```javascript
// todo: Import the default and named exports from rpg-utils.js

// Test the default export
const hero = createCharacter('Aragorn', 'Warrior')
console.log(hero)

// Test the named exports
const damage = calculateDamage(50, 20)
console.log(`Attack deals ${damage} damage!`)

const manaCost = calculateManaCost(5)
console.log(`Level 5 spell costs ${manaCost} mana`)
```

> [!NOTE] When importing from local files in ES Modules, you must include the `.js` file extension!

### 5. Run Your Application

Test your application by running:

```bash
node app.js
```

You should see output similar to:

```
{ name: 'Aragorn', class: 'Warrior', level: 1, hp: 100 }
Attack deals 30 damage!
Level 5 spell costs 50 mana
```

## Additional Challenges (Optional)

If you finish early, try these additional exercises:

1. Create another module that exports only named exports (no default)
2. Export a constant value (like an array or object) and import it in your app

> [!NOTE]  You can not directly import JSON files using ESM syntax like you can with CommonJS.

# Submission

## Pushing to GitHub

Create a new repository on GitHub called `esm-practice`. Push your project to GitHub.

## Submitting to Blackboard

Once you have your project pushed to GitHub, submit the link to your GitHub repository to Blackboard.
