---
title: Command Line Navigation
subtitle: Version Control Essentials
hideNav: false

live: https://fvtc.software/appel/version-control-essentials/intro-to-git
dev: http://localhost:3006/appel/version-control-essentials/intro-to-git
repo: https://github.com/rdappel/courses
---

# Navigating the Command Line

Before we start using Git, let's take a moment to look at some basic commands you will need to know to navigate the command line. The command line interface (CLI) is a text-based interface that allows you to interact with your computer using commands.

If you are using MacOS or Linux, use the Terminal. If you are using Windows, use the Command Prompt. If you are using Visual Studio Code, you can use the integrated terminal.

> [!NOTE] If you have experience using command line tools, specifically `ls/dir`, `cd`, and `mkdir`, you can skip directly to [Exercise 1](#exercise-1).

Here are some basic commands you will need to know:

- `ls/dir`: List the files and folders in the current directory (folder). The command prompt uses `dir` and the terminal uses `ls`, but for the most part they work the same way.

- `cd`: Change directories. For example, `cd MyProject` will take you to the myProject folder, assuming it exists in the current directory. You can also use `cd ..` to go up to the parent directory, or `cd ~` to go to your home/user directory. You can also combine them with slashes to navigate to a specific directory, such as `cd ~/../Joe/Desktop`, which will take you to the Desktop folder for the user Joe (assuming that user exists).

- `mkdir`: Make a new directory. For example, `mkdir MyProject` will create a new folder called MyProject in the current directory.

> [!NOTE] The terms "directory" and "folder" are synonymous. I will be using them interchangeably throughout this course.

In this video we will see these commands in action:

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

Perform the following tasks:

1. Open up your terminal and navigate to your desktop.

2. Create a new directory called `Exercise1`.

3. Show the files and folders in the current directory, to confirm that the folder was created.

4. Navigate into the `Exercise1` directory.

## Hints {#exercise-1-hints}

<details>
    <summary>How do I create a new folder?</summary>

Use the `mkdir` command followed by the name of the folder that you want to create. For example, `mkdir MyFolder` will create a new folder called MyFolder:

```bash
mkdir MyFolder
```

</details>

<details>
    <summary>How do I navigate into a folder?</summary>

Use the `cd` command followed by the name of the folder that you want to navigate into. For example, `cd MyFolder` will take you into the MyFolder folder:

```bash
cd MyFolder
```

</details>

<details>
    <summary>How do I list the files and folders in the current directory?</summary>

Use the `dir` command on the Windows command prompt:

```bash
dir
```

Or, use the `ls` command on the terminal:

```bash
ls
```

</details>

## Submission {#exercise-1-submission}

Once you have completed the exercise, copy the commands you used to complete the exercise and paste them into the text area below. Then click the "Submit Exercise" button.

<div data-language="bash" class="exercise-submission">
    <textarea placeholder="Paste your code here..."></textarea>
    <button type="button" class="submit-button">Submit Exercise</button>
</div>


## Solution {#exercise-1-solution}

> [!NOTE] Your instructor can see if you view the solution before submitting your answer, so please try to solve the exercise on your own first.

<details>
    <summary>Show the Answer</summary>

Here are the commands you need to complete the exercise:

```bash
cd Desktop
mkdir Exercise1
ls
cd Exercise1
```

Note that the `ls` command will need to be replaced with `dir` if you are using the command prompt on Windows.

</details>

<details>
    <summary>Walkthrough Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>



