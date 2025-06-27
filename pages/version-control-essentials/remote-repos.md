---
title: Remote Repositories
subtitle: Version Control Essentials
hideNav: false

live: https://fvtc.software/appel/version-control-essentials/remote-repos
dev: http://localhost:3006/appel/version-control-essentials/remote-repos
repo: https://github.com/rdappel/courses
---

# Remote Repositories

In the previous sections, we learned how to create a local repository and make changes to it. In this section, we will learn how to create a remote repository in GitHub, and push our code to it.

# Creating a Remote Repository

Creating a remote repository is different depending on the hosting service and the environment you are using. For example, if you're using Git Bash to push a repository to GitHub the process is very different than if you're pusing a Visual Studio project to Azure DevOps.

We will cover both of these processes (and more) in upcoming sections.

For now, let's take a look at how to create a remote repository on GitHub:

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/gcPF4p3lAj8" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

> [!TIP] Remember to keep the repository page open in your browser. We will be using a couple of the commands that it provides for pushing up a project.

# Pushing to a Remote Repository

Once you have created a remote repository, you can push your local changes to the remote repository. This allows you to share your code with others and collaborate on projects.

Mac users will need to create a Personal Access Token (PAT) in GitHub to authenticate with the remote repository. Windows users will be prompted to log in using their browser, which is the recommended method.

The following videos will walk you through the installation process. Choose the corresponding video for your operating system:

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/ju-u3343L-A" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

<details>
    <summary class="video">Creating a PAT (Mac)</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

The commands we ran were:

```bash
git init

git add .

git commit -m ":tada: first commit"
```

The commands that were copy/pasted from GitHub:

```bash
git remote add origin <url>

git push -u origin master
```

> [!NOTE] You don't need to memorize these last two commands, because you can always copy them from the remote repository page. Remember that `Ctrl` + `V` will not work in Git Bash. Instead, right-click in the terminal and select "Paste" from the context menu.

## Pushing Changes to a Repository

Once you have pushed your local repository to a remote repository, you can push changes to the remote repository as you make them. This allows you to share your code with others and collaborate on projects.

The process is different than your initial push because your local repo is already connected to the remote repo.

This video will show you how to push changes to GitHub:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

The text that I used for the README file was:


```markdown
# Demo Repository

🚀 This is a demo repository for the Version Control Essentials course.

🧠 README files are used to provide information about the project, such as how to install it, how to use it, and how to contribute to it.

🔻 You can use Markdown to format your README file. Markdown is a lightweight markup language that allows you to write formatted text using plain text syntax. You can learn more about Markdown at [https://www.markdownguide.org/](https://www.markdownguide.org/).
```

The commands we ran were:

```bash
git add .

git commit -m ":memo: added readme"

git push
```

Then the next update was:

```bash
git add .

git commit -m ":sparkles: added git commands"

git push
```

# Exercise 1

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

For this exercise, you will add a comment to your index.html file, commit the changes, and push them to your remote repository.

If you haven't used comments in HTML before, you can read up on them on w3schools: [HTML Comments](https://www.w3schools.com/html/html_comments.asp).

Once you have added your comment, create a commit with a message that describes the change you made. Then, push your changes to your remote repository.

The [Gitmoji](https://gitmoji.dev/) website recommends using the 💡 `:bulb:` emoji for adding comments to your code, so you can use that in your commit message.


## Hints {#exercise-1-hints}

<details>
    <summary>How do I push changes to my repo?</summary>

You will need to create a commit, then use the `git push` command to push your changes to the remote repository.

```bash
git add .
git commit -m "your commit message here"
git push
```

</details>

## Solution {#exercise-1-solution}

<details>
    <summary>Show the Answer</summary>

Here are the commands you need to complete the exercise:

```bash
git add .
git commit -m ":bulb: added a comment"
git push
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