---
title: Branching and Feature Development Workflow
subtitle: Version Control Essentials
hideNav: false

live: https://fvtc.software/appel/version-control-essentials/branching
dev: http://localhost:3006/appel/version-control-essentials/branching
repo: https://github.com/rdappel/courses
---

# Branching and Feature Development Workflow

Branching is one of the most powerful features of Git. It allows you to create separate lines of development within a single repository. This is incredibly useful for developing new features, fixing bugs, or experimenting with code without affecting the main codebase.

Think of branches like parallel universes for your code. You can work on different features or fixes in different branches without them interfering with each other. When you're satisfied with the changes in a branch, you can merge it back into the main branch.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

## Why Use Branches?

- **Isolation**: Work on new features without breaking the main codebase

- **Collaboration**: Multiple developers can work on different features simultaneously

- **Experimentation**: Try new ideas without risk

- **Organization**: Keep different types of work separate (features, bug fixes, experiments)

# Creating and Switching Branches

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

To create a new branch, use the `git branch` command:

```bash
git branch <branch-name>
```

This creates a new branch called `<branch-name>`, but you're still on your current branch. To switch to the new branch, use:

```bash
git checkout <branch-name>
```

You can also create and switch to a new branch in one command:

```bash
git checkout -b <branch-name>
```

# Viewing Branches

To see all the branches in your repository, use:

```bash
git branch
```

This will show all local branches, with an asterisk (*) next to the current branch. To see remote branches as well, use:

```bash
git branch -a
```

# Merging Branches

When you're ready to incorporate changes from one branch into another, you use the `git merge` command. However, it's important to be cautious when merging, especially when merging into your main branch.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

## Cautious Merge Approach

When merging branches, especially if you're working on a team or have multiple branches, it's a good idea to follow a cautious approach to avoid conflicts and ensure stability.

1. **First, merge master into dev**: This way, if there are any merge conflicts, you deal with them in the dev branch (not master).

```bash
git checkout dev
git merge master
```

2. **Resolve any conflicts** that arise during this merge in the dev branch.

3. **Test thoroughly** to make sure everything works correctly in the dev branch.

4. **Then merge dev into master**: Since you've already resolved conflicts, this should be a clean merge.

```bash
git checkout master
git merge dev
```

This approach keeps your main branch (master) stable and clean, while handling any messy conflict resolution in the development branch.


# Common Branching Strategies

## Feature Branches

Create a new branch for each feature you're working on:

```bash
git checkout -b feature/user-authentication
```

## Bug Fix Branches

Create branches for bug fixes:

```bash
git checkout -b bugfix/fix-login-issue
```

## Release Branches

Some teams use release branches for preparing releases:

```bash
git checkout -b release/v1.2.0
```

# Best Practices

- **Use descriptive branch names**: `feature/user-login` is better than `new-stuff`

- **Keep branches focused**: One feature or fix per branch

- **Merge or delete branches promptly**: Don't let branches get stale

- **Test before merging**: Always test your changes before merging into main branches

- **Use the cautious merge approach**: Merge main into feature first, then feature into main

# Exercise 1

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

For this exercise, you will practice creating branches, making changes, and merging them back together.

## Instructions

1. **Create a new project folder** called `branching-practice` and initialize it as a Git repository.

2. **Create a simple HTML file** called `index.html`:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Branching Practice</title>
</head>
<body>
    <h1>Welcome to My Site</h1>
    <p>This is the main page.</p>
</body>
</html>
```

3. **Commit your initial file**

4. **Create a new branch** for adding a navigation menu:

```bash
git checkout -b feature/navigation
```

5. **Add a navigation menu** to your HTML file (inside the `<body>` tag, before the `<h1>`):

```html
<nav>
    <ul>
        <li><a href="#home">Home</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#contact">Contact</a></li>
    </ul>
</nav>
```

6. **Commit your navigation changes** to the feature branch

7. **Merge your changes back to master** using the cautious approach (merge master into feature first)

8. **Create another branch** for adding a footer:

```bash
git checkout -b feature/footer
```

9. **Add a footer** to your HTML file (before the closing `</body>` tag):

```html
<footer>
    <p>&copy; 2025 My Website. All rights reserved.</p>
</footer>
```

10. **Commit your changes**

11. **Merge the footer changes back to master** using the cautious approach (merge master into feature first)

## Hints {#exercise-1-hints}

## Submission {#exercise-1-submission}

Once you have completed the exercise, run `git log --oneline` to see your commit history. Copy the output and paste it into the text area below.

<div data-language="bash" class="exercise-submission">
    <textarea placeholder="Paste your git log output here..."></textarea>
    <button type="button" class="submit-button">Submit Exercise</button>
</div>

## Solution {#exercise-1-solution}

<details>
    <summary>Show the Answer</summary>

Your git log output should look something like this:

```
a1b2c3d Add footer
e4f5g6h Add navigation menu
i7j8k9l Initial commit with basic HTML
```

The exact commit hashes will be different, but you should see three commits showing the progression of your work.

Your final HTML file should look like this:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Branching Practice</title>
</head>
<body>
    <nav>
        <ul>
            <li><a href="#home">Home</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
    </nav>
    <h1>Welcome to My Site</h1>
    <p>This is the main page.</p>
    <footer>
        <p>&copy; 2025 My Website. All rights reserved.</p>
    </footer>
</body>
</html>
```

</details>

<details>
    <summary>Walkthrough Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>
