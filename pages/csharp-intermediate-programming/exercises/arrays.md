---
title: Exercise 5 - Arrays
subtitle: C# Intermediate Programming
hideNav: false

live: https://fvtc.software/appel/csharp-intermediate-programming/exercises/arrays
dev: http://localhost:3006/appel/csharp-intermediate-programming/exercises/arrays
repo: https://github.com/rdappel/courses
---

# Exercise 5 - Arrays

In this exercise, you will practice working with arrays in C#. You will create a console application that uses arrays to store and manipulate data.

## Submissions

- None

## Instructions

Open Visual Studio and from the command palette, run `FVTC: Connect to Live Exercise`, then specify a location for your project. The starter code should automatically download.

> [!NOTE] If you haven't installed the FVTC Live Exercise Extension, you can [download it here](https://api.fvtc.software/downloads).

In the `Program.cs` file, you will need to add the following:

1. Create a (public) property to store an array of integers. Call the array `Numbers`, and initialize it with the values `1, 2, 3, 4, 5, 6, 7, 8, 9, 10`.

2. Create a method called `ArrayToString` that converts the array to a string and prints it to the console.

3. Create a method called `SumArray` that calculates the sum of all the elements in the array and returns the result.

4. Create a method called `AverageArray` that calculates the average of all the elements in the array and returns the result. Remember that the average might not be an integer!

5. In the `Main` method, call the `ArrayToString`, `SumArray`, and `AverageArray` methods and print the results to the console. The results should look like this:

<div class="no-copy">

```bash
Array: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10
Sum: 55
Average: 5.5
```

</div>

## Running and Testing your Code

To run and test your code, right-click on the `Exercise.UI` project in the Explorer window and select `Open in Integrated Terminal`. In the terminal window, type `dotnet run` and press Enter. To test, type `dotnet test` and press Enter.

## Submission

Once you have completed the exercise, run `FVTC: Submit Live Exercise` in the command palette to submit your code for grading.

> [!TIP] Confirm here that your submission was successful.


## Hints

<details>
	<summary>How do I create an array property?</summary>

You can create an array property in a class by using the following syntax:

```csharp
public int[] Numbers { get; set; }
```

</details>

<details>
	<summary>How do I initialize an array with values?</summary>

You can initialize an array with the following syntax:

```csharp
Numbers = new int[] { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
```

</details>

<details>
	<summary>How do I convert an array to a string?</summary>

You can iterate over the array and concatenate the elements into a string, or you can use the `string.Join` method.

```csharp
// Using a loop
string arrayString = "";
for (int i = 0; i < Numbers.Length; i++)
{
	arrayString += Numbers[i] + (i < Numbers.Length - 1 ? ", " : "");
}

// Using string.Join
string arrayString = string.Join(", ", Numbers);
```

</details>

<details>
	<summary>How do I calculate the sum of an array?</summary>

You can use a loop to iterate over the elements and add them together.

```csharp
// Using a loop
int sum = 0;
foreach (int number in Numbers) { sum += number; }
```

</details>

<details>
	<summary>How do I calculate the average of an array?</summary>

You can calculate the average by dividing the sum of the elements by the number of elements.

```csharp
int sum = 0;
foreach (int number in Numbers) { sum += number; }
int average = sum / Numbers.Length;
```

If you already have a function that calculates the sum, you can reuse it to calculate the average.

```csharp
int average = SumArray() / Numbers.Length;
```

</details>

<details>
	<summary>How do I print an array to the console?</summary>

Assuming you have the `ArrayToString` method that converts the array to a string, you can print it to the console like this:

```csharp
Console.WriteLine("Array: " + arrayString);
```

</details> 






