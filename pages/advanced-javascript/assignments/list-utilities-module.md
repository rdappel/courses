---
title: Assignment 1 - List Utilities Module
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/assignments/list-utilities-module
dev: http://localhost:3006/appel/advanced-javascript/assignments/list-utilities-module
repo: https://github.com/rdappel/courses
---

# Assignment 1 - List Utilities Module

For this assignment, you'll create a small JavaScript utility module used for filtering, sorting, and searching lists of movies. This is a foundation you'll reuse later in the course.

<details open>
   <summary class="video">Show/Hide Video</summary>
   <div class="video-container">
      <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
         allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
      </iframe>
   </div>
</details>

# Instructions

1. Fork and Clone the Starter Repository

- Go to: [https://github.com/FVTC/ajs-assignment1](https://github.com/FVTC/ajs-assignment1)
- Click "Fork" to create your own copy.
- Clone your forked repository to your local machine.

2. Create the Utility File

- In your cloned repo, create a file named exactly `list-utils.js`.

3. Implement Required Functions

All functions must be **pure** (no mutation of input arrays). Implement the following:

| Function | What It Should Do |
|----------|-------------------|
| `filterByCategory(movies, category)` | Return movies whose category matches (case-insensitive). |
| `filterByMinRating(movies, minRating)` | Return movies with rating >= minRating. |
| `getFeatured(movies)` | Return movies where `isFeatured === true`. |
| `sortByRating(movies, order = 'desc')` | Return a new array sorted by rating. Default: highest → lowest. `order = 'asc'` reverses it. |
| `getAverageRating(movies)` | Return the average rating (number). Empty array → return `0`. |
| `searchByTitle(movies, searchTerm)` | Case-insensitive substring search on title. |

# Submission

When you are finished with your assignment, push your changes to your forked GitHub repository.

There is a GitHub Actions workflow configured to automatically test your functions. Make sure all tests pass and the workflow shows a passing status.

When you have confirmed this, submit your repository link to Blackboard.