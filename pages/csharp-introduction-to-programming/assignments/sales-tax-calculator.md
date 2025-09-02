---
title: Assignment 10 - Sales Tax Calculator
subtitle: C# Introduction to Programming
hide-nav: false

live: https://fvtc.software/appel/csharp-introduction-to-programming/assignments/sales-tax-calculator
dev: http://localhost:3006/appel/csharp-introduction-to-programming/assignments/sales-tax-calculator
repo: https://github.com/rdappel/courses
---

# Assignment 10 - Sales Tax Calculator

For this assignment, you will create a WinForms application that uses a function to calculate sales tax. The application should include a form and a class.

## Project Setup

Create a new Windows Forms App project in Visual Studio. Name the project `<your-initials>.SalesTaxCalculator.UI`, and the solution `<your-initials>.SalesTaxCalculator`.

## Form Design

Arrange the controls to closely resemble the standard layout used in previous assignments.

(No image provided for this assignment.)

## Operation

1. When the user clicks the display button:

    - Validate the sales amount using TryParse

    - Instantiate an instance of the `Transaction` class

    - Call the `CalculateSalesTax` method to calculate the sales tax

    - Display the sales tax and total due

    - Dispose of the object

2. The Clear button resets all entered and calculated data.

3. The Exit button closes the application.

4. The About button opens a modal About form.

## Class Design

- **Class:** `Transaction`

- **Properties:**

    - `TaxRate`

- **Methods:**

    - `CalculateSalesTax`

        - Returns the sales tax amount

        - Accepts the sales amount as an input parameter

## About Form

- When the user clicks the About button, display a modal About form

- The About form should show:

    - A picture

    - Your name

    - Application description

    - An OK button to return to the main form

## Extra Credit: Splash Form

Add a Splash Form that displays while the main form is loading.

> [!NOTE] A splash form uniquely identifies an application while it is loading, as well as providing something for the viewer to see while critical initialization sections of the code execute.

## Specifications

- Use standard Microsoft naming conventions for all controls

- Include appropriate comments in your code

- Validate all input as specified

- Align all numeric data appropriately

- Set appropriate AcceptButton and CancelButton.

- Set access keys for buttons and controls.

- Ensure logical tab sequence and proper data alignment.

# Submission

Show your instructor (classroom students), or push your code to the Azure DevOps repository and submit the URL to Blackboard.
