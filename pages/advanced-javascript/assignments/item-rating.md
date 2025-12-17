---
title: Assignment 3 - Item Rating
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/assignments/item-rating
dev: http://localhost:3006/appel/advanced-javascript/assignments/item-rating
repo: https://github.com/rdappel/courses
---

# Assignment 3 - Item Rating

In this assignment, you will modify your personal homepage from Assignment 2 to add an interactive star rating system. Visitors will be able to rate your favorite movies, books, or hobbies by clicking on stars (1-5).

Additionally, you will add a [GitHub Corners](https://github.com/tholman/github-corners) ribbon to your site that links to your GitHub repository.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Specifications

### 1. Add GitHub Corners Ribbon

Add a GitHub Corners ribbon to your homepage that links to your GitHub repository.

Visit [GitHub Corners](https://tholman.com/github-corners/) and choose a color/style that fits your homepage.

It should position automatically in the corner of your page.

> [!IMPORTANT] Remember to replace the default link with the URL of your own GitHub repository.

> [!TIP] If you don't like the color options on the site, you can change the `fill` attribute in the SVG code to match your homepage's color scheme.

### 2. Add rating functionality

Each item in your list (movies, books, or hobbies) should now have:
- A star rating component that displays 5 stars
- The ability for users to click on a star to set a rating
- Visual feedback showing which stars are filled based on the rating

### 3. Create an Interactive StarRating Component

Create a `StarRating` component that:
- Accepts an `initialRating` prop (the starting rating value, default to 0)
- Uses the `useState` hook to manage its own rating state internally
- Displays 5 stars (you can use `react-icons` or Unicode stars)
- Shows filled stars up to the current rating value
- Shows outlined/empty stars for the remaining stars
- Allows users to click on a star to set the rating (clicking the 3rd star sets rating to 3)
- The rating persists within the component

### 4. Update Your Item List

Modify the section of your homepage that displays your favorite movies, books, or hobbies to:
- Display each item with its name
- Add a StarRating component next to each item
- Optionally pass an `initialRating` prop to start with a specific rating

### 5. Install react-icons

If you haven't already, install the `react-icons` package to use Font Awesome star icons:

```bash
npm install react-icons
```

Then import the star icons in your StarRating component:

```javascript
import { FaStar, FaRegStar } from 'react-icons/fa'
```

> [!TIP] `FaStar` is the filled star icon, and `FaRegStar` is the outlined/empty star icon.

## Enhanced Feature (Optional)

If you want to enhance your rating component, consider adding **Half Stars**:

Allow for half-star ratings (e.g., 3.5 stars)

   - Import `FaStarHalfAlt` from `react-icons/fa`
   - Update your logic to handle decimal ratings


# Using AI for this Assignment

You are allowed to use AI tools like Copilot or ChatGPT to help you with this assignment. However, make sure to:
- Understand how the `useState` hook works with arrays of objects
- Ensure your click handlers properly update the state
- Test the functionality thoroughly to ensure ratings persist correctly

> [!NOTE] AI tools may suggest more complex approaches (like passing callback functions). For this assignment, keep the rating state internal to the StarRating component to focus on understanding `useState` basics.

## Deploying to GitHub Pages

Make sure your changes are deployed to GitHub Pages so your site is live:

1. Delete (or rename your /docs folder)

2. Run the build command:

```bash
npm run build
```

3. Rename the generated `/dist` folder to `/docs`

4. Commit and push your changes to GitHub

## Submitting to Blackboard

Submit the URL of your deployed GitHub Pages site on Blackboard for grading.
