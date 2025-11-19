---
title: Getting Started
subtitle: Version Control Essentials
hideNav: false

live: https://fvtc.software/appel/version-control-essentials/getting-started
dev: http://localhost:3006/appel/version-control-essentials/getting-started
repo: https://github.com/rdappel/courses
---

# Getting Started

As a software developer, or a web developer, you will be working on projects that involve multiple files and multiple people. Keeping track of changes, managing versions, and collaborating with others can be a challenge. This is where version control comes in.

By far the most popular version control system is [Git](https://git-scm.com/). Git is a free, open-source version control system that was created by Linus Torvalds, the creator of Linux. It is used by many large companies, including Microsoft, Google, Facebook, and Twitter.

## Is Git Already Installed?

You can quickly check to see if git is installed on your computer, and which version. Simply open a terminal (or command prompt) and type the following command:

```bash
git --version
```

If you see a version number, then Git is already installed on your computer. If you see an error message or if your version is less than 2.0, you will need to install Git.

## Installing Git

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/KfoGSWYFYH4" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

To install Git, go to [https://git-scm.com/downloads](https://git-scm.com/downloads) and download the version for your operating system. If you are using Windows, you will need to install Git Bash, which is a terminal that allows you to run Git commands.

# Local Repositories

A local repository is a repository that is stored on your computer. This allows you to keep track of changes to your code.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/7LL7_XxCdB8" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Initializing a Repository

To create a local repository, open a terminal and navigate to the directory where you want to store your code. Then, run the following command:

```bash
git init
```

> [!NOTE] You only need to run this command once per repository. If you have cloned a repository from a remote repository, you do not need to run this command.

This will create a new directory called `.git` in your current directory. This directory contains all of the information about your repository, including the history of changes to your code.

## Staging Changes

Before you can commit changes to your repository, you need to stage them. This tells Git which files you want to commit. To stage a file, run the following command:

```bash
git add <file>
```

You can also stage all of the files in your repository by running the following command:

```bash
git add .
```

## Committing Changes

Once you have staged your changes, you can commit them to your repository. To commit your changes, run the following command:

```bash
git commit -m "Commit message"
```

The commit message should be a short description of the changes you are committing. For example, if you are fixing a bug, you might use the following commit message:

```bash
git commit -m "Fix bug #1234"
```

# Remote Hosting

A remote repository is a repository that is hosted on a server. This allows multiple people to work on the same project at the same time. GitHub, Bitbucket, and Azure DevOps are all examples of remote repositories. Depending on your instructor, you will be using one of these services to submit your assignments.

This video will show you how to create a repository on GitHub, Bitbucket, and Azure DevOps. The process is very similar for all three services.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/asMNJ8uJFws" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Pushing Code to GitHub

Even if you're not using GitHub for your class, watch this video because the process is very similar for all three services.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/wsYSY6553gc" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

To push your code to GitHub, you need to add a remote repository. To do this, run the following command:

```bash
git remote add origin <url>
```
> [!NOTE] This line is displayed in the GitHub repository when you create it, so you can copy and paste it.

Then, push your code to GitHub by running the following command:

```bash
git push -u origin main
```

> [!NOTE] If your branch is called `master`, just replace `main` with `master`.

## Pushing Code to Bitbucket

The process for pushing code to Bitbucket is very similar to pushing code to GitHub. But there is an additional step! You will need an App Password to push code to Bitbucket. In this video, I will walk you through how to do this.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/ysCr09d1alc" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Pushing Code to Azure DevOps

Again, the process for pushing code to Azure DevOps is very similar to pushing code to GitHub. In this video, I will walk you through how to do this.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/Edk4rCBZzr0" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Subsequent Pushes

After you have pushed your code to one of these services, if you make any changes to your code, you can push them by running the following commands.

First stage your changes:

```bash
git add .
``` 

Then commit your changes:

```bash
git commit -m "New code added!"
```

Finally, push your changes:

```bash
git push
```