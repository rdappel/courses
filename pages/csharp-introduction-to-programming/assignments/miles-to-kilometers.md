---
title: Assignment 3 - Miles to Kilometers
subtitle: C# Introduction to Programming
hide-nav: false

live: https://fvtc.software/appel/csharp-introduction-to-programming/assignments/miles-to-kilometers
dev: http://localhost:3006/appel/csharp-introduction-to-programming/assignments/miles-to-kilometers
repo: https://github.com/rdappel/courses
---

# Assignment 3 - Miles to Kilometers

For this assignment, you will create a WinForms application to convert miles to kilometers.

<details open style="display: none;">
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/AAAAAAA" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

## Project Setup

Create a new Windows Forms App project in Visual Studio. Name the project `<your-initials>.MilesToKilometers.UI`, and the solution `<your-initials>.MilesToKilometers`. This will help keep your projects organized.

## Form Design

Arrange the controls to closely resemble the following image:

![Form Layout](https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/cs-intro/miles-to-kilometers-running.png)

## Operation

1. When the user enters a value in the Miles textbox and clicks the `Convert` button, the application should convert the miles to kilometers (1 mile = 1.61 kilometers) and display the result.

2. When the user changes the value in the Miles textbox, the calculated Kilometers should be cleared.

3. When the `Clear` button is clicked, both the Miles and Kilometers fields should be cleared, and focus should return to the Miles textbox.

4. When the `Exit` button is clicked, the application should close.

## Specifications

1. Use appropriate tab sequence for all controls.

2. Set appropriate AcceptButton and CancelButton properties.

3. Right align all numeric data.

4. Focus back to the Miles textbox after displaying kilometers and when clearing the form.

5. Use correct naming conventions for your project, solution, and all controls.

6. Use appropriate variables for all numeric data.

7. Include appropriate comments in your code.

# Submission

Either show your instructor (classroom students), or push your code to the Azure DevOps repository and submit the URL to Blackboard.

> [!NOTE] If you don't know how to push your code to Azure DevOps, contact your instructor for assistance.