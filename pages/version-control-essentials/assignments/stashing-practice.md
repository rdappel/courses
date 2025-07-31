---
title: Assignment 7 - Stashing Practice
subtitle: Version Control Essentials
hideNav: false

live: https://fvtc.software/appel/version-control-essentials/assignments/stashing-practice
dev: http://localhost:3006/appel/version-control-essentials/assignments/stashing-practice
repo: https://github.com/rdappel/courses
---

# Assignment 7 - Stashing Practice

For this assignment, you will practice using Git stash to handle workflow interruptions while building a simple website project.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

# Instructions

## Part 1: Set Up Your Project

1. **Create a new project folder** called `your-name-stashing-practice`. For example, `john-doe-stashing-practice`.

2. **Initialize it as a Git repository**:

```bash
git init
```

3. **Create a basic HTML file** called `index.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Portfolio</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Welcome to My Portfolio</h1>
    </header>
    
    <main>
        <p>This is my personal website where I showcase my work.</p>
    </main>
</body>
</html>
```

4. **Create a CSS file** called `styles.css`:

```css
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 20px;
    background-color: #f5f5f5;
}

header {
    text-align: center;
    margin-bottom: 30px;
}

h1 {
    color: #333;
}

main {
    max-width: 800px;
    margin: 0 auto;
}
```

5. **Make your initial commit**:

```bash
git add .
git commit -m "Initial portfolio setup"
```

6. **Push your project to GitHub** (create a new repository called `your-name-stashing-practice`)

## Part 2: Feature Development with Interruptions

### Scenario 1: Working on Navigation

1. **Start working on a navigation menu**. Add this code inside the `<header>` section (after the `<h1>` tag) in your `index.html`:

```html
<nav>
    <ul>
        <li><a href="#home">Home</a></li>
        <li><a href="#about">About</a></li>
    </ul>
</nav>
```

2. **Add some CSS styling** for the navigation in your `styles.css` file:

```css
nav ul {
    list-style: none;
    padding: 0;
    display: flex;
    justify-content: center;
}

nav li {
    margin: 0 15px;
}
```

3. **BEFORE committing this work**, you realize you need to fix an urgent issue with the page title. **Stash your navigation work**:

```bash
git stash push -m "Working on navigation menu"
```

4. **Fix the urgent issue** - change the page title from "My Portfolio" to "My Awesome Portfolio" in the `<title>` tag.

5. **Commit the title fix**:

```bash
git add index.html
git commit -m "Fix: Update page title"
```

6. **Return to your navigation work**:

```bash
git stash pop
```

7. **Complete the navigation** by adding one more link in the HTML:

```html
<li><a href="#contact">Contact</a></li>
```

8. **Commit your completed navigation feature**:

```bash
git add .
git commit -m "Add navigation menu"
```

### Scenario 2: Working on About Section

1. **Start working on an About section**. Add this after the existing `<p>` tag in your `index.html`:

```html
<section id="about">
    <h2>About Me</h2>
    <p>I'm a student learning web development and Git!</p>
</section>
```

2. **Add CSS styling** for the About section in `styles.css`:

```css
section {
    margin: 30px 0;
    padding: 20px;
    background-color: white;
    border-radius: 5px;
}

h2 {
    color: #555;
}
```

3. **BEFORE committing**, you need to pull the latest changes from your remote repository. **Stash your About section work**:

```bash
git stash push -m "Adding About section"
```

4. **Pull any updates** from your remote repository:

```bash
git pull
```

5. **Restore your About section work**:

```bash
git stash pop
```

6. **Complete and commit your About section**:

```bash
git add .
git commit -m "Add About section"
```

### Scenario 3: Working on Contact Information

1. **Start adding contact information**. Add this section after your About section:

```html
<section id="contact">
    <h2>Contact Me</h2>
    <p>Email: your.email@example.com</p>
</section>
```

2. **Realize you're working on the wrong feature!** You should be working on a footer instead. **Stash your contact work**:

```bash
git stash push -m "Contact info work - wrong priority"
```

3. **Work on the footer instead**. Add this before the closing `</body>` tag:

```html
<footer>
    <p>&copy; 2025 My Portfolio. All rights reserved.</p>
</footer>
```

4. **Add footer CSS** to your `styles.css`:

```css
footer {
    text-align: center;
    margin-top: 40px;
    padding: 20px;
    background-color: #333;
    color: white;
}
```

5. **Commit your footer**:

```bash
git add .
git commit -m "Add footer"
```

6. **Now go back to your contact work**:

```bash
git stash pop
```

7. **Finish and commit your contact section**:

```bash
git add .
git commit -m "Add contact section"
```

8. **Push all your changes to GitHub**:

```bash
git push
```

## Part 3: Clean Up

1. **Check if you have any remaining stashes**:

```bash
git stash list
```

2. **If you have any old stashes, clean them up**:

```bash
git stash clear
```

# Submission

Once you have completed all the tasks, submit the following in Blackboard:

1. **The URL of your GitHub repository**

2. **Paste the output of the following command**:

```bash
git log --oneline
```

3. **Answer these questions**:

   - How many times did you use `git stash push` in this assignment?
   
   - What is the difference between `git stash pop` and `git stash apply`?
   
   - Describe a real-world scenario where you might need to stash your work.
   
   - Why is it helpful to add messages to your stashes (using the `-m` flag)?

> [!NOTE] Your final website should have a header with navigation, a main content area with About and Contact sections, and a footer. Make sure to test your HTML file in a browser to see how it looks!
