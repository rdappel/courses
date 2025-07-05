---
title: Pulling and Pushing
subtitle: Version Control Essentials
hideNav: false

live: https://fvtc.software/appel/version-control-essentials/pulling-and-pushing
dev: http://localhost:3006/appel/version-control-essentials/pulling-and-pushing
repo: https://github.com/rdappel/courses
---

# Pulling and Pushing

In this section, we will learn how to pull and push changes to a remote repository. Pulling means getting the latest changes from the remote repository, while pushing means sending your changes to the remote repository. We have actually already pushed code to a remote repository in the previous section, but we will go over it again here in greater depth.`

## Pulling Changes

Generally, you will want to pull changes from the remote repository before you start working on your code. This ensures that you have the latest version of the code and that you are not working on an outdated version.

This video will show you how to perform a pull, and cover some of the common situations when you might need to pull changes:

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

If you no longer have your demo1 repository, you can [fork my demo1 repository from GitHub](https://github.com/rdappel/demo1/fork).

Here is the command to pull changes from a remote repository:

```bash
git pull
```

## Pushing Changes

As mentioned earlier, you already pushed changes to a remote repository in the previous section. However, there are some situations where pushing changes might fail. This video will show you some of the common situations where pushing changes might fail, and how to resolve them:

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

# Using an IDE

Most IDEs have built-in support for Git, which makes it easy to pull and push changes. In this section, we will cover how to pull and push changes using Visual Studio Code. Using an IDE can speed up your workflow and make it easier to manage your code.

This video will show you how to pull and push changes using Visual Studio Code:

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

# Exercise 1

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

For this exercise, you will practice pulling changes from a remote repository.

> [!NOTE] When you pull the changes, I want you to use the command line, not an IDE.

1. In your browser, navigate to your demo1 repository on GitHub.

2. Click on the "Code" button and copy the URL of your repository.

3. Modify your index.html file, and add a paragraph with the text "Exercise 1: Pulling Changes".

4. Save the file and commit your changes with the message "Exercise 1".

5. In Git Bash or your termainal, pull the latest changes from your remote repository.

6. Verify that your changes have been pulled successfully by checking the contents of your index.html file.

7. If you encounter any issues, refer to the videos above for troubleshooting tips.

8. To submit, copy the contents of your terminal and paste them into the text area below.

## Hints {#exercise-1-hints}

<details>
    <summary>How do I pull changes from a remote repository?</summary>

To pull changes from a remote repository, you can use the following command:

```bash
git pull
```

</details>

## Submission {#exercise-1-submission}

Once you have completed the exercise, paste the contents of your terminal into the text area below. Then click the "Submit Exercise" button.

<div data-language="bash" class="exercise-submission">
    <textarea placeholder="Paste your code here..."></textarea>
    <button type="button" class="submit-button">Submit Exercise</button>
</div>

## Solution {#exercise-1-solution}

<details>
    <summary>Walkthrough Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>