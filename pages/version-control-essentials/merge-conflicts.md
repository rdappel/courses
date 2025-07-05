---
title: Handling Merge Conflicts
subtitle: Version Control Essentials
hideNav: false

live: https://fvtc.software/appel/version-control-essentials/merge-conflicts
dev: http://localhost:3006/appel/version-control-essentials/merge-conflicts
repo: https://github.com/rdappel/courses
---

# Handling Merge Conflicts

As you saw in the previous section, pulling changes from a remote repository can sometimes lead to merge conflicts. A merge conflict occurs when two people make changes to the same line of code in a file, and Git doesn't know which change to keep.
In this section, we will spend some time learning how to handle merge conflicts.

This video will show you how to handle merge conflicts in Visual Studio Code:

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

Here is the lorem text that I used in the video to create a merge conflict:

```text
Laudantium reiciendis impedit voluptate repudiandae dolorum voluptatibus minima nisi laborum recusandae, atque ullam enim est? Consequatur provident quia temporibus, accusantium labore incidunt sequi eius quae soluta blanditiis doloremque maiores, quam maxime animi, saepe omnis. A cum dolor amet expedita minima beatae cumque voluptatem eveniet perspiciatis deleniti, dolorum aliquam ea, alias autem quis hic debitis? Quidem, debitis alias est quod, nulla error iste modi explicabo voluptatem expedita ut molestias illum quibusdam repudiandae dolorum possimus omnis.
```

The code to resolve a merge conflict in Visual Studio Code is as follows:
```bash
git add .
git commit -m "Added lorem text"
git push # this code will fail!

# resolve the merge conflict in Visual Studio Code, then run:
git add .
git commit -m "Merged keeping both changes"
git push # this code will succeed!
```

## Example with VS Code Source Control

If you are using Visual Studio Code, you can also resolve merge conflicts using the Source Control panel. This video will show you how to do that:

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

# Exercise 2

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

For this exercise, you will simply submit your commit history to demonstrate that you have successfully resolved a merge conflict.

1. **Navigate to your repository**: Open your browser and navigate to the remote repository you created for demo1.

2. **Locate the commit history**: Click on the "Commits" tab to view the commit history of your repository. It's located on the right side of the repository page, just above the file list.

![Commit History](https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/vce/commit-history-link.png)


3. **Copy the URL**: Copy the URL of the commit history page from your browser's address bar. It should look something like this: `https://github.com/your-username/your-repo/commits/main`.

## Submission {#exercise-2-submission}

Once you have found the commit history, you will submit the URL as your solution for this exercise.

<div data-language="bash" class="exercise-submission">
    <textarea placeholder="Paste your code here..."></textarea>
    <button type="button" class="submit-button">Submit Exercise</button>
</div>
