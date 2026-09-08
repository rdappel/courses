---
title: Functions
subtitle: Computer Programming C++
hideNav: false

live: https://fvtc.software/appel/computer-programming-cpp/functions
---

# Functions in C++

In this lesson, we will learn about functions in C++. Functions are a way to organize code into reusable blocks. They are a fundamental concept in programming and are used in every programming language.

> [!NOTE] You should be familiar with methods from C#. Functions are similar, but technically different. A method is a function that is part of a class. Therefore, all methods are functions, but not all functions are methods.

## Function Syntax

Here is the basic syntax for a function in C++:

```cpp
return_type function_name(parameters)
{
	// code
}
```

- `return_type` is the type of value that the function will return. If the function does not return a value, use `void`.
- `function_name` is the name of the function. This is how you will call the function.
- `parameters` are the values that the function will accept. `parameters` are optional.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/lZA3GmrYTaI" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code:

```cpp
void PrintHi()
{
	cout << "Hi";
}

int main()
{
	PrintHi();
	
	(void)_getch();
	return 0;
}
```

# Parameters

Parameters are the values that the function will accept. In C++ you must specify the type of each parameter.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/qB0oCwemvws" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code from the video:

```cpp
void PrintHi(int count, bool formal)
{
	for (int i = 0; i < count; i++)
	{
		if (!formal) cout << "Hi\n";
		else cout << "Hello good sir!\n";
	}
}

int main()
{
	PrintHi(3, true);
	
	(void)_getch();
	return 0;
}
```

> [!NOTE] You can use `const` to make a parameter a const value. For example, `void PrintHi(const int count)` will prevent the function from modifying the value of `count`. This isn't particularly useful now, but it will be later when we learn about structs and classes.

## Optional Parameters

In C++, you can provide default values for parameters. This allows you to call the function without providing a value for that parameter. This is referred to as an "optional parameter", and is also sometimes called a "default parameter."

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/XwBBhLraAXA" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code from the video:

```cpp
void PrintHi(int count = 1, bool formal = false)
{
	for (int i = 0; i < count; i++)
	{
		if (!formal) cout << "Hi\n";
		else cout << "Hello good sir!\n";
	}
}
```

# Function Overloading

Function overloading is a feature in C++ that allows you to define multiple functions with the same name, but different parameters. This is useful when you want to perform the same operation on different types of data.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/j_1u6eAQgBI" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here are the overloaded functions from the video:

```cpp
void PrintHi(int count)
{
	PrintHi(count, false);
}

void PrintHi(int count, bool formal)
{
	for (int i = 0; i < count; i++)
	{
		if (!formal) cout << "Hi\n";
		else cout << "Hello good sir!\n";
	}
}
```

