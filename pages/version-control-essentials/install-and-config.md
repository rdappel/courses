---
title: Installation and Configuration
subtitle: Version Control Essentials
hideNav: false

# next:
#   title: Creating Local Repos
#   url: /appel/version-control-essentials/create-local-repos

# previous:
#   title: Home
#   url: /appel/version-control-essentials

live: https://fvtc.software/appel/version-control-essentials/install-and-config
dev: http://localhost:3006/appel/version-control-essentials/install-and-config
repo: https://github.com/rdappel/courses
---

# Downloading and Installing Git

## Is Git Already Installed?

You can quickly check to see if git is installed on your computer, and which version. Simply open a terminal (or command prompt) and type the following command:

```bash
git --version
```

If you see a version number, then Git is already installed on your computer. If you see an error message or if your version is less than 2.40, you will need to install Git.

## Installation

The following videos will walk you through the installation process. Choose the corresponding video for your operating system:

<details>
    <summary class="video">Windows 10/11</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/fey75kkPXYs" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

<details>
    <summary class="video">Mac</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/BYK5qa-LT38" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

To install Git, go to [https://git-scm.com/downloads](https://git-scm.com/downloads) and download the version for your operating system.

# User Configuration

Now that Git is installed, you need to configure it with your name and email address. This information will be used to identify you when you make changes to your code.

> [!NOTE] If you are on campus, using a school computer, this step is not necessary. Git will use your school email address and username.

This video will walk you through the process of configuring Git:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/ugbnTik03B8" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

You can use your school email address, or your personal email if you prefer.

Here is the command to set your user name:

```bash
git config --global user.name "Your Name"
```

And here is the command to set your email address:

```bash
git config --global user.email "Your Email"
```

> [!TIP] You can change your name and email address at any time by running these commands again, or by modifying the `.gitconfig` file in your home directory.

# Exercise 2

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/HbZSxgp3dro" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

> [!NOTE] `Ctrl` + `C` and `Ctrl` + `V` do not copy & paste in Git Bash! To copy text in Bash, simply highlight it with your mouse, it will automatically be copied to your clipboard. To paste text, right-click in the terminal and select "Paste" from the context menu.

Perform the following tasks:

1. Open the Desktop directory using the "Open Git Bash Here" option in the context menu.

2. Using the terminal/bash, show which version of Git you have installed.

3. Copy the commands in Bash and submit them below.

## Hints {#exercise-2-hints}

<details>
    <summary>How do I check the version of Git?</summary>

Run the following command in your terminal:

```bash
git --version
```

There is a shortcut for this command, which is `git -v`.

</details>

## Submission {#exercise-2-submission}

Once you have completed the exercise, paste the contents of your terminal into the text area below. Then click the "Submit Exercise" button.

<div data-language="bash" class="exercise-submission">
    <textarea placeholder="Paste your code here..."></textarea>
    <button type="button" class="submit-button">Submit Exercise</button>
</div>

## Solution {#exercise-2-solution}

<details>
    <summary>Show the Answer</summary>

Right-click on your desktop and select "Open Git Bash Here".

Then run the following command:

```bash
git --version
```

</details>

<details>
    <summary>Walkthrough Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/v3jJMCt05Iw" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>