---
title: Assignment 5 - Pet Clinic
subtitle: C# Introduction to Programming
hide-nav: false

live: https://fvtc.software/appel/csharp-introduction-to-programming/assignments/pet-clinic-services
dev: http://localhost:3006/appel/csharp-introduction-to-programming/assignments/pet-clinic-services
repo: https://github.com/rdappel/courses
---

# Assignment 5 - Pet Clinic

For this assignment, you will create a WinForms application for Lions, Tigers and Bears Pet Clinic to display and calculate charges for basic services.

<details open style="display: none;">
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Project Setup

Create a new Windows Forms App project in Visual Studio. Name the project `<your-initials>.PetClinic.UI`, and the solution `<your-initials>.PetClinic`. This will help keep your projects organized.

## Form Design

Design the form with at least 8 checkboxes for different pet clinic services (e.g., Office Call, Vaccination, Grooming, Nail Trim, Dental Cleaning, Microchipping, Flea Treatment, Boarding, etc.).

Each service should have an associated label to display the charge for that service. When a checkbox is checked, display the charge in the label; when unchecked, remove the charge.

Include a Total Due area to display the sum of all selected services (currency format). Align all numeric data appropriately.

Include a `Clear` button to reset all checkboxes, labels, and the total variable, and an `Exit` button to close the application.

## Operation

1. When a service is selected (checkbox checked), display the charge for that service in the associated label and add the charge to the total due.

2. When a service is deselected (checkbox unchecked), remove the charge from the label and subtract the charge from the total due.

3. The Total Due area should always show the current sum of selected services in currency format.

4. When the `Clear` button is clicked, all checkboxes, labels, and the total variable should be reset.

5. When the `Exit` button is clicked, the application should close.

## Specifications

1. Use correct naming conventions for your project, solution, and all controls.

2. Use appropriate variables for all numeric data (consider variable scope for the total).

3. Include appropriate comments in your code.

4. Align all numeric data appropriately.

# Submission

Either show your instructor (classroom students), or push your code to the Azure DevOps repository and submit the URL to Blackboard.

> [!NOTE] If you don't know how to push your code to Azure DevOps, contact your instructor for assistance.