> [!NOTE] This code will not compile! The following section [function prototypes](#function-prototypes) will explain why, and how to fix it.

# Function Prototypes

The C++ compiler reads your code from top to bottom. This means that if you call a function before it is defined, the compiler will not know what you are talking about. To fix this, you can use a function prototype. Take a look:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/0ZOYfUbLjUA" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code from the video:

```cpp
// function prototypes
void PrintHi(int count);
void PrintHi(int count, bool formal);

int main()
{
	PrintHi(2);

	(void)_getch();
	return 0;
}

void PrintHi(int count)
{
	PrintHi(count, false);
}

void PrintHi(int count, bool formal)
{
	for (int i = 0; i < count; i++)
	{
		if (!formal) cout << "Hi\n";
		else cout << "Hello good sir!\n";
	}
}
```

# Return Values

Often when we execute a function, we want to get a value back. Similar to C#, we can have a function return a value.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/vqP9YI4Yh98" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code from the video:

```cpp
// function prototypes
int GetUserNumber(int max = 10);

int main()
{
	int number = GetUserNumber(50);
	cout << "Your number is " << number << ".\n";

	(void)_getch();
	return 0;
}

int GetUserNumber(int max)
{
	int value = 0;
	while (value < 1 || value > max)
	{
		cout << "Enter a number between 1 and " << max << ": ";
		cin >> value;
	}

	return value;
}
```

# Exercise 1

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/JFTnBqKfN1w" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

In this exercise, modify the `GetUserNumber` function to accept a minimum value as well as a maximum value. Have the minimum default to 1.

If the function is called and the minimum value is greater than the maximum value, swap the values.

Test the function by calling it with:

```cpp
int userNumber1 = GetUserNumber(5, 10);
int userNumber2 = GetUserNumber(10, 5);

cout << "User number 1: " << userNumber1 << endl;
cout << "User number 2: " << userNumber2 << endl;
```

## Hint {#exercise-1-hint}

<details>
	<summary>How do I swap two values?</summary>

You will probably need to use a temporary variable to swap the values, like this:

```cpp
int t = min;
min = max;
max = t;
```

</details>

## Solution {#exercise-1-solution}

<details>
	<summary>Show the Answer</summary>

```cpp
// function prototypes
int GetUserNumber(int max = 10, int min = 1);

int main()
{
	//int number = GetUserNumber();
	//cout << "Your number is " << number << ".\n";

	int userNumber1 = GetUserNumber(5, 10);
	int userNumber2 = GetUserNumber(10);

	(void)_getch();
	return 0;
}

int GetUserNumber(int max, int min)
{
	if (min > max)
	{
		int t = min;
		min = max;
		max = t;
	}

	int value = 0;
	while (value < min || value > max)
	{
		cout << "Enter a number between " << min << " and " << max << ": ";
		cin >> value;
	}

	return value;
}
```

</details>

<details>
	<summary>Walkthrough Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/uzUHoQUHDUg" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# Recursion

Recursion is a technique in programming where a function calls itself. In order to prevent infinite loops, you must have a base case that will stop the recursion.

Let's look at an example:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/vw9GMS9WySA" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the example from the video:

```cpp
void CountDownFrom(int starting)
{
	cout << starting << "\n";
	if (starting > 0) CountDownFrom(starting - 1);
}

int main()
{
	CountDownFrom(10);

	(void)_getch();
	return 0;
}
```

> [!WARNING] The `main` function should never be called manually! Calling `main` manually will cause all of the local variables to be duplicated and will not be able to be freed.

# The Call Stack

When a function is called, the computer creates a new stack frame. This stack frame contains the local variables for that function. When the function returns, the stack frame is removed.

We can monitor the call stack by using the `callstack` window in Visual Studio. This is useful for debugging because it allows you to see where a function was called from.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/xhk9O9fXoaQ" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

If your Call Stack window is not visible, you can find it by going to `Debug > Windows > Call Stack`.

> [!NOTE] The Call Stack window is only available when you are debugging your program.

# Exercise 2

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/xhH6AvKLWc8" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

For this exercise, I want you to create a function called `PrintHi` that will print "Hi" to the console. This should sound familiar (hint: it was the first two functions that we created). This time though, I want you to make the function recursive.

The function should accept an integer parameter that will determine how many times "Hi" is printed. Make the parameter default to 1.

Call the function from `main` with a value of 5, and again with no value.

## Hints {#exercise-2-hints}

<details>
	<summary>How do I make a function recursive?</summary>

You need to call the function from within itself. You should also have a condition that will stop the recursion.

</details>

<details>
	<summary>How do I make a parameter default to 1?</summary>

You can set the default value in the function prototype. For example, `void PrintHi(int count = 1);`, or in the function definition itself, if you create your function above `main`.

</details>

## Solution {#exercise-2-solution}

<details>
	<summary>Show the Answer</summary>

```cpp
void PrintHi(int count = 1)
{
	cout << "Hi\n";
	if (count > 1) PrintHi(count - 1);
}

int main()
{
	PrintHi(5); // should print "Hi" 5 times
	cout << "\n";
	PrintHi(); // should print "Hi" once

	(void)_getch();
	return 0;
}
```

</details>

<details>
	<summary>Walkthrough Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/z08i2WDtYpQ" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# Reference Variables

When working with primitive types in C++, you generally have one variable that holds one value. Sometimes however, it's useful to have two variables that refer to the same value in memory. This is called a reference variable.

To create a reference variable, you use the `&` symbol after the type. For example:

```cpp
int a = 5;
int &b = a;
```

Now `b` and `a` refer to the same value in memory. Changing either variable will change the other.

> [!NOTE] Reference variables cannot be set to a literal value. They must be set to a variable. For example, this code will not compile: `int &b = 5;`.

This video will illustrate the differenc between a reference variable and a normal variable:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/7nDfT2cX1p0" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# Reference Parameters

Reference parameters are a way to pass a variable by reference to a function. This allows the function to modify the value of the original variable. Take a look:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/09yu8iM0hf8" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code from the video:

```cpp
void PassByValue(int b)
{
	cout << "b: " << b << "\n";
	b++;
	cout << "b is now: " << b << "\n";
}

void PassByReference(int &c)
{
	cout << "c: " << c << "\n";
	c++;
	cout << "c is now: " << c << "\n";
}

int main()
{
	int a = 6;
	PassByValue(a);
	cout << "a (first time): " << a << "\n"; // a is still 6!

	PassByReference(a);
	cout << "a (second time): " << a << "\n"; // a is now 7!

	(void)_getch();
	return 0;
}
```

Let's look at a more practical example:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/ThKhBevd4-k" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the (cleaned up) code from the video:

```cpp
float Add(float n1, float n2) { return n1 + n2; }
float Subtract(float n1, float n2) { return n1 - n2; }
float Multiply(float n1, float n2) { return n1 * n2; }

// division can fail, so we use a reference param for the result!
bool Divide(float numerator, float denominator, float &answer)
{
	if (numerator == 0) return false; // can't divide by zero!
	answer = numerator / denominator; // modify the original variable ("result" in main())
	return true; // success!
}

int main()
{
	cout << "Addition: " << Add(3, 0) << "\n";
	cout << "Subtraction: " << Subtract(3, 0) << "\n";
	cout << "Multiplication: " << Multiply(3, 0) << "\n";

	// handle division by zero! (Replace the denominator to test)
	float result;
	if (Divide(3, 5, result)) cout << "Division: " << result;
	else cout << "Can't divide by zero!";

	(void)_getch();
	return 0;
}
```
