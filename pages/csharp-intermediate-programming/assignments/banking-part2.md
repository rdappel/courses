---
title: Assignment 6 - Banking 2
subtitle: C# Intermediate Programming
hide-nav: false

live: https://fvtc.software/appel/csharp-intermediate-programming/assignments/banking-part2
dev: http://localhost:3006/appel/csharp-intermediate-programming/assignments/banking-part2
repo: https://github.com/rdappel/courses
---

# Assignment 6 - Banking (Part 2)

Continue building your [Banking (Part 1)](./banking-part1) application. Add a persistence layer that saves and loads the customer list using XML or JSON serialization.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/_BvnsmGnHqU" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Solution Structure

1. Continue using the Windows Forms UI, business layer, models, and unit tests from Part 1.
2. Add a **Persistence Layer (PL)** project to the solution.
3. Implement the serialization and file operations in the PL, keeping them separate from the UI and business logic.

## Specifications

- Serialize the entire `CustomerList` to a **single file** using either XML or JSON.
- Save and restore each customer's information, deposits, and withdrawals, including their IDs, amounts, and dates.
- Choose one of the following approaches:
  - Automatically save when the application exits and load when it starts.
  - Provide **Save** and **Load** buttons so the user can save and load the customer list.
- After loading, display the restored customers and their deposits and withdrawals in the existing UI.
- Handle the first run when the file does not yet exist. Do not overwrite previously saved data with the sample customers from `Populate`.
- Notify the user if a file cannot be saved or loaded.
- Continue to use proper control naming conventions and appropriate comments.

# Submission

Push your code to the Azure DevOps repository and submit the URL to Blackboard.