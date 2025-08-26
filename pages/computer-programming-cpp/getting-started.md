---
title: Getting Started
subtitle: Computer Programming C++
hideNav: false

live: https://fvtc.software/appel/computer-programming-cpp/getting-started
---

# Getting Started

This unit will introduce you to the basics of C++. If you are used to programming in C#, much of this unit will be review. Let's get started by creating a project.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/IwvrOJ9HjUE" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

If you do not have "Visual C++" templates available in the New Project window, you need to [Modify your Visual Studio Installation](https://www.youtube.com/watch?v=suoeL7yfbyc).


## The Main Function

Every program needs an entry point. The windows applications that you wrote in C# had a file called Program.cs, that contained a "Main" function. Similarly, we need to create a starting point for our appliction.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/PfGWzyj-0fc" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

Here is the code from the video:

```cpp
// Getting Started Demo
// Ryan Appel
 
int main()
{
    return 0;
}
```

> [!NOTE] Comments work the same way in C++ as they do in C#. You can use `//` to create a single-line comment, or `/* */` to create a multi-line comment. 

You can debug your program by pressing the "Start" button in Visual Studio, or by pressing F5, just like you did in C#.

When you debug your program, you will see a console window appear with the following text:

```plaintext
C:\Users\...\RDA.GettingStartedDemo.exe (process 24460) exited with code 0.
To automatically close the console when debugging stops, enable Tools->Options->Debugging->Automatically close the console when debugging stops.
Press any key to close this window . . .
```

Watch what happens when I run the actual program (not the debugger) by opening it from the file explorer.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/cDVWPq9dpME" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

The program runs and the console window appears, but it closes immediately. This is because Visual Studio is configured add the "Press any key to close this window..." line to the end of the program. This is not a part of the program itself, but rather a feature of Visual Studio.

I want to control this behavior myself, so I can have the same experience when running the program from the file explorer as I do when running it from Visual Studio.

Let's change the following setting.

Go to: `Tools->Options->Debugging` and then check `Automatically close the console when debugging stops`.

> [!IMPORTANT] Your code must have exactly one `main()` function. If you have more than one, you will get a linker error.

## Writing to the Console

Let's print some text to the console. We can do this using the `cout` object, which is part of the `std` namespace.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/6AD7VgmpbEs" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

Here is the code from the video:

```cpp
// Getting Started Demo
// Ryan Appel

#include <iostream> // allows us to use cout
#include <conio.h> // allows us to use _getch()

int main()
{
    std::cout << "Hello world!"; // print to the console
    (void)_getch(); // wait for key press
    return 0;
}
```

The `<<` operator is used to send data to the console. In this case, we are sending the string `"Hello world!"`.

Let's print some more text to the console.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/QMdpaC-CJRs" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

Here is the code from the video, for brevity I will only show the new code:

```cpp
std::cout << "Hello World!" << std::endl;
std::cout << "This is a new line.\n";
std::cout << "This is another line." << "\n";
```

Notice how we can use `std::endl` to end the line, or we can use the escape sequence `\n`. Both will produce the same result.

> [!NOTE] Technically `std::endl` will also flush the output buffer, but for our purposes, it is the same as using `\n`.

I personally prefer to use `\n` because it is more concise. So I will be using that in the future. However, you may see `std::endl` in other people's code, so it is good to know what it is.

## Escape Sequences

Escape sequences are special characters that are used to represent non-printable characters. For example, the escape sequence `\n` represents a new line. Here are some common escape sequences:

- `\n` - New Line
- `\t` - Tab
- `\\` - Backslash
- `\"` - Double Quote
- `\'` - Single Quote
- `\0` - Null Character

> [!NOTE] One nice thing about escape sequences is that they are (for the most part) portable across different programming languages. `\t` will produce a tab in C++, C#, JavaScript, and many other languages.

In this video, we will look at how to use escape sequences.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/OW142Bqc3hg" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

Here's the code from the video:

```cpp
std::cout << "\"Hello World!\"";
```

# Exercise 1

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/2FsDCG-IVkg" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

In this exercise, you will create a new project and write a program that prints the following text to the console:

```plaintext
"Ryan is the best instructor ever!"
	- Ryan
```

## Hints {#exercise-1-hints}

<details>
	<summary>What includes do I need?</summary>

You will need to include the `iostream` header file to use `cout`, and the `conio.h` header file to use `_getch()`.

```cpp
#include <iostream>
#include <conio.h>
```

</details>

<details>
	<summary>How do I print text to the console?</summary>

You can use the `cout` object to print text to the console. Here is an example:

```cpp
std::cout << "Hello World!";
```

</details>

<details>
	<summary>How do I print a new line?</summary>

You can use the escape sequence `\n` to print a new line. Here is an example:

```cpp
std::cout << "Hello World!\n";
```

</details>

<details>
	<summary>How do I print a tab?</summary>

You can use the escape sequence `\t` to print a tab. Here is an example:

```cpp
std::cout << "Hello\tWorld!";
```

</details>

<details>
	<summary>How do I print a double quote?</summary>

You can use the escape sequence `\"` to print a double quote. Here is an example:

```cpp
std::cout << "\"Hello World!\"";
```

</details>

## Solution {#exercise-1-solution}

<details>
	<summary>Show the Answer</summary>

```cpp
// Exercise 1
// Ryan Appel

#include <iostream>
#include <conio.h>

int main()
{
	std::cout << "\"Ryan is the best instructor ever!\"\n";
	std::cout << "\t- Ryan";

	(void)_getch();
	return 0;
}
```

Alternatively, you could have kept the statement on one line:

```cpp
std::cout << "\"Ryan is the best instructor ever!\"\n\t- Ryan";
```

</details>

<details>
	<summary>Walkthrough Video</summary>
		<div class="video-container">
		<iframe src="https://www.youtube.com/embed/e3XMy0J7ivw" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		></iframe>
	</div>
</details>

# The Standard Namespace

The `std` namespace is a collection of classes, functions, and objects that are part of the standard library. It can become cumbersome to write `std::` before everything, so we can use the `using` directive to bring the `std` namespace into scope.

In this video, we will look at how to do this.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/q_TfXTGwImU" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

Here's the code:

```cpp
#include <iostream>
#include <conio.h>

using namespace std;

int main()
{
    cout << "Hello World!"; // note that we don't need std::

	(void)_getch();
    return 0;
}
```

> [!CAUTION] It is often considered bad practice to use `using namespace std;` This is because it can pollute the global namespace. We will go into more detail about this in the future. For now, we can use it to make our code more concise.

# Variables and Primitive Data Types

You should be familiar with variables and primitive data types from previous classed. In C++, the primitive data types are similar to C#, and include: `int`, `float`, `double`, `char`, `bool`, and `void`.

Note that `string` is not a primitive data type in C++. Instead, it is a class that is part of the `std` namespace. We will go into more detail later.

In this video, we will look at how to declare variables and assign values to them.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/8KTbN2ib-yw" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

Here's the code from the video:

```cpp
int age = 30;
const float pi = 3.14159f;
const double e = 2.71828;
char middleInitial = 'D';
bool isInstructor = true;
```

> [!NOTE] Notice that I added an `f` to the end of the `pi` variable. This is because `3.14159` would be a `double` by default, and I want to make it a `float`. 

## Constants

As explained in the previous video, you can use the `const` keyword to create a constant variable. This is a variable that cannot be changed after it is initialized.

Remember that in C++, you can put the `const` keyword before or after the data type.

```cpp
const float pi = 3.14159f;
float const pi = 3.14159f;
```

Both of these are valid and will produce the same result. Though, I prefer to put the `const` keyword before the data type.

> [!TIP] The general rule of thumb with `const` is that it applies to the thing to its left. If there is nothing to the left, it applies to the thing to its right. We will see `const` used in other contexts in the future. So remember this rule!

## Casting

Casting is the process of converting one data type to another. In C++, there are two types of casting: implicit and explicit.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/cxUwAXPuXqo" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

### Implicit Casting

Implicit casting is when the compiler automatically converts one data type to another. This is done when the conversion is safe and no data is lost. For example, converting an `int` to a `float` is safe because the `float` can hold a larger range of values.

```cpp
int age = 30;
float ageFloat = age; // implicit cast -- ageFloat is 30.0
```

### Explicit Casting

Explicit casting is when you tell the compiler to convert one data type to another. This is done when the conversion is not safe and data may be lost. For example, converting a `float` to an `int` will truncate the decimal portion of the number.

```cpp
float pi = 3.14159f;
int piInt = (int)pi; // explicit cast -- piInt is 3
```

# User Input

In this video, we will look at how to get input from the user. We will use the `cin` object, which is part of the `std` namespace.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/EVmcnk9Hnvo" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

Here's the code from the video:

```cpp
#include <iostream>

using namespace std;

int main()
{
    int age;
    cout << "Enter your age: ";
    cin >> age;
    cout << "You are " << age << " years old.";
    return 0;
}
```

The `cin` object is used to get input from the user. The `>>` operator is used to send the input to a variable. In this case, we are sending the input to the `age` variable.

> [!TIP] Sometimes students confuse the `>>` operator with the `<<` operator. I find it helpful to think about which way the data is moving. For example `cout << "hi";` is sending "hi" to the console, and `cin >> age;` is sending an age from the console (user input) to the `age` variable.

# Exercise 2

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/oc9D3fFu4L4" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

In this exercise, you will create a new project and write a program that asks the user for their age and then prints the following text to the console:

```plaintext
You are `N` years old.
In 10 years, you will be `X` years old.
```

Where `N` is the age that the user entered, and `X` is the age that the user will be in 10 years.

Store the user's age in a variable called `age`, and store the age in 10 years in a variable called `ageIn10Years`.

## Hints {#exercise-2-hints}

<details>
	<summary>How do I get input from the user?</summary>

You can use the `cin` object to get input from the user. Here is an example:

```cpp
int age = 0;
std::cout << "Enter your age: ";
std::cin >> age;
```

</details>

<details>
	<summary>How do I print a variable to the console?</summary>

You can use the `<<` operator to print a variable to the console. Here is an example:

```cpp
int age = 30;
std::cout << "You are " << age << " years old.";
```

</details>

<details>
	<summary>How do I perform arithmetic in C++?</summary>

You can use the standard arithmetic operators in C++. Here is an example:

```cpp
int age = 30;
int ageIn10Years = age + 10;
```

</details>

## Solution {#exercise-2-solution}

<details>
	<summary>Show the Answer</summary>

```cpp
// Exercise 2
// Ryan Appel

#include <iostream>
#include <conio.h>

using namespace std;

int main()
{
	int age = 0;
	int ageIn10Years = 0;

	cout << "Enter your age: ";
	cin >> age;

	ageIn10Years = age + 10;

	cout << "You are " << age << " years old.\n";
	cout << "In 10 years, you will be " << ageIn10Years << " years old.";

	(void)_getch();
	return 0;
}

```

</details>

<details>
	<summary>Walkthrough Video</summary>
		<div class="video-container">
		<iframe src="https://www.youtube.com/embed/DIMpJ_2mDIc" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		></iframe>
	</div>
</details>

