---
title: Assignment 4 - Merge Conflict
subtitle: Version Control Essentials
hideNav: false

live: https://fvtc.software/appel/version-control-essentials/assignments/merge-conflict
dev: http://localhost:3006/appel/version-control-essentials/assignments/merge-conflict
repo: https://github.com/rdappel/courses
---

# Assignment 4 - Merge Conflict

For this assignment, you will work with a partner to create a merge conflict and resolve it.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/vUaRNbRK910" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

# Instructions

## Part 1: Create a Repository

To get started, you will need to create a new repository on GitHub and add some basic content to it.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/n0B8DiwQx2Q" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

Follow these steps to create your repository and add content:

1. **Create a new project**: Create a new folder for this assignment and call it `your-name-assignment-4`. For example, `john-doe-assignment-4`.

2. **Create an index.html file**: Inside your project folder, create a file called `index.html`. This file will contain the code that you and your partner will work on.

3. **Add some content**: Add some basic HTML content to the `index.html` file. You can use the following code as a starting point:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Assignment 4 - Merge Conflict</title>
</head>
<body>
    <h1></h1>
    <p>This is a simple HTML file for the merge conflict assignment.</p>
</body>
</html>
```

4. **Add your name**: Replace the `<h1></h1>` tag with your name. For example, `<h1>John Doe</h1>`. Then save your changes and view the file in your web browser to ensure it displays correctly.

5. **Push your code to GitHub**: Using what you've learned over the past couple of weeks, initialize your project as a Git repository, commit your changes, and push the code to a new remote repository on GitHub. Make sure to name the repository something like `your-name-merge-conflict`, or `your-name-assignment-4`.

## Part 2: Find a Partner

Your partner will modify your project by adding their name and some information about themselves.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/YUso6HSfGFc" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

Follow these steps to find a partner and collaborate:

1. **Find a partner**: There is a [Teams channel](https://teams.microsoft.com/l/channel/19%3Aaa6ad81494264deba8b288e24f4091de%40thread.tacv2/Find%20a%20Partner?groupId=db69ef1e-3c6a-4ac8-8636-f800a33a72ab&tenantId=ae888c53-4d60-47da-a75a-c8a10f1d47b0) for this course where you can find a partner. Make sure to specify that you are looking for a partner for Assignment 4.

2. **Exchange repositories**: Once you find a partner, you will need to add them as a collaborator to your repository on GitHub. To do this, go to your repository on GitHub, click on "Settings", then "Manage access", and invite your partner by their GitHub username or email address.

3. **Clone your partner's repository**: After your partner has added you as a collaborator, clone their repository to your local machine.

4. **Modify the index.html file**: Open the `index.html` file in your partner's repository and create a new `<h1>` tag with your name, and add a paragraph below it with some text about yourself. For example:

```html
<h1>Jane Doe</h1>
<p>Hello, my name is Jane Doe and I like to read.</p>
```

5. **Commit and push your changes**: Save your changes, commit them with a message like "Added my name and info", and push the changes to your partner's remote repository.

## Part 3: Create and Resolve a Merge Conflict

Now that your partner has made changes to your project, it's time to create and resolve a merge conflict.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/DnwnhDW1OoY" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

Follow these steps to create and resolve a merge conflict:

> [!IMPORTANT] Do not `pull` your partner's changes before creating the merge conflict. You will be creating a conflict intentionally, so you need to have your own local copy of the repository with your changes before proceeding. 

1. **Create a merge conflict**: Look at the changes your partner made in your project. Specifically take note of the line numbers which were modified. Now, go back to your own local copy of the repository and make a conflicting change to the same line in the `index.html` file. For example, you could add an image, or a link to your favorite website.

2. **Attempt to push your changes**: After making your changes, try to commit and push them to your repository. You should encounter a merge conflict error message indicating that your changes cannot be pushed because they conflict with the changes made by your partner.

3. **Find the conflict**: Use `git pull` to retrieve your partner's changes. This will create a merge conflict in your local repository. Open the `index.html` file in a text editor or IDE, and you will see the conflicting sections marked with `<<<<<<< HEAD`, `=======`, and `>>>>>>>`.

4. **Resolve the merge conflict**: Edit the `index.html` file to resolve the conflict. You can choose to keep both changes, or select one over the other. Make sure to remove the conflict markers (`<<<<<<<`, `=======`, and `>>>>>>>`) after resolving the conflict. For example, you might end up with something like this:

```html
<p>Here is my favorite movie: <a href="https://example.com">Ryan's favorite movie</a>.</p>

<h1>Jane Doe</h1>
<p>Hello, my name is Jane Doe and I like to read.</p>
```

5. **Commit the resolved changes**: Once the merge conflict is resolved, save the file, stage the changes, and commit them with a message like "Resolved merge conflict".

6. **Push the resolved changes**: Finally, push your changes to your remote repository. This should succeed without any errors.

# Submission

Once you have successfully resolved the merge conflict and pushed your changes, you will submit the URL of BOTH your repository and your partner's repository as your solution for this assignment.
