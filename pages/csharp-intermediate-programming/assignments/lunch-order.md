---
title: Assignment 1 - Lunch Order
subtitle: C# Intermediate Programming
hide-nav: false

live: https://fvtc.software/appel/csharp-intermediate-programming/assignments/lunch-order
dev: http://localhost:3006/appel/csharp-intermediate-programming/assignments/lunch-order
repo: https://github.com/rdappel/courses
---

# Assignment 1 - Lunch Order

For this assignment you’ll create a form that accepts a lunch order from the user and then calculates the order subtotal and total.

<details open style="display: none;">
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/AAAAAAA" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Project Setup

Create a new Windows Forms App project in Visual Studio. Name the project `<your-initials>.LunchOrder.UI`, and the solution `<your-initials>.LunchOrder`. This will help keep your projects organized.

## Form Design

Arrange the controls to closely resemble the following image:

![Form Layout](https://raw.githubusercontent.com/rdappel/courses/refs/heads/master/support-files/cs-intermed/lunch-order-running.png)

## Operation

- For each order, the user selects a main course item and the application displays the associated add-on items. Then, the user can select zero or more of these add-ons.

- When the user clicks the `Place Order` button, the application calculates and displays the subtota, tax, and the total due for the order.

- When the user selects a main course, the application should remove check marks from any of the add-on items and clear the order totals.

- When the user checks or unchecks an add-on item, the application should clear the order totals.

### Add-ons

- For a hamburger, the three add-on items are: (1) Lettuce, tomato, and onions; (2) Mayonnaise and mustard; and (3) French fries. The price of each is 75 cents.

- For a pizza, the three add-on items are: (1) Pepperoni, (2) Sausage, and (3) Olives. The price of each is 50 cents.

- For a salad, the three items are (1) Croutons, (2) Bacon bits, and (3) Bread sticks. The price of each is 25 cents.

> [!NOTE] The add-on items have different prices depending on the main course selected.

## Specifications

- The subtotal is equal to the cost of the main course item, plus the cost of the add-ons. The tax is the subtotal * .0775. And the total due is the subtotal + tax.

- Use correct naming conventions for your project, solution, and all controls.

- Remember to comment your code appropriately.

# Submission

Push your code to the Azure DevOps repository and submit the URL to Blackboard.

> [!NOTE] If you don't know how to push your code to Azure DevOps, ask your instructor for assistance.