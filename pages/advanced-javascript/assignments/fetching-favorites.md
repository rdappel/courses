---
title: Assignment 4 - Fetching Favorites
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/assignments/fetching-favorites
dev: http://localhost:3006/appel/advanced-javascript/assignments/fetching-favorites
repo: https://github.com/rdappel/courses
---

# Assignment 4 - Fetching Favorites

In this assignment, you will refactor your personal homepage from Assignment 3 to fetch your favorite movies, books, or hobbies from JSON files using the `useEffect` hook. Instead of hardcoding the data in your component, you'll load it dynamically with proper loading states and error handling.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Specifications

### 1. Create Data Files

Create a `public/data` directory in your project and move your favorite items (movies, books, or hobbies) into JSON files.

**movies.json** - Your favorite movies with additional details:
```json
[
  {
    "id": 1,
    "title": "The Shawshank Redemption",
    "year": 1994,
    "genre": "Drama",
    "director": "Frank Darabont",
    "rating": 0
  },
  {
    "id": 2,
    "title": "The Dark Knight",
    "year": 2008,
    "genre": "Action",
    "director": "Christopher Nolan",
    "rating": 0
  },
  {
    "id": 3,
    "title": "Inception",
    "year": 2010,
    "genre": "Sci-Fi",
    "director": "Christopher Nolan",
    "rating": 0
  }
]
```

You can also create **books.json**, **games.json**, or **hobbies.json** depending on what you featured on your homepage. Add at least 5 items to your JSON file(s).

> [!TIP] Include properties like `genre`, `year`, `author`, or other relevant details to make your data more interesting. Start the `rating` at 0 so users can rate items themselves.

### 2. Create Components to Display Fetched Data

Create at least two new components that fetch and display data:

**ProjectList Component:**
- Fetches data from `projects.json` using `useEffect`
- Displays a loading message while data is being fetched
- Handles errors gracefully with an error message
- Maps through the projects and displays them in cards or a list
- Each project should show its title, description, and technologies

**Skills Component:**
- FetchRefactor Your List Component

Update the section of your homepage that displays your favorite items to fetch data instead of using a hardcoded array:

**Before (hardcoded):**
```javascript
const App = () => {
Your component must display a loading message while data is being fetched:

```javascript
if (loading) {
  return <div className="loading">Loading movies...</div>
}
```

Style your loading message to match your site's design. Consider adding a spinner or animatio
```javascript
const App = () => {
  const [movies, setMovies] = useState([])
  const [loading, setLoading] = useState(true)
Your component must handle errors gracefully:
```javascript
if (error) {
  return <div className="error">Error: {error}</div>
}
```

Test your error handling by temporarily changing the file path to something incorrect like `/data/wrong.json`
        setError(err.message)
      } finally {
        setLoading(false)
      }
    }

    fetchMovies()
  }, [])
  // ...
}
```
Style your loading message to match your site's design.

### 4. Implement Error Handling

Both components must handle errors:
```javascript
const [error, setError] = useState(null)

if (error) {
  return <div>Error: {error}</div>
}
```

You can test error handling by temporarily changing the file path to a non-existent file.

### 5. Use Async/Await Pattern

Use the async/await pattern inside your `useEffect` hook:
Display Fetched Data with Additional Details

Update your list rendering to display the additional information from your JSON:

```javascript
<ul>
  {movies.map(movie => (
    <li key={movie.id}>
      <h3>{movie.title} ({movie.year})</h3>
      <p>Director: {movie.director} | Genre: {movie.genre}</p>
      <StarRating initialRating={movie.rating} />
    </li>
  ))}
