---
title: Branching and Feature Development Workflow
subtitle: Version Control Essentials
hideNav: false

live: https://fvtc.software/appel/version-control-essentials/branching
dev: http://localhost:3006/appel/version-control-essentials/branching
repo: https://github.com/rdappel/courses
---

# Branching and Development Workflow

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

## Development Branch Workflow

In professional development, it's common to avoid working directly with the master branch. Instead, you typically work with a `dev` (development) branch and create feature branches from there.

Here's the recommended workflow:

### Initial Setup

1. **Create a dev branch** from master:

```bash
git checkout -b dev
```

2. **Push the dev branch** to your remote repository:

```bash
git push -u origin dev
```

### Feature Development

1. **Create feature branches from dev** (not master):

```bash
git checkout dev
git checkout -b feature/new-feature
```

2. **Work on your feature** and commit changes to the feature branch.

3. **When ready to merge**, use the cautious approach:

   - First, merge dev into your feature branch:
   ```bash
   git checkout feature/new-feature
   git merge dev
   ```

   - Resolve any conflicts in the feature branch, not in dev.

   - Test thoroughly to ensure everything works.

   - Then merge the feature branch into dev:
   ```bash
   git checkout dev
   git merge feature/new-feature
   ```

### Releasing to Master

When dev is stable and ready for release:

1. **Merge dev into master**:

```bash
git checkout master
git merge dev
```

2. **Tag the release** (optional but recommended):

```bash
git tag -a v1.0.0 -m "Release version 1.0.0"
```

This approach keeps master as a stable release branch, dev as your main development branch, and feature branches for individual features.


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

- **Use the development branch workflow**: Create feature branches from dev, not master

- **Keep master stable**: Only merge into master when ready for release

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

3. **Commit your initial file** to master

4. **Create a dev branch** from master:

```bash
git checkout -b dev
```

5. **Create a feature branch** for adding a navigation menu (from dev):

```bash
git checkout -b feature/navigation
```

6. **Add a navigation menu** to your HTML file (inside the `<body>` tag, before the `<h1>`):

```html
<nav>
    <ul>
        <li><a href="#home">Home</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#contact">Contact</a></li>
    </ul>
</nav>
```

7. **Commit your navigation changes** to the feature branch

8. **Merge your changes back to dev** using the cautious approach (merge dev into feature first, then feature into dev)

9. **Create another feature branch** for adding a footer (from dev):

```bash
git checkout dev
git checkout -b feature/footer
```

10. **Add a footer** to your HTML file (before the closing `</body>` tag):

```html
<footer>
    <p>&copy; 2025 My Website. All rights reserved.</p>
</footer>
```

11. **Commit your changes**

12. **Merge the footer changes back to dev** using the cautious approach

13. **Finally, merge dev into master** when everything is stable:

```bash
git checkout master
git merge dev
```

## Hints {#exercise-1-hints}

<details>
    <summary>How do I create a feature branch from dev?</summary>

First make sure you're on the dev branch, then create the feature branch:

```bash
git checkout dev
git checkout -b feature/branch-name
```

</details>

<details>
    <summary>How do I do the cautious merge approach?</summary>

To merge a feature branch into dev:

1. First merge dev into your feature branch:
```bash
git checkout feature/branch-name
git merge dev
```

2. Resolve any conflicts, then merge feature into dev:
```bash
git checkout dev
git merge feature/branch-name
```

</details>

## Submission {#exercise-1-submission}

Once you have completed the exercise, run `git log --oneline` to see your commit history. Copy the output and paste it into the text area below.

<div data-language="bash" class="exercise-submission">
    <textarea placeholder="Paste your code here..."></textarea>
    <button type="button" class="submit-button">Submit Exercise</button>
</div>

## Solution {#exercise-1-solution}

<details>
    <summary>Show the Answer</summary>
    
Your git log output should look something like this:

```bash
a1b2c3d Merge branch 'dev' (final merge to master)
e4f5g6h Add footer
i7j8k9l Add navigation menu
m1n2o3p Create dev branch
p4q5r6s Initial commit with basic HTML
```

The exact commit hashes will be different, but you should see the progression showing:

- Initial commit on master

- Development work on dev and feature branches

- Final merge from dev to master


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
