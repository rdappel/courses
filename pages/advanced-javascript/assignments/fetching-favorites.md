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
        <iframe src="https://www.youtube.com/embed/svMw4E9eULo" width="100%" height="100%" frameborder="0" allowfullscreen
            allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
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

### 2. Refactor Your List Component

Update the section of your homepage that displays your favorite items to fetch data instead of using a hardcoded array.

Your component will need to:

- Use three state variables: one for the data array, one for loading status, and one for errors
- Use `useEffect` with an async function inside to fetch the data from `/data/movies.json` (or your chosen file)
- Use `fetch()` to retrieve the JSON file
- Update the state with the fetched data
- Handle the loading and error states appropriately

> [!TIP] Remember that `useEffect` cannot be async directly, but you can define an async function inside it and call it immediately.

### 3. Implement Loading States

Your component must display a loading message while data is being fetched. The loading state should:

- Show before the data has loaded
- Display a user-friendly message (e.g., "Loading movies...")
- Be styled to match your site's design
- Optionally include a spinner or animation

### 4. Implement Error Handling

Your component must handle errors gracefully. If the fetch fails:

- Display an error message to the user
- Include the error details in the message
- Style the error message to stand out visually

Test your error handling by temporarily changing the file path to something incorrect like `/data/wrong.json`.

### 5. Display Fetched Data

Update your list rendering to display the additional information from your JSON. Each item should show:

- The item's title and year
- Additional details like genre, director, or author (depending on your data)
- The StarRating component with the rating from the JSON

> [!IMPORTANT] Use `data.id` for the key prop instead of the array index for better React performance and consistency.

### 6. Update Document Title

Use a second `useEffect` to update the browser tab title (document.title) once the data loads. The title should:

- Display the count of items (e.g., "5 Favorite Movies")
- Only update after the data has finished loading
- Use the appropriate dependency array to run when the data changes

# Using AI for this Assignment

You are encouraged to use AI tools like Copilot or ChatGPT to help you with this assignment. Focus on understanding:

- How `useEffect` works with the dependency array `[]`
- The async/await pattern for data fetching
- Error handling with try/catch/finally
- Managing multiple state variables (data, loading, error)
- Why the data only loads once instead of on every render

> [!NOTE] Make sure you understand the code you're submitting. You may be asked to explain how your useEffect implementation works.

# Submission

## Deploying to GitHub Pages

Deploy your updated site to GitHub Pages:

1. Delete (or rename) your `/docs` folder

2. Run the build command:

```bash
npm run build
```

1. Rename the generated `/dist` folder to `/docs`

2. Commit and push your changes to GitHub

3. Verify your site loads correctly and all data fetches properly

## Submitting to Blackboard

Submit the URL of your deployed GitHub Pages site on Blackboard for grading.

> [!IMPORTANT] Make sure your JSON files are in the `/public/data` directory so they're accessible after deployment. Files in `/public` are copied to the build output automatically.
