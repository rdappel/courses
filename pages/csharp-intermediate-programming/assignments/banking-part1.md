---
title: Assignment 5 - Banking 1
subtitle: C# Intermediate Programming
hide-nav: false

live: https://fvtc.software/appel/csharp-intermediate-programming/assignments/banking-part1
dev: http://localhost:3006/appel/csharp-intermediate-programming/assignments/banking-part1
repo: https://github.com/rdappel/courses
---

# Assignment 5 - Banking (Part 1)

Create a multi-project solution for a banking application, including a Windows Forms UI, business layer, models, and unit tests.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/PrVEKySzgiE" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Solution Structure

1. **User Interface:**
  - Windows Forms Application (.NET)
  - Form Design: Arrange the controls to closely resemble the form in the video.

2. **Business Layer:**
  - `CustomerList`
    - `Populate`
      - Creates three customers

3. **Business Layer Unit Test:**
  - `Customer Tests`
  - `CustomerList Tests`
  - `DepositTests`
  - `Withdrawal Tests`

4. **Business Layer Models:**
  - `Person`
    - `SSN` (string)
    - `FirstName` (string)
    - `LastName` (string)
    - `Age` (int, calculated property)
    - `BirthDate` (DateTime)
    - `FullName` (calculated property)
  - `Customer` (derived from Person)
    - `Id` (int)
    - `Deposits` (List<Deposit>)
    - `Withdrawals` (List<Withdrawal>)
  - `Deposit`
    - `DepositId` (int)
    - `DepositAmount` (double)
    - `DepositDate` (DateTime)
  - `Withdrawal`
    - `WithdrawalId` (int)
    - `WithdrawalAmount` (double)
    - `WithdrawalDate` (DateTime)

All classes should have private intrinsic variables and public getters and setters.

## User Interface Requirements

- Main form contains a listbox of customers displaying first and last name.
- Selecting a customer populates the details of the `Customer` object (including base properties from `Person`) in appropriate text boxes.
- After selecting a customer, that customer's deposits are displayed in a DataGridView and withdrawals in another DataGridView.
- **Add Deposit:** Opens a form to add deposit amount and date (do not show Id).
- **Edit Deposit:** Opens a form to edit deposit amount and date (do not show Id).
- **Add Withdrawal:** Opens a form to add withdrawal amount and date (do not show Id).
- **Edit Withdrawal:** Opens a form to update amount and date of an existing withdrawal (do not show Id).
- Id should be a readonly label.

## Specifications

- Use proper control naming conventions.
- Include appropriate comments in your code.

# Submission

Push your code to the Azure DevOps repository and submit the URL to Blackboard.

