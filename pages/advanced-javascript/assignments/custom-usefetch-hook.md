---
title: Assignment 8 - Custom useFetch Hook
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/assignments/custom-usefetch-hook
dev: http://localhost:3006/appel/advanced-javascript/assignments/custom-usefetch-hook
repo: https://github.com/rdappel/courses
---

# Assignment 8 - Custom useFetch Hook

In this assignment, you will create a custom `useFetch` hook and use it on your personal homepage to dynamically load external content from a free public API. This will demonstrate your understanding of custom hooks and how they can encapsulate reusable logic.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Specifications

### 1. Create a useFetch Hook

Create a custom hook called `useFetch` in a `hooks/` directory:

- Create a file `hooks/useFetch.js`
- The hook should accept a URL as a parameter
- Return an object containing `data`, `loading`, and `error` states
- Handle the complete fetch lifecycle (loading, success, error)
- Use `useEffect` to trigger the fetch when the URL changes

> [!TIP] You can use the `useFetch` implementation from the lecture notes as a starting point. Make sure you understand how it works!

### 2. Choose a Public API

Select one of these free public APIs to fetch data from (or find your own):

**Recommended APIs:**

- **JSONPlaceholder** - `https://jsonplaceholder.typicode.com/users`
  - Fake user data, posts, comments, todos
  - Great for testing, no API key required

- **REST Countries** - `https://restcountries.com/v3.1/all`
  - Country data including flags, population, languages
  - No API key required

- **Open Trivia Database** - `https://opentdb.com/api.php?amount=10&type=multiple`
  - Trivia questions in various categories
  - No API key required

- **PokéAPI** - `https://pokeapi.co/api/v2/pokemon?limit=20`
  - Pokemon data including stats, abilities, sprites
  - No API key required

- **Dog CEO's Dog API** - `https://dog.ceo/api/breeds/image/random/10`
  - Random dog images by breed
  - No API key required

- **Cat Facts** - `https://catfact.ninja/facts?limit=5`
  - Random cat facts
  - No API key required

> [!NOTE] Make sure to check the API documentation to understand the structure of the response data. Most APIs return JSON that you'll need to navigate to display the relevant information.

### 3. Create a New Component

Create a new component on your homepage that uses the `useFetch` hook:

- Import and use your custom `useFetch` hook
- Pass the API URL to the hook
- Destructure `data`, `loading`, and `error` from the returned object
- Display appropriate content based on these states

### 4. Display Loading State

When data is being fetched:

- Show a loading message (e.g., "Loading data...")
- Style it to match your site's theme
- Consider adding a loading spinner or animation

### 5. Display Error State

When an error occurs:

- Show an error message to the user
- Include the error details for debugging
- Style the error message to be noticeable
- Provide helpful information (e.g., "Failed to load data. Please try again later.")

### 6. Display Fetched Data

When data successfully loads:

- Map over the array of data (if applicable) and render each item
- Display relevant information from each item
- Style the data presentation to match your homepage
- Use semantic HTML elements

Example for displaying countries:

```javascript
import useFetch from '../hooks/useFetch'

const Countries = () => {
	const { data, loading, error } = useFetch('https://restcountries.com/v3.1/all')

	if (loading) return <p>Loading countries...</p>
	if (error) return <p>Error: {error}</p>

	return (
		<div className="countries">
			<h2>Countries of the World</h2>
			<ul>
				{data.slice(0, 10).map(country => (
					<li key={country.cca3}>
						<img src={country.flags.png} alt={`${country.name.common} flag`} width="50" />
						<span>{country.name.common}</span>
					</li>
				))}
			</ul>
		</div>
	)
}

export default Countries
```

### 7. Add the Component to Your Homepage

- Import your new component into your main homepage or app component
- Position it appropriately within your page layout
- Ensure it fits visually with the rest of your site

## Optional Enhancements

If you want to take this assignment further:

1. **Multiple API Calls**: Use your `useFetch` hook in multiple components with different APIs

2. **User Controls**: Add buttons to fetch different data (e.g., different Pokemon, new random dogs)

3. **Limit Results**: Add logic to only display a subset of results (e.g., first 10 items)

4. **Caching**: Modify your hook to cache API responses to avoid refetching the same data

5. **Retry Logic**: Add a "Retry" button that appears when an error occurs

6. **Search/Filter**: Add input fields to search or filter the API results

> [!NOTE] I'm not expecting you to implement these enhancements yourself. Leverage Copilot, and then take a look at the code it generates to understand how it works.

## Using AI for this Assignment

You are encouraged to use AI tools like Copilot or ChatGPT to help you with this assignment. However, make sure to:

- Understand how custom hooks work and why they're useful
- Comprehend the structure of the API response you're working with
- Know how `useEffect` manages the fetch lifecycle
- Verify that all three states (loading, error, success) are properly handled

# Submission

## Deploying to GitHub Pages

Deploy your updated site to GitHub Pages:

1. Run the build command:

```bash
npm run build
```

2. Delete your existing `/docs` folder

3. Rename the generated `/dist` folder to `/docs`

4. Commit and push your changes to GitHub

5. Verify your deployed site loads and fetches data correctly from the API

## Submitting to Blackboard

Submit the URL of your deployed GitHub Pages site on Blackboard for grading.
