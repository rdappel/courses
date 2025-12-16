---
title: Assignment 2 - React Homepage
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/assignments/homepage
dev: http://localhost:3006/appel/advanced-javascript/assignments/homepage
repo: https://github.com/rdappel/courses
---

# Assignment 2 - React Homepage

In this assignment, you will create a personal homepage using React components. You will build a component-based website that displays information about yourself using components.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Specifications

Your React application should have the following components:

### 1. Header Component

Create a `Header` component that contains:
- Your name or website title
- A tagline or subtitle
- Any other header content you want to include

### 2. Nav Component

Create a `Nav` component that contains:
- At least 3 navigation links (e.g., Home, Projects, Contact)
- The links don't need to work yet (we haven't learned routing)
- Use `#` for the href attributes

### 3. Footer Component

Create a `Footer` component that contains:
- Copyright information
- Social media links or contact information
- Any other footer content you want to include

### 4. Main Content

In your main App component, include:
- Your Header component
- Your Nav component
- A section with your bio or about information
- A list of your favorite movies, books, or hobbies (use the `map` function to render the list)
- Your Footer component

### 5. Styling

Style your components using CSS. You can use:
- A global stylesheet in your `src` folder
- Component-specific CSS files
- Inline styles via the `style` prop

At a minimum, your styling should include:
- Colors and fonts that create a cohesive design
- Proper spacing and layout
- Responsive design considerations

### 6. Props

Use props to pass data to your components. For example:
- Pass your name and tagline to the `Header` component
- Pass your `Nav` component to the `Header` component as children
- Pass any other relevant data to your components via props

Use keys when rendering lists with the `map` function to ensure each list item is uniquely identified.

## Project Setup

Create a new Vite + React project by creating a new directory and running the following commands:

```bash
npm create vite@latest .
npm i
npm run dev
```

Then, go through the project structure and remove unnecessary files.

## Component Structure

Your project should have a structure similar to this:

```
src/
  components/
    Header.jsx
    Nav.jsx
    Footer.jsx
  App.jsx
  App.css
  main.jsx
```

## Example Code Structure

Here's an example of how your `App` component might look:

```javascript
import Header from './components/Header'
import Nav from './components/Nav'
import Footer from './components/Footer'

const App = () => {
  const favoriteMovies = [
    'The Shawshank Redemption',
    'The Godfather',
    'The Dark Knight'
  ]

  return (
    <div className="app">
      <Header name="Your Name" tagline="Web Developer">
        <Nav />
      </Header>
      <main>
        <section>
          <h2>About Me</h2>
          <p>Your bio here...</p>
        </section>
        <section>
          <h2>Favorite Movies</h2>
          <ul>
            {favoriteMovies.map((movie, index) => (
              <li key={index}>{movie}</li>
            ))}
          </ul>
        </section>
      </main>
      <Footer />
    </div>
  )
}

export default App
```

> [!IMPORTANT] Remember to use the `key` prop when rendering lists with `map`!

# Using AI for this Assignment

You are allowed to use AI tools like Copilot or ChatGPT to help you with this assignment. However, make sure to:
- Understand the code that is generated.
- Customize the code to fit your personal homepage.
- Ensure that the final code is your own work and reflects your understanding of React components and props.

> [!NOTE] It is unlikely that AI tools will produce a complete solution that meets all the requirements of this assignment. You will need to review, modify, and enhance the generated code to ensure it fulfills the specifications outlined above.

# Submission

## Pushing to GitHub

You are going to replace your github.io pages site (homepage from Modern JavaScript) with this new React homepage. This video will walk you through the steps to push your project to GitHub.

## Submitting to Blackboard

Once you have your project pushed to GitHub, submit the link to your GitHub repository to Blackboard.
