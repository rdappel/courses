---
title: Assignment 8 - Game Analysis
subtitle: Computer Programming C++
hideNav: false

live: https://fvtc.software/appel/computer-programming-cpp/assignments/game-analysis
dev: http://localhost:3006/appel/computer-programming-cpp/assignments/game-analysis
repository: https://github.com/rdappel/courses
---

# Assignment 8 - Game Analysis

For this assignment, you will explore the code for a shoot-em-up game written in C++. The game is a simple 2D shooter where the player controls a spaceship and shoots at enemy ships. The game uses a graphics library called [Allegro](https://liballeg.org/), though most of that code is abstracted from you.

The purpose of this assignment is to prepare you for the final project, where you will be creating a modification of this game. You will need to understand parts of the code in order to make changes to it.

This video will help you get the repository set up and running in Visual Studio:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/wxEhWdglgts" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Start by creating a fork of the game's repository.

I want want you to give the repository a name that includes the words "space-fighter-analysis". You might need to create another fork later, for your group project, so make sure you can tell the difference between the two.

```plaintext
space-fighter-analysis
```

The repository is located here: [cpp-space-fighter](https://github.com/FVTC/cpp-space-fighter)

After you have the repository forked, clone it to your computer and open it in Visual Studio. Then try to build and run the project.

Depending on your version of Visual Studio, you may need to make some changes to the project settings. There are some instructions in the README file of the repository that will help you with this. If you have any trouble, please ask for help.

The README file also has a image of the project structure, called a Class Diagram, or UML diagram. This diagram shows the classes and their relationships in the project. It will help you understand how the game is structured.

You can also view the complete documentation for the project here: [cpp-space-fighter-docs](https://docs.shurikenstudios.com/katana-engine/)

# Explore the Code

Once you have the project running, take some time to explore the code. You will need to understand how the game works in order to make changes to it.

First, notice that the solution is broken up into two projects: `SpaceFighter` and `KatanaEngine`. The `SpaceFighter` project is the game itself, while the `KatanaEngine` project is a library that has classes that can be reused in other games.

In the following videos, I will cover some of the important concepts in the code:

## Game Loop

A game loop is a way to structure a game so that it runs continuously. The game loop is responsible for updating the game state and rendering the game to the screen.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/SF8h0cOZzxw" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Classes covered in the video:

- `GameplayScreen`

- `Level`

- `PlayerShip`

- `GameObject`

## Sprite Batching

Sprite batching is a technique used to improve the performance of a game. It involves drawing multiple sprites at once, instead of drawing each sprite individually.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/BsLyn9hA-mc" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Classes covered in the video:

- `SpriteBatch`

- `Level`

## Screens and Screen Manager

The game is divided into different screens, such as the main menu, and the gameplay screen. The screen manager is responsible for managing these screens.

If you're familiar with Photoshop or other graphic design software, you can think of the screens as layers that are stacked on top of each other. The screen manager is like the layer manager that allows you to keep track of which layer (or layers) are currently visible.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/_Y00xjMljlA" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Classes covered in the video:

- `ScreenManager`

- `GameplayScreen`

- `MainMenuScreen`

## Resources and Resource Manager

The game uses resources, sometimes called assets, such as images, sounds, fonts, and text files. The resource manager is responsible for loading and managing these resources.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/jaRT6prlx_g" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Classes covered in the video:

- `ResourceManager`

- `Level01`

- `Level`

> [!NOTE] The resouces are stored in the `Content` folder of the `SpaceFighter` project.

# Additional Concepts

In the next unit, there will be more videos that cover additional concepts in the code. You will not be required to watch all of the videos, but you may find them helpful as you work on your final project. For example, if your group decides to add power-ups to the game, you may want to watch the video on how collisions work.

# Assignment Instructions

For this assignment, you will make some minor changes to your fork of the game. You will need to make the following changes:

1. Change the color and the font of the menu items on the main menu screen.

2. Change the speed of the player's ship.

3. Play around with the calculations for the Bio Enemy ship's movement. Try to make it move in a different pattern.

4. When a ship is destroyed, print a debug message to the console.

5. When "Start Game" is selected on the main menu, load Level 2 instead of Level 1.

6. Add a background image to Level 2. There are a few images in the `Content` folder that you can use, or you can find your own.

## Getting Help

If you're struggling with any of these changes, it's okay to ask your teammates for help. Please make sure to give an earnest effort before asking them.

# Submission

When you have completed the assignment, push your changes to your fork of the repository. Then, submit the url of your repository in Blackboard.