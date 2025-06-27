---
title: Cloning and Forking Repositories
subtitle: Version Control Essentials
hideNav: false

live: https://fvtc.software/appel/version-control-essentials/remote-repos
dev: http://localhost:3006/appel/version-control-essentials/remote-repos
repo: https://github.com/rdappel/courses
---

# Cloning a Repository

Cloning is the process of creating a copy of a remote repository onto your local machine, so you can work on it.

In this video, we will walk through the process of cloning a repository from GitHub:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/W4v6Npok_t0" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

The command to clone a repository is:

```bash
git clone <remote-url>
```

# Forking a Repository

Forking is the process of creating a copy of a remote repository on your GitHub account. This allows you to make changes to the repository without affecting the original repository. Forking is commonly used in open-source projects, where you want to contribute to a project but don't have write access to the original repository.

In this video, we will walk through the process of forking a repository on GitHub:

> [!NOTE] If you want to follow along, the repository we are forking is [js-movie-api](https://github.com/fvtc/js-movie-api).

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/CQwpjpz89Ps" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# Deleting a Remote Repository

If you need to delete a remote repository, you can do so from the repository page on GitHub. Click on the "Settings" tab, scroll down to the "Danger Zone" section, and click on the "Delete this repository" button.

There will be a confirmation dialog that asks you to type the name of the repository to confirm that you want to delete it. 

In the video below, I will show you how to delete a remote repository:

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/WY3l6UsSFng" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

# Exercise 2

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/yJkrGMJZxpU" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

For this exercise, you will need to fork and clone the following repository:

- [vce-forking-exercise](https://github.com/fvtc/vce-forking-exercise)

Once you have forked and cloned the repository, open the `index.html` file in your browser. You should see some 3d text that says "VCE".

Next, open the `index.html` file in your text editor and change where it says "VCE" to your name (it should be on line 14).

Save the file and go back to your browser. Refresh the page and you should see your name displayed on the page.

Finally, push your changes to GitHub, and submit the url of your forked repository below.

## Hints {#exercise-2-hints}

<details>
	<summary>How do I fork a GitHub repository?</summary>

To fork a repository, go to the repository page on GitHub and click the "Fork" button in the top right corner. This will create a copy of the repository on your GitHub account.

</details>

<details>
	<summary>How do I get a remote repository onto my local machine?</summary>

To clone a repository, go to the repository page on GitHub and click the "Code" button.

Copy the URL and run the following command in Git Bash:

```bash
git clone <url>
```

</details>

<details>
	<summary>How do I push my changes to GitHub?</summary>

To push your changes to GitHub, run the following commands in Git Bash:

```bash
git add .

git commit -m "Finished Exercise 2"

git push
```

</details>

## Submission {#exercise-2-submission}

Once you have completed the exercise, copy the URL of your forked repository and paste it into the text area below. Then click the "Submit Exercise" button.

<div data-language="plaintext" class="exercise-submission">
	<textarea placeholder="Paste your code here..."></textarea>
	<button type="button" class="submit-button">Submit Exercise</button>
</div>

## Solution {#exercise-2-solution}

<details>
	<summary>Walkthrough Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/_qdOPhXKFA8" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>
