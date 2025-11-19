---
title: Variables and Operators
subtitle: Modern JavaScript
hideNav: false

live: https://fvtc.software/appel/modern-javascript/variables-and-operators
---

# Variables

You should be familiar with variables from C#. In JavaScript, variables are declared using the `let` keyword and constants are declared using the `const` keyword. This video will walk you through declaring variables and constants in JavaScript.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/RxdP32ag3Ag" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code that we wrote in the video:

Remember that `let` is used for variables:

```javascript
let name = 'John'
```

And `const` is used for constants:

```javascript
const name = 'John'
const age = 20
```

The backtick character (`` ` ``) in combination with the dollar sign/curly braces (`${}`) is used for string interpolation:

```javascript
console.log(`${name} is ${age + 50} years old.`) 
```

## Data Types

There are several different data types in JavaScript. The most common ones are covered in this video.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/Hff36CaQ-pg" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

For reference, here are the data types that we covered in the video:

- **String**: A string is a sequence of characters. Strings are used to represent text. Strings are declared using double quotes (`"`) or single quotes (`'`).

- **Number**: A number is a numeric value. Numbers can be integers (whole numbers) or floating-point numbers (numbers with a decimal point). Numbers are declared without quotes.

- **Boolean**: A boolean is a value that is either `true` or `false`. Booleans are used to represent the truth value of an expression. Booleans are declared without quotes.

- **Null**: Null is a special value that represents "nothing". Null is declared without quotes.

- **Undefined**: Undefined is a special value that represents a variable that has not been assigned a value. Undefined is declared without quotes.

- **Object**: An object is a collection of key-value pairs. Objects are declared using curly braces (`{}`).

- **Array**: An array is a collection of values. Arrays are declared using square brackets (`[]`).

- **Function**: A function is a block of code that can be called by name. Functions are declared using the `function` keyword.

## Comments

Comments in JavaScript are similar to comments in C#. Single-line comments start with `//` and multi-line comments start with `/*` and end with `*/`. Here is an example:

```javascript
// This is a single-line comment

/*
This is a multi-line comment.
See how it spans multiple lines?
So spany lines. Much comment. Very multi-line. Wow. - Doge
*/
```

# Operators

JavaScript has several different operators. In this video, we will cover the most common ones.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/jQsIDKfERGM" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Assignment Operators

Assignment operators are used to assign values to variables. The most common assignment operator is `=`. Here is an example:

```javascript
let x = 5
console.log(x) // 5
```

## Arithmetic Operators

Arithmetic operators are used to perform arithmetic operations on numbers. The most common arithmetic operators are `+`, `-`, `*`, `/`, and `%`. Here is an example:

```javascript
const a = 10
const b = 3
const c = a + b // 13
const d = a - b // 7
const e = a * b // 30
const f = a / b // 3.333333
const g = a % b // 1
```

## Comparison Operators

Comparison operators are used to compare two values. The most common comparison operators are `==`, `!=`, `===`, `!==`, `>`, `<`, `>=`, and `<=`. Here is an example:

```javascript
let x = 5
let y = 10
console.log(x == y) // false
console.log(x != y) // true
console.log(x === y) // false
console.log(x !== y) // true
console.log(x > y) // false
console.log(x < y) // true
console.log(x >= y) // false
console.log(x <= y) // true
```

> [!NOTE] The `==` and `!=` operators are used to compare values, while the `===` and `!==` operators are used to compare values and types. So, `5 == "5"` is true, but `5 === "5"` is false. I recommend using the `===` and `!==` operators, because they are more strict.

## Logical Operators

Logical operators are used to combine multiple conditions. The most common logical operators are `&&` (and), `||` (or), and `!` (not). Let's take a look:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/hjj0gNGpsHs" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
let x = 5
let y = 10
console.log(x > 0 && y > 0) // true
console.log(x > 0 || y > 0) // true
console.log(!(x > 0)) // false
```

> [!NOTE] The `||` operator is often used to provide a default value for a variable. For example, if we want to assign a default value of "John Doe" to a variable called `name`, we can do this: `let name = inputValue || "John Doe"`.

## Increment and Decrement Operators

Increment and decrement operators are used to modify the value of a variable. They work just like you are used to from C#. Let's take a look:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/YiatrtrJnB8" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

```javascript
let x = 5
x++
console.log(x) // 6
x--
console.log(x) // 5
x += 10
console.log(x) // 15
x -= 10
console.log(x) // 5
```

## Ternary Operator

The ternary operator is used to assign a value to a variable based on a condition. It is similar to an if statement. Here is an example:

```javascript
let x = 5
let y = x > 0 ? "positive" : "negative"
console.log(y) // "positive"
```

# Exercise 1

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/ZplYC6-PiAE" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Create a webpage that contains a `p` element with some text.

Add a script tag with the following code:

```javascript
const p = document.querySelector('p')

setTimeout(() => {

}, 3000)
```

After 3 seconds, the text inside the `p` element should be replaced with the text `3 seconds elapsed`.

## Hint {#exercise-1-hint}

<details>
	<summary>How do I change the text of an element?</summary>

You can change the text of an element by setting the `textContent` property:

```javascript
const p = document.querySelector('p')
p.textContent = 'Hello world'
```

</details>

## Solution {#exercise-1-solution}

<details>
	<summary>Show the answer</summary>

```javascript
const p = document.querySelector('p')

setTimeout(() => {
	p.textContent = '3 seconds elapsed'
}, 3000)
```

</details>

<details>
	<summary>Walkthrough Video</summary>
    	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/t0s9JjVT8pE" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		></iframe>
	</div>
</details>
