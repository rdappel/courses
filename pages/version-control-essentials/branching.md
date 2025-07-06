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

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

## What is a Branch?

Think of branches like parallel universes for your code. You can work on different features or fixes in different branches without them interfering with each other. When you're satisfied with the changes in a branch, you can merge it back into the main branch.

## Why Use Branches?

- **Isolation**: Work on new features without breaking the main codebase

- **Collaboration**: Multiple developers can work on different features simultaneously

- **Experimentation**: Try new ideas without risk

- **Organization**: Keep different types of work separate (features, bug fixes, experiments)

## Creating and Switching Branches

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
git branch feature-branch
```

This creates a new branch called `feature-branch`, but you're still on your current branch. To switch to the new branch, use:

```bash
git checkout feature-branch
```

You can also create and switch to a new branch in one command:

```bash
git checkout -b feature-branch
```

## Viewing Branches

To see all the branches in your repository, use:

```bash
git branch
```

This will show all local branches, with an asterisk (*) next to the current branch. To see remote branches as well, use:

```bash
git branch -a
```

## Making Changes on a Branch

Once you're on a branch, you can make changes just like you normally would:

1. Edit your files

2. Stage your changes: `git add .`

3. Commit your changes: `git commit -m "Add new feature"`

These commits will only exist on your current branch and won't affect other branches.

## Merging Branches

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

When you're ready to incorporate changes from one branch into another, you use the `git merge` command. However, it's important to be cautious when merging, especially when merging into your main branch.

### The Cautious Approach to Merging

Here's a safer approach to merging branches. Let's say you have a `dev` branch that you want to merge into `master`:

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

## Merge Conflicts

Sometimes Git can't automatically merge branches because the same lines of code have been changed in both branches. This creates a merge conflict.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

When a merge conflict occurs, Git will mark the conflicting sections in your files:

```plaintext
<<<<<<< HEAD
Your current branch's changes
=======
The other branch's changes
>>>>>>> branch-name
```

To resolve the conflict:

1. **Edit the file** to keep the changes you want
2. **Remove the conflict markers** (`<<<<<<<`, `=======`, `>>>>>>>`)
3. **Stage the resolved file**: `git add filename`
4. **Commit the merge**: `git commit -m "Resolve merge conflict"`

## Deleting Branches

Once you've merged a branch and no longer need it, you can delete it:

```bash
git branch -d branch-name
```

If the branch hasn't been merged and you want to force delete it:

```bash
git branch -D branch-name
```

## Common Branching Strategies

### Feature Branches

Create a new branch for each feature you're working on:

```bash
git checkout -b feature/user-authentication
```

### Bug Fix Branches

Create branches for bug fixes:

```bash
git checkout -b bugfix/fix-login-issue
```

### Release Branches

Some teams use release branches for preparing releases:

```bash
git checkout -b release/v1.2.0
```

## Best Practices

- **Use descriptive branch names**: `feature/user-login` is better than `new-stuff`

- **Keep branches focused**: One feature or fix per branch

- **Merge or delete branches promptly**: Don't let branches get stale

- **Test before merging**: Always test your changes before merging into main branches

- **Use the cautious merge approach**: Merge main into feature first, then feature into main

## Working with Remote Branches

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

When working with remote repositories, you'll often need to push your branches to the remote:

```bash
git push origin branch-name
```

To set up tracking so you can just use `git push` in the future:

```bash
git push -u origin branch-name
```

To pull changes from a remote branch:

```bash
git pull origin branch-name
```

## Viewing Branch History

To see the commit history of branches in a visual format:

```bash
git log --oneline --graph --all
```

This shows a nice graph of your branch history and merges.

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

1. **Create a new project folder** and initialize it as a Git repository:

```bash
mkdir branching-practice
cd branching-practice
git init
```

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

3. **Commit your initial file**:

```bash
git add index.html
git commit -m "Initial commit with basic HTML"
```

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

6. **Commit your changes**:

```bash
git add index.html
git commit -m "Add navigation menu"
```

7. **Switch back to master** and merge your changes using the cautious approach:

```bash
git checkout master
git merge feature/navigation
```

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

10. **Commit your changes**:

```bash
git add index.html
git commit -m "Add footer"
```

11. **Switch back to master and merge the footer**:

```bash
git checkout master
git merge feature/footer
```

12. **Clean up by deleting the feature branches**:

```bash
git branch -d feature/navigation
git branch -d feature/footer
```

## Hints {#exercise-1-hints}

<details>
    <summary>How do I check which branch I'm on?</summary>

You can check your current branch with:

```bash
git branch
```

The current branch will have an asterisk (*) next to it.

</details>

<details>
    <summary>How do I see my commit history?</summary>

You can see your commit history with:

```bash
git log --oneline
```

This shows a condensed view of your commits.

</details>

<details>
    <summary>What if I make a mistake?</summary>

If you make a mistake and want to undo your last commit (but keep the changes in your working directory):

```bash
git reset --soft HEAD~1
```

If you want to completely undo your last commit and lose the changes:

```bash
git reset --hard HEAD~1
```

</details>

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
