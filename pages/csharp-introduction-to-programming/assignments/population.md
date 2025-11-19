---
title: Assignment 7 - Population Change
subtitle: C# Introduction to Programming
hide-nav: false

live: https://fvtc.software/appel/csharp-introduction-to-programming/assignments/population
dev: http://localhost:3006/appel/csharp-introduction-to-programming/assignments/population
repo: https://github.com/rdappel/courses
---

# Assignment 7 - Population Change

For this assignment, you will create a WinForms application to help answer population questions in the library. The application will accept city and state, beginning and ending population, and calculate the percent increase or decrease.

## Project Setup

Create a new Windows Forms App project in Visual Studio. Name the project `<your-initials>.PopulationChange.UI`, and the solution `<your-initials>.PopulationChange`.

## Form Design

Arrange the controls to closely resemble the following image:

![Form Layout](https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/cs-intro/population-running.png)

## Operation

1. Verify that data has been entered for City and State.

    - State must be exactly 2 characters and displayed in all capital letters.

2. Verify that Beginning Population and Ending Population are valid numeric values.

3. When any entered data changes, clear all calculated values.

4. When calculation is performed:

    - If the ending population is greater than the beginning population, calculate and display percent increase.

    - If the ending population is less than the beginning population, calculate and display percent decrease.

    - If the ending population is equal to the beginning population, display a message box stating no change.

    - Display a message box stating increase, decrease, or no change as appropriate.

5. After calculation completes without user errors, select and return the cursor to the Beginning Population textbox.

6. The Clear button should reset all entered and calculated data and return the cursor to the City textbox.

7. The Exit button should close the application.

8. Set appropriate AcceptButton and CancelButton.

9. Set access keys for buttons and controls.

10. Ensure logical tab sequence and proper data alignment.

## Specifications

- Use standard Microsoft naming conventions for all controls.

- Include appropriate comments in your code.

- Validate all input as specified.

- Align all numeric data appropriately.

## Calculations

Calculate the percent change using the formulas:

   Percent Increase = (Ending Population - Beginning Population) / Beginning Population * 100

   Percent Decrease = (Beginning Population - Ending Population) / Beginning Population * 100

> [!TIP] You can use `.ToString("p")` to format the output as a percentage.

# Submission

Show your instructor (classroom students), or push your code to the Azure DevOps repository and submit the URL to Blackboard.

