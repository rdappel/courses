---
title: Assignment 6 - Theme Switcher with Context API
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/assignments/theme-switcher-with-context
dev: http://localhost:3006/appel/advanced-javascript/assignments/theme-switcher-with-context
repo: https://github.com/rdappel/courses
---

# Assignment 6 - Theme Switcher with Context API

In this assignment, you'll refactor your previous theme switcher (from Assignment 5) to use the Context API instead of lifting state through props. This will eliminate prop drilling and make your application more scalable.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/JNCylHzkF9o" width="100%" height="100%" frameborder="0" allowfullscreen
            allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

## Specifications

### 1. Create a ThemeContext

Create a new file `contexts/ThemeContext.js` (or similar) that:

- Uses `createContext()` to create a theme context
- Exports the context for use throughout the application

### 2. Create a ThemeProvider Component

Create a `ThemeProvider` component that:

- Manages the theme state (light/dark or your custom themes)
- Provides both the theme value and a setter function through context
- Wraps your entire application (or at least the App component)
- Can be placed in your main entry point (e.g., `main.jsx`)

### 3. Remove Prop Drilling

Refactor your existing components to:

- Remove theme-related props from components that don't directly use them
- Use `useContext()` to access the theme directly in components that need it
- Eliminate the need to pass theme props through intermediate components

### 4. Update Your Components

Modify your components that need the theme to:

- Import `useContext` from React
- Import your `ThemeContext`
- Use `useContext(ThemeContext)` to get the current theme and setter function
- Apply styles based on the theme value

### 5. Ensure Consistency

Make sure:

- All components that previously received theme props now get it from context
- Theme styles are applied consistently across your entire application
- The theme toggle button still works as expected
- All functionality from Assignment 5 is preserved

## Comparison: Props vs Context

To help you understand the difference, here's a simple comparison:

**With Props (Assignment 5):**

```javascript
<App theme={theme} setTheme={setTheme} />
  <Header theme={theme} setTheme={setTheme} />
    <ThemeToggle theme={theme} setTheme={setTheme} />
```

**With Context (Assignment 6):**

```javascript
<ThemeProvider>
  <App />
    <Header />
      <ThemeToggle />  // Access theme directly from context
</ThemeProvider>
```

## Optional Enhancements

Consider these improvements:

1. **Persist with localStorage**: Use the theme context to save the user's preference to `localStorage` and restore it on page load

2. **System Theme Detection**: Detect the user's system theme preference using `prefers-color-scheme` and set it as the default

3. **Create a Custom Hook**: After learning about custom hooks, create a `useTheme` hook that wraps `useContext(ThemeContext)` for cleaner code

4. **Multiple Themes**: Extend your context to support more than two themes (e.g., light, dark, high contrast)

## Using AI for this Assignment

You are encouraged to use AI tools like Copilot or ChatGPT to help you with this assignment. However, make sure to:

- Understand how Context API works and when to use it instead of props
- Know the difference between `createContext()` and `useContext()`
- Understand why context eliminates prop drilling
- Be able to explain why your refactored code is better than the original

## Submission

### Pushing to GitHub

Remember to run `npm run build` to create an optimized production build before pushing, then rename the `build` folder to `docs` in your repository.

### Submitting to Blackboard

Submit the link to your GitHub repository to Blackboard.
