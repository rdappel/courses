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

## Solution Structure

1. **User Interface:**
  - Windows Forms Application (.NET)
  - Form Design: Arrange the controls to closely resemble the following image:

    ![Banking Application Layout](https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/cs-intermed/banking1-running.png)

2. **Business Layer:**
  - `CustomerManager`
    - `Populate`: Returns a `List<Customer>`
      - Creates three customers
      - Calls `DepositManager.Populate()`
      - Calls `WithdrawalManager.Populate()`
  - `DepositManager`
    - `Populate` method
  - `WithdrawalManager`
    - `Populate` method

3. **Business Layer Unit Test:**
  - `utCustomer`
    - `PopulateTest`
  - `utDeposit`
    - `PopulateTest`
  - `utWithdrawal`
    - `PopulateTest`

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
- Ensure the application does not crash (points deducted per occurrence).

# Submission

Push your code to the Azure DevOps repository and submit the URL to Blackboard.