</ul>
```

> [!IMPORTANT] Use `movie.id` for the key prop instead of the array index for better React performance and consistency
Use `useEffect` in your main App component to update the document title:

```javascript
useEffect(() => {
  document.title = 'Your Name - Portfolio'
}, [])
```

You can make this dynamic by Based on Data

Use `useEffect` to update the document title once the data loads:

```javascript
useEffect(() => {
  if (!loading && movies.length > 0) {
    document.title = `${movies.length} Favorite Movies`
  }
}, [loading, movies])
```

This makes your page title dynamic based on the fetched data.

### 7. Style Your Enhanced List

Improve the visual presentation of your items:
- Add CSS for the loading and error states
- Style each item card with better spacing and typography
- Display the additional details (year, genre, director) in an appealing way
- Ensure your StarRating component integrates nicely with the new data
- Consider adding hover effects or transitions
const filteredSkills = filter === 'all' 
  ? skills by Genre/Category
Add buttons to filter your items by genre or category:
```javascript
const [filter, setFilter] = useState('all')

const filteredMovies = filter === 'all' 
  ? movies 
  : movies.filter(movie => movie.genre === filter)

// Then in your JSX:
<div>
  <button onClick={() => setFilter('all')}>All</button>
  <button onClick={() => setFilter('Drama')}>Drama</button>
  <button onClick={() => setFilter('Action')}>Action</button>
</div>
```

### Sort Functionality
Add a dropdown or buttons to sort your items:
```javascript
const [sortBy, setSortBy] = useState('title')

const sortedMovies = [...movies].sort((a, b) => {
  if (sortBy === 'year') return b.year - a.year
  if (sortBy === 'title') return a.title.localeCompare(b.title)
  return 0
})
```

### Search Feature
Add a search input to filter items by title:
```javascript
consmovies.json
    (or books.json, games.json, etc.)
src/
  components/
    Header.jsx
    Nav.jsx
    Footerdisplay multiple types of items (movies AND books AND games) with separate sections for each
public/
  data/
    projects.json
    skills.json
src/
  components/
    Header.jsx
    Nav.jsx
    Footer.jsx
    ProjectList.jsx
    Skills.jsxThe loading message should appear briefly when the page first loads
2. **Error Handling**: Change `/data/movies.json` to `/data/wrong.json` temporarily and verify the error displays
3. **Data Display**: All properties from your JSON (title, year, genre, etc.) should display correctly
4. **Star Ratings**: The StarRating component should still work with each item
5. **Document Title**: The browser tab title should update after data loads
6. **Console Logs**: Check for any warnings or errors in the browser console
7. **Single Fetch**: Open the Network tab in DevTools and confirm the JSON file is only fetched once

> [!CAUTION] If your data fetches on every render (infinite loop), make sure you included the empty
## Testing Your Implementation
 understanding:
- How `useEffect` works with the dependency array `[]`
- The async/await pattern for data fetching
- Error handling with try/catch/finally
- Managing multiple state variables (data, loading, error)
- Why the data only loads once instead of on every render

> [!NOTE] Make sure you understand the code you're submitting. Be prepared to explain how your useEffect hook works and why you structured it the way you did
5. **Multiple Renders**: Ensure data only fetches once (not on every render)

> [!CAUTION] If your data fetches on every render (infinite loop), check that you included the dependency array `[]` in your useEffect.

## Using AI for this Assignment

You are encouraged to use AI tools like Copilot or ChatGPT to help you with this assignment. Focus on:
- Understanding how `useEffect` works with the dependency array
- Grasping the async/await pattern for data fetching
- Implementing proper error handling with try/catch
- Managing multiple state variables (data, loading, error)

> [!NOTE] Make sure you understand the code you're submitting. You may be asked to explain how your useEffect implementation works.

## Submission

### Deploying to GitHub Pages

Deploy your updated site to GitHub Pages:

1. Delete (or rename) your `/docs` folder

2. Run the build command:
```bash
npm run build
```

3. Rename the generated `/dist` folder to `/docs`

4. Commit and push your changes to GitHub

5. Verify your site loads correctly and all data fetches properly

### Submitting to Blackboard

Submit the URL of your deployed GitHub Pages site on Blackboard for grading.

> [!IMPORTANT] Make sure your JSON files are in the `/public/data` directory so they're accessible after deployment. Files in `/public` are copied to the build output automatically.
