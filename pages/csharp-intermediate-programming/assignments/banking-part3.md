---
title: Assignment 7 - Banking 3
subtitle: C# Intermediate Programming
hide-nav: false

live: https://fvtc.software/appel/csharp-intermediate-programming/assignments/banking-part3
dev: http://localhost:3006/appel/csharp-intermediate-programming/assignments/banking-part3
repo: https://github.com/rdappel/courses
---

# Assignment 7 - Banking (Part 3)

Continue building your [Banking (Part 2)](./banking-part2) application. Extend the persistence layer to store and retrieve customers and their transactions in a database.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Solution Structure

1. Continue using the Windows Forms UI, business layer, models, unit tests, and persistence layer (PL) from the previous parts.
2. Extend the PL to communicate with a database, keeping database access separate from the UI and business logic.
3. Use a database hosted locally or in Azure.

## Specifications

- Create database tables for customers, deposits, and withdrawals. Each deposit and withdrawal must be associated with the correct customer.
- Load customers and their deposits and withdrawals from the database when the application starts.
- Allow the user to add, edit, and delete customers, deposits, and withdrawals. Save each change to the database when the user makes it; do not require a separate Save button.
- When a customer is deleted, ensure that the customer's deposits and withdrawals are handled consistently so no orphaned transactions remain.
- Preserve the IDs and other information needed to display and update the correct records.
- Continue to use proper control naming conventions and appropriate comments.

# Submission

Push your code to the Azure DevOps repository and submit the URL to Blackboard.