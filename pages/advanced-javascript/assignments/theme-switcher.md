---
title: Assignment 5 - Theme Switcher
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript/assignments/theme-switcher
dev: http://localhost:3006/appel/advanced-javascript/assignments/theme-switcher
repo: https://github.com/rdappel/courses
---

# Assignment 5 - Theme Switcher

In this assignment, you will add a theme switcher feature to your personal homepage. Users will be able to toggle between light and dark themes (or any two themes of your choice). You'll practice lifting state to the appropriate component level and using the `useRef` hook to manage focus properly.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0" allowfullscreen
            allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

## Specifications

### 1. Create a Theme Toggle Component

Create a `ThemeToggle` component that:

- Displays a button to toggle between themes (e.g., "Light Mode" / "Dark Mode" or use an icon)
- Accepts the current theme as a prop
- Accepts a callback function to handle theme changes
- Uses descriptive text or icons to indicate the current theme state

### 2. Lift State to the Appropriate Level

Determine which component should own the theme state:

- The theme state must be accessible to all components that need to apply styling based on the theme
- Consider which parent component is the common ancestor of all components that need the theme
- Lift the state up to that component level
- Pass the theme state and setter function down as props to child components that need them

### 3. Apply Theme Styles Throughout Your Application

Update your components to apply different styles based on the current theme:

- Modify your `Header`, `Nav`, `Footer`, and main content areas to respond to theme changes
- Define color schemes for both themes (e.g., light mode: light background with dark text, dark mode: dark background with light text)
- Ensure text remains readable in both themes
- Consider background colors, text colors, borders, and other visual elements

You can apply theme styles using:
- Conditional inline styles
- Conditional CSS classes
- CSS variables that change based on the theme

### 4. Use the useRef Hook for Focus Management

Implement proper focus management using the `useRef` hook:

- After the theme toggles, the toggle button should receive focus
- Create a ref for the toggle button
- Use the ref to programmatically focus the button after the theme state changes
- This ensures keyboard users don't lose their place when toggling themes

> [!TIP] Remember that `useEffect` can be used to perform side effects after state changes. You may need to focus the button in a `useEffect` that depends on the theme state.

### 5. Enhance User Experience

Make your theme switcher user-friendly:

- Provide clear visual feedback when hovering over the toggle button
- Consider adding a transition effect when theme colors change
- Ensure the toggle button is easily discoverable on the page
- Optionally add an icon (you can use `react-icons`) to make the button more visually appealing

## Optional Enhancements

If you want to take your theme switcher further, consider:

1. **Persist Theme Preference**: Use `localStorage` to save the user's theme preference so it persists across page refreshes

2. **System Theme Detection**: Use the `prefers-color-scheme` media query to detect the user's system theme preference and use it as the default

3. **More Than Two Themes**: Extend your switcher to support multiple themes (e.g., light, dark, high contrast, colorful)

4. **Smooth Transitions**: Add CSS transitions to smoothly animate color changes when switching themes

## Using AI for this Assignment

You are encouraged to use AI tools like Copilot or ChatGPT to help you with this assignment. However, make sure to:

- Understand how lifting state works and why it's necessary
- Comprehend how `useRef` differs from `useState`
- Know when and why to use `useEffect` for side effects
- Verify that your theme applies consistently across all components

# Submission

## Pushing to GitHub

Remember to run `npm run build` to create an optimized production build of your homepage before pushing and then rename the `build` folder to `docs` in your repository. This will ensure GitHub Pages serves the latest version of your site.

## Submitting to Blackboard

Submit the link to your GitHub repository to Blackboard.