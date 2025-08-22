---
title: Conditionals and Loops
subtitle: Modern JavaScript
hideNav: false

live: https://fvtc.software/appel/modern-javascript/conditionals-and-loops
---

# Conditional Statements

For the most part, conditional statements in JavaScript are similar to C#, so I won't go into much detail here. However, there are a few differences that you should be aware of.

## If, Else, and Else If Statements

In C# when you're using an `if` statement (or `else if`), the condition must be a boolean expression (resolve to either `true` or `false`). In JavaScript, values can be considered "truthy" (considered true when evaluated in a boolean context) or "falsy" (considered false). Here is a list of falsy values:

- `false` (duh)
- `0`
- `''` (empty string)
- `null`
- `undefined`
- `NaN`

For the most part, anything that is not falsy is truthy.

As example, the following code would not complie in C#, but works just fine in JavaScript:

```javascript
// assume 'someVariable' is not defined anywhere

if (someVariable) {
	// this code will be skipped in JavaScript, but would cause a compile error in C#
}
```

## Switch Statements

Switch statements are also similar to C#, so we won't be spending much time on them. Here is an example:

```javascript
const day = new Date().getDay()

switch (day) {
	case 0:
		console.log('Sunday')
		break
	case 1:
		console.log('Monday')
		break
	case 2:
		console.log('Tuesday')
		break

	// cases 3 through 5 removed for brevity...
	
	default:
		console.log('Invalid day')
}
```

# Loops

Like conditionals, loops in JavaScript are similar to C#, so we won't be spending much time on them. Here are a few examples:

## For Loop

```javascript
for (let i = 0; i < 10; i++) {
	console.log(i)
}
```

There are a couple of additional ways to write a `for` loop in JavaScript. Namely the `for-of`, and `for-in` loops. They are used to iterate over arrays and object properties, respectively. We won't be covering these because there are more concise ways to do this in JavaScript.

## While and Do-While Loops

Again, since these are so similar to C#, we won't be spending much time on them. Here are a couple of examples:

```javascript
let i = 0

while (i < 10) {
	console.log(i)
	i++
}
```

```javascript
let i = 0

do {
	console.log(i)
	i++
} while (i < 10)
```
