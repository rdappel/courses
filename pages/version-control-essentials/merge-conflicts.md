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

This video will show you how to handle merge conflicts:

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/7pDFDf3l7PI" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

Here is the lorem text that I used in the video to create a merge conflict:

```text
Laudantium reiciendis impedit voluptate repudiandae dolorum voluptatibus minima nisi
laborum recusandae, atque ullam enim est? Consequatur provident quia temporibus,
accusantium labore incidunt sequi eius quae soluta blanditiis doloremque maiores,
quam maxime animi, saepe omnis. A cum dolor amet expedita minima beatae cumque
voluptatem eveniet perspiciatis deleniti, dolorum aliquam ea, alias autem quis hic
debitis? Quidem, debitis alias est quod, nulla error iste modi explicabo voluptatem
expedita ut molestias illum quibusdam repudiandae dolorum possimus omnis.
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

# Git with VS Code

If you are using Visual Studio Code, you can also resolve merge conflicts using the Source Control panel. This video will show you how to do that:

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/d8gAJZNxcRU" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

# Git with Visual Studio

Visual Studio also has built-in support for Git, meaning that you can do all of the same things that you can do in Visual Studio Code.

This video will show you how to clone a repository directly in Visual Studio:

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

As you can see, cloning a repository in Visual Studio is pretty straightforward. You can also use Visual Studio to commit, push and pull changes, and resolve merge conflicts, as shown in this video:

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

As mentioned in the video, the merge tool in Visual Studio is really powerful. It allows you to see the changes made by both parties side-by-side, and quickly choose which to keep.

# Exercise 2

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

For this exercise, you will practice resolving merge conflicts using Visual Studio Code. You will need to create a merge conflict in your own repository, and then resolve it using the steps outlined in this section.

1. **Create a merge conflict**: Choose a file in one of your repositories and make a change to it in your browser. Then, open the same file in Visual Studio Code (or Visual Studio) and make a different change to the same line of code.

2. **Pull the changes**: In Visual Studio Code (or Visual Studio), pull the changes from the remote repository. This will create a merge conflict.

3. **Resolve the merge conflict**: Use the steps outlined in this section to resolve the merge conflict. Make sure to keep both changes, and commit the changes to your repository.

4. **Push the changes**: After resolving the merge conflict, push the changes to your remote repository.

## Submission {#exercise-2-submission} 

Once you have completed the exercise, you will need to submit your commit history to show that you have resolved the merge conflict.

If you are using GitHub, navigate to your repository, click on the "Commits" link, shown below.

![Commit History Link - GitHub](https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/vce/commit-history-link-github.png)

If you are using Azure DevOps, make sure that you have the correct repository selected, then click on the "Commits" link in the left-hand menu, as shown below.

![Commit History Link - DevOps](https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/vce/commit-history-link-devops.png)

Once you have the commit history open, copy the URL from your browser's address bar and paste it into the submission box below.

<div data-language="bash" class="exercise-submission">
    <textarea placeholder="Paste your code here..."></textarea>
    <button type="button" class="submit-button">Submit Exercise</button>
</div>

## Solution {#exercise-1-solution}

<details>
    <summary>Walkthrough Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/3YSREV4RrN4" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>