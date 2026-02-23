---
title: Assignment 7 - Homepage Section Controls
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/assignments/homepage-section-controls
dev: http://localhost:3006/appel/advanced-javascript/assignments/homepage-section-controls
repo: https://github.com/rdappel/courses
---

# Assignment 7 - Homepage Section Controls

In this assignment, you will add a `useReducer` hook to your existing homepage.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Specifications

Add a **Homepage Section Controls** feature using `useReducer`.

### Requirements

1. Use `useReducer` to manage visibility for these homepage sections:
   - `showAbout`
   - `showFavorites`
   - `showContact`

2. Add buttons that dispatch reducer actions:
   - Toggle About
   - Toggle Favorites
   - Toggle Contact
   - Reset (show all sections again)

3. Conditionally render each section based on reducer state.

4. Keep this update inside your existing homepage project (do not create a new app).

## Starter Example (Reducer Shape)

```javascript
const initialState = {
	showAbout: true,
	showFavorites: true,
	showContact: true
}

const sectionReducer = (state, action) => {
	switch (action.type) {
		case 'TOGGLE_ABOUT':
			return { ...state, showAbout: !state.showAbout }
		case 'TOGGLE_FAVORITES':
			return { ...state, showFavorites: !state.showFavorites }
		case 'TOGGLE_CONTACT':
			return { ...state, showContact: !state.showContact }
		case 'RESET':
			return initialState
		default:
			return state
	}
}
```

## Submission

### Pushing to GitHub

Commit and push your homepage updates to your existing homepage repository.

### Submitting to Blackboard

Submit the link to your updated GitHub repository (or deployed page, if requested by your section) on Blackboard.