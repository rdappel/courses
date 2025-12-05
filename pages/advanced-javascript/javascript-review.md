---
title: JavaScript Review
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript
dev: http://localhost:3006/appel/advanced-javascript
repo: https://github.com/rdappel/courses
---

# Course Overview

Welcome to the Advanced JavaScript course! The focus of this course is React and using JavaScript Frameworks to build modern web applications. However, before we dive into React, we need to ensure you have a solid understanding of JavaScript fundamentals.

For most of you, it's been a few weeks (or months) since you last wrote JavaScript. So, the focus of this first week is to review the JavaScript concepts you learned in the Modern JavaScript course. This will help you get back into the swing of things and prepare you for the more advanced topics we'll cover later in the course.

# Necessary Software

Before we start reviewing, please make sure you have all of the same software installed that you did for the Modern JavaScript course. If you need help with this, please refer to the [Software Used in this Course](https://fvtc.software/appel/modern-javascript/getting-started#software-used-in-this-course) section of the Modern JavaScript course.


# JavaScript Review

In this section, we'll review some of the key concepts from the Modern JavaScript course. This will include functions, array methods, and higher-order functions. If you need a refresher on any of these topics, please refer to the [Modern JavaScript course content](https://fvtc.software/appel/modern-javascript).

## Array Functions

Let's start by reviewing some common array functions in JavaScript. The ones we'll focus on are map, filter, and reduce. These will be essential when working with arrays in React.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen></iframe>
    </div>
</details>

Here is the code from the video:

```javascript
const numbers = [ 1, 2, 3, 4, 5 ]

// Function to double a number
const double = n => n * 2

// Use map to get a new array with doubled values
const doubledNumbers = numbers.map(double)
console.log(doubledNumbers)

// Function to check if a number is even
const isEven = n => n % 2 === 0

// Use filter to get only even numbers
const evenNumbers = numbers.filter(isEven)
console.log(evenNumbers)

// Reducer function that sums two numbers
const sum = (n1, n2) => n1 + n2

// Use reduce to sum all numbers in the array
const sum = numbers.reduce(sum, 0)
console.log(sum)
```

## Destructuring Arrays and Objects

Destructuring is a convenient way of extracting multiple values from data stored in objects and arrays.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen></iframe>
    </div>
</details>

Here is the code from the video:

```javascript
const array = [ 10, 20, 30, 40 ]

const object = {
    name: "Alice",
    age: 25,
    city: "New York"
}

// Destructuring an array
const [ first, _, third ] = array
console.log(first, third) // Output: 10 30

// Destructuring an object
const { name, age } = object
console.log(name, age) // Output: Alice 25
```

I find these especially useful when objects or arrays are passed as function parameters.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen></iframe>
    </div>
</details>

Here is the code from the video:

```javascript
const getWeather = async () => {
    return new Promise(resolve => {
        const weatherData = {
            city: "San Francisco",
            state: "CA",
            current: {
                temperature: 68,
                condition: "Sunny",
                icon: "sunny.png",
                high: 72,
                low: 55
            },
            forecast: {
                days: 5,
                data: [
                    { day: "Monday", high: 70, low: 50 },
                    { day: "Tuesday", high: 68, low: 48 },
                    { day: "Wednesday", high: 65, low: 47 },
                    { day: "Thursday", high: 66, low: 49 },
                    { day: "Friday", high: 67, low: 50 }
                ]
            }
        }

        setTimeout(() => resolve(weatherData), 1000)
    })
}

const logTemperature = ({ current }) => {
    console.log(`The current temperature is ${current.temperature}°F.`)
}

const logTuesdayHigh = ({ forecast: { data } }) => {
    const tuesday = data.find(({ day }) => day === "Tuesday")
    console.log(`The high temperature on Tuesday is ${tuesday.high}°F.`)
}

const weather = await getWeather()
logTemperature(weather)
logTuesdayHigh(weather)
```

## Ternary Operator

The ternary operator is a concise way to perform conditional expressions in JavaScript. It is often used as a shorthand for the if-else statement.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen></iframe>
    </div>
</details>

Here is the code from the video:

```javascript
const age = 18

// Set canVote based on age using the ternary operator
const canVote = age >= 18 ? "Yes" : "No"
console.log(canVote)
```

In this example, the ternary operator checks if the age is 18 or older. If true, it returns "Yes"; otherwise, it returns "No".