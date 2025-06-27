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
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

> [!TIP] Remember to keep the repository page open in your browser. We will be using a couple of the commands that it provides for pushing up a project.

# Pushing to a Remote Repository

Once you have created a remote repository, you can push your local changes to the remote repository. This allows you to share your code with others and collaborate on projects.

Mac users will need to create a Personal Access Token (PAT) in GitHub to authenticate with the remote repository. Windows users will be prompted to log in using their browser, which is the recommended method.

The following videos will walk you through the installation process. Choose the corresponding video for your operating system:

<details>
    <summary class="video">Windows</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

<details>
    <summary class="video">Mac</summary>
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