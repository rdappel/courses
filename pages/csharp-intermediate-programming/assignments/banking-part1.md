---
title: Project 5 - Banking Application
subtitle: C# Intermediate Programming
hide-nav: false

live: https://fvtc.software/appel/csharp-intermediate-programming/assignments/banking-part1
dev: http://localhost:3006/appel/csharp-intermediate-programming/assignments/banking-part1
repo: https://github.com/rdappel/courses
---

# Project 5 - Banking Application

Create a multi-project solution for a banking application, including a Windows Forms UI, business layer, models, and unit tests.

## Solution Structure

- **A. User Interface:**
  - Windows Forms Application (.NET)
  - Form Design

  Arrange the controls to closely resemble the following image:

    ![Banking Application Layout](https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/cs-intermed/banking1-running.png)

- **B. Business Layer:**
  - `CustomerManager`
    - `Populate`: Returns a `List<Customer>`
      - Creates three customers
      - Calls `DepositManager.Populate()`
      - Calls `WithdrawalManager.Populate()`
  - `DepositManager`
    - `Populate` method
  - `WithdrawalManager`
    - `Populate` method

- **C. Business Layer Unit Test:**
  - `utCustomer`
    - `PopulateTest`
  - `utDeposit`
    - `PopulateTest`
  - `utWithdrawal`
    - `PopulateTest`

- **D. Business Layer Models:**
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

- Main form contains a drop-down list (listbox) of customers displaying first and last name.
- Selecting a customer populates the details of the `Customer` object (including base properties from `Person`) in appropriate text boxes.
- After selecting a customer, a button displays deposits in another list box or DataGridView. A similar button displays withdrawals.
- Pay attention to date format and alternate row coloring in grids.
- **Add Deposit:** Opens a form to add deposit amount and date (do not show Id).
- **Edit Deposit:** Opens a form to edit deposit amount and date (do not show Id).
- **Add Withdrawal:** Opens a form to add withdrawal amount and date (do not show Id).
- **Edit Withdrawal:** Opens a form to update amount and date of an existing withdrawal (do not show Id).
- Id should be a readonly label.

## Specifications

- Use proper control naming conventions.
- Include appropriate comments in your code.
- Ensure the application does not crash (points deducted per occurrence).

# Submission

Push your code to the Azure DevOps repository and submit the URL to Blackboard.

