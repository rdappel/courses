---
title: Assignment 2 - File I/O
subtitle: C# Intermediate Programming
hide-nav: false

live: https://fvtc.software/appel/csharp-intermediate-programming/assignments/file-io
dev: http://localhost:3006/appel/csharp-intermediate-programming/assignments/file-io
repo: https://github.com/rdappel/courses
---

# Assignment 2 - File I/O

For this assignment you’ll create a program that reads and writes text files.

<details open style="display: none;">
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/AAAAAAA" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Project Setup

Create a new Windows Forms App project in Visual Studio. Name the project `<your-initials>.FileIO.UI`, and the solution `<your-initials>.FileIO`. This will help keep your projects organized.

## Form Design

Arrange the controls to closely resemble the following image:

![Form Layout](https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/cs-intermed/file-io-running.png)


## Operation

The program should allow the user to enter text into a textbox and then save that text to a file when the "Save" menu item is selected from the file menu.

The user can also open an existing text file and display its contents in the textbox when the "Open" menu item is selected.

## Specifications

- The File menu should contain the following items:

	1. **New** - Prompts the user to save if there is unsaved text in the textbox. Clears the textbox if the user chooses to proceed.

	2. **Open** - Opens a dialog to allow the user to select an existing text file. Displays the contents of the selected file in the textbox, and shows the file path in the status bar.

	3. **Save** - Saves the contents of the textbox to the current file. If the file has not been saved before, it should open a "Save As" dialog.

	4. **Save As** - Opens a dialog to allow the user to specify a new file name and location for saving the contents of the textbox.

	5. **Exit** - Closes the application.

- The current date and time should be displayed in the status bar when the application starts.

- Use correct naming conventions for your project, solution, and all controls.

- Remember to comment your code appropriately.

# Submission

Push your code to the Azure DevOps repository and submit the URL to Blackboard.

> [!NOTE] If you don't know how to push your code to Azure DevOps, ask your instructor for assistance.