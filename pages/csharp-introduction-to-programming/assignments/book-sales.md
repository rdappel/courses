---
title: Assignment 4 - Book Sales
subtitle: C# Introduction to Programming
hide-nav: false

live: https://fvtc.software/appel/csharp-introduction-to-programming/assignments/book-sales
dev: http://localhost:3006/appel/csharp-introduction-to-programming/assignments/book-sales
repo: https://github.com/rdappel/courses
---

# Assignment 4 - Book Sales

For this assignment, you will create a WinForms application for FVTC Book Sales. The application will allow the user to enter the total sales amount and calculate a 25% discount.

<details open style="display: none;">
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Project Setup

Create a new Windows Forms App project in Visual Studio. Name the project `<your-initials>.BookSales.UI`, and the solution `<your-initials>.BookSales`. This will help keep your projects organized.

## Form Design

Arrange the controls to closely resemble the standard layout used in previous assignments.

(No image provided for this assignment.)

## Operation

1. The user enters the total sales amount.

2. When the `Calculate` button is clicked, the application should:

   - Calculate the discount amount (25% of total sales)

   - Calculate the discounted sales amount (total sales minus discount)

   - Display both calculated values as currency

3. When the `Clear` button is clicked, all fields should be cleared and focus should return to the total sales textbox.

4. When the `Exit` button is clicked, the application should close.

5. If the user changes the value in the total sales textbox, any calculated values should be cleared.

6. If the user clicks `Calculate` without entering a sales amount, the application should handle this situation gracefully (e.g., show a message or prevent calculation).

## Specifications

1. Use logical tab sequence for all controls.

2. Set AcceptButton (`Calculate`) and CancelButton (`Exit`) properties appropriately.

3. Assign access keys to each of the Buttons.

4. Display all calculated values as currency.

5. Align numeric data appropriately.

6. Reset focus to the total sales textbox after calculation and clearing the form.

7. Use correct naming conventions for your project, solution, and all controls.

8. Use appropriate variables for all numeric data.

9. Include appropriate comments in your code.

# Submission

Either show your instructor (classroom students), or push your code to the Azure DevOps repository and submit the URL to Blackboard.
