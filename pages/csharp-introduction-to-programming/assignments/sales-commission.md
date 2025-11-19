---
title: Assignment 6 - Sales Commission
subtitle: C# Introduction to Programming
hide-nav: false

live: https://fvtc.software/appel/csharp-introduction-to-programming/assignments/sales-commission
dev: http://localhost:3006/appel/csharp-introduction-to-programming/assignments/sales-commission
repo: https://github.com/rdappel/courses
---

# Assignment 6 - Sales Commission

For this assignment, you will create a WinForms application to determine the commission earned for sales agents. The application must validate input, calculate commission, and display results according to the specifications below.

## Project Setup

Create a new Windows Forms App project in Visual Studio. Name the project `<your-initials>.SalesCommission.UI`, and the solution `<your-initials>.SalesCommission`.

## Form Design

Arrange the controls to closely resemble the following image:

![Form Layout](https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/cs-intro/sales-commission-running.png)

## Operation

1. When the user enters a sales amount, verify that it is numeric and greater than or equal to 0.

    - If not, display a message box with an error, select the text, and allow re-entry.

2. When a valid sales amount is entered, calculate the commission (10% of sales amount) and display it.

3. Display the label as follows:

    - If both first and last name are entered: `Commission for Bill Gates` (using entered names)

    - If only one name is entered: `Commission for Bill` or `Commission for Gates`

    - If no name is entered: `Commission`

4. When any value is entered in first name, last name, or sales amount, clear all calculated display areas.

5. The Clear button should reset all entered and calculated data.

6. The Exit button should close the application.

7. Set appropriate AcceptButton and CancelButton.

8. Set access keys for buttons and controls.

9. Ensure logical tab sequence and proper data alignment.

## Specifications

- Use standard Microsoft naming conventions for all controls.

- Include appropriate comments in your code.

- Validate all input as specified.

- Align all numeric data appropriately.

# Submission

Show your instructor (classroom students), or push your code to the Azure DevOps repository and submit the URL to Blackboard.
