---
title: Workflow Interruptions & Stashing
subtitle: Version Control Essentials
hideNav: false

live: https://fvtc.software/appel/version-control-essentials/workflow-stashing
dev: http://localhost:3006/appel/version-control-essentials/workflow-stashing
repo: https://github.com/rdappel/courses
---

# Workflow Interruptions & Stashing

Sometimes when you're coding, you get interrupted. Maybe your boss asks you to quickly fix something, or you realize you need to pull the latest changes before continuing your work. But what if you're not ready to commit your current changes yet?

This is where Git's stashing feature comes to the rescue! Think of it as a way to temporarily save your work so you can come back to it later.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/xeF7YSK7DkM" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

## What is a Stack?

Before we learn about Git stash, let's understand what a "stack" is. A stack is like a stack of plates:

- You can only add plates to the **top** of the stack
- You can only remove plates from the **top** of the stack
- The last plate you put on is the first one you take off

This is called **LIFO** - "Last In, First Out."

Examples of stacks in everyday life:
- A stack of books on your desk
- A stack of papers
- Browser history (when you click "back")

![Diagram showing an item being added to a stack (pushed) and then removed (popped)](https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/vce/push-pop.png)

Git stash works the same way - when you save (stash) your work, it goes on top of the stack. When you want your work back, you get the most recent one first.

## What is Git Stash?

Git stash is like a temporary save button for your uncommitted changes. When you stash your work:

1. Git saves all your current changes
2. Your files go back to how they were at your last commit
3. You can work on something else
4. Later, you can restore your saved changes and continue where you left off

Think of it like putting your homework in a folder, working on a different assignment, then taking your homework back out of the folder.

# Basic Stashing Commands

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/QG3UCgYDWTo" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

## Saving Your Work - Git Stash Push

To save your current work temporarily:

```bash
git stash push -m "Working on navigation menu"
```

Or just:

```bash
git stash
```

This saves your changes and gives you a clean workspace.

## Getting Your Work Back - Git Stash Pop

To get your most recent saved work back:

```bash
git stash pop
```

This puts your changes back and removes them from the stash (like taking the top plate off the stack).

> [!IMPORTANT] `git stash pop` removes the stash after restoring it. If something goes wrong, you can't get it back easily.

## A Safer Option - Git Stash Apply

If you want to be extra careful:

```bash
git stash apply
```

This puts your changes back but keeps a copy in the stash (like copying the top plate instead of removing it).

# When Would You Use Stashing?

Here are some common situations where stashing is helpful:

## Scenario 1: Quick Bug Fix

You're working on a new feature, but you notice a typo that needs fixing right away.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/DrRT0XXLS6w" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

```bash
git stash push -m "New feature work"
# Fix the typo, commit it
git stash pop
# Continue with your feature
```

## Scenario 2: Need to Pull Updates

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/ZJOh4StGv_Y" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

You're working on your project, but your teammate pushed some changes. You need to pull their changes, but you're not ready to commit yours yet.

```bash
git stash push -m "Half-finished feature"
git pull
git stash pop
```

## Scenario 3: Wrong Branch

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/7J1XDZtxtl4" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

You realize you're working on the wrong branch!

```bash
git stash
git checkout dev
git stash pop
```

# Managing Your Stashes

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/jhajO7hdi8o" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

## Seeing What You've Stashed

To see all your stashes:

```bash
git stash list
```

This might show something like:

```
stash@{0}: On main: Working on navigation menu
stash@{1}: On main: Half-finished login form
```

## Looking at Stash Contents

To see what changes are in your most recent stash:

```bash
git stash show
```

## Cleaning Up Old Stashes

To delete a specific stash:

```bash
git stash drop stash@{1}
```

To delete all stashes:

```bash
git stash clear
```

# Exercise 1

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/Y3RksZAwzKE" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

For this exercise, you will practice the basic stashing workflow with a simple HTML project.

## Instructions

1. **Create a new project folder** and set it up:

```bash
mkdir stash-practice
cd stash-practice
git init
```

2. **Create a simple HTML file** called `index.html`:

```html
<!DOCTYPE html>
<html>
<head>
    <title>My Project</title>
</head>
<body>
    <h1>Welcome to My Site</h1>
    <p>This is my awesome website!</p>
</body>
</html>
```

3. **Make your first commit**:

```bash
git add index.html
git commit -m "Initial website"
```

4. **Start adding a new feature** - add a paragraph about yourself (but DON'T commit yet):

```html
<p>My name is [Your Name] and I'm learning Git!</p>
```

5. **Oops! You need to fix something urgent** - stash your work:

```bash
git stash push -m "Adding about me section"
```

6. **Make an urgent fix** - change the title to "My Awesome Project":

```html
<title>My Awesome Project</title>
```

7. **Commit the fix**:

```bash
git add index.html
git commit -m "Fix: Update page title"
```

8. **Get back to your feature work**:

```bash
git stash pop
```

9. **Finish and commit your feature**:

```bash
git add index.html
git commit -m "Add about me section"
```

## Hints {#exercise-1-hints}

<details>
    <summary>How do I see what's in my stash?</summary>

Use these commands to check your stashes:

```bash
git stash list    # See all stashes
git stash show    # See what's in the most recent stash
```

</details>

<details>
    <summary>What if I forget to add a message?</summary>

If you forget the `-m` flag, Git will create a generic message. It's not the end of the world, but adding messages helps you remember what you stashed!

</details>

## Submission {#exercise-1-submission}

Once you've completed the exercise, run these commands and copy the output:

```bash
git log --oneline
```

```bash
git stash list
```

Paste both outputs into the text area below.

<div data-language="bash" class="exercise-submission">
    <textarea placeholder="Paste your git log and stash list output here..."></textarea>
    <button type="button" class="submit-button">Submit Exercise</button>
</div>

## Solution {#exercise-1-solution}

<details>
    <summary>Show the Answer</summary>

Your git log should look something like this:

```
a1b2c3d Add about me section
e4f5g6h Fix: Update page title
i7j8k9l Initial website
```

Your stash list should be empty (since you used `git stash pop`):

```
# No output means no stashes remaining
```

Your final HTML should look like this:

```html
<!DOCTYPE html>
<html>
<head>
    <title>My Awesome Project</title>
</head>
<body>
    <h1>Welcome to My Site</h1>
    <p>This is my awesome website!</p>
    <p>My name is [Your Name] and I'm learning Git!</p>
</body>
</html>
```

</details>

<details>
    <summary>Walkthrough Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/aYRQ2J2oHwc" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>
