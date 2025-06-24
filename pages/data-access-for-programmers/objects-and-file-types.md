---
title: Objects and File Types
subtitle: Data Access for Programmers
hideNav: false

live: https://fvtc.software/appel/data-access-for-programmers/objects-and-file-types
---

# Objects and File Types

Now that you have an understanding of primitive data-types, we can move on to more complex data-types. The most common (non-primitive) data-type is called an object. 

## What are Objects?

Objects are used to represent real-world things. For example, a person or a car. Properties are attributes that describe the object. For example, a person might have a first name, last name, and an address, while a car has a make, model, and a year.

The following videos will introduce you to objects.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe
			src="https://www.youtube.com/embed/1xVC54ozhRU"
			width="100%" height="100%" frameborder="0" allowfullscreen
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
		></iframe>
	</div>
</details>

## Object Examples

Let's take a look at a couple of examples. The first one is written in C#, and the second one is written in JavaScript.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe
			src="https://www.youtube.com/embed/SpQgxu8XVTY"
			width="100%" height="100%" frameborder="0" allowfullscreen
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
		></iframe>
	</div>
</details>

Here's the C# code:

```csharp
// First we define a class

public class Student
{
	public int ID { get; set; }
	public string FirstName { get; set; }
	public string LastName { get; set; }
	public string City { get; set; }
	public string State { get; set; }
	public string Phone { get; set; }
}

// Then we create an object

Student john = new Student();
john.ID = 120333241;
john.FirstName = "John";
john.LastName = "Smith";
john.City = "Appleton";
john.State = "WI";
john.Phone = "920-722-5013";
```

And here's the JavaScript code:

```javascript
const john = {
	ID: 120333241,
	FirstName: "John",
	LastName: "Smith",
	City: "Appleton",
	State: "WI",
	Phone: "920-722-5013"
}
```

## Running Demo 1

Let's take a look at an object used in a JavaScript program.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe
			src="https://www.youtube.com/embed/BOeEJ8HKyCc"
			width="100%" height="100%" frameborder="0" allowfullscreen
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
		></iframe>
	</div>
</details>

```javascript
// Create a Car instance (object)

const audi = {
	"model": "R8",
	"price": 100000.00
}

console.log(audi.model);
console.log(audi.price);

// Create another object

const toyota = {
	"model": "Supra",
	"price": 45000.00
}

console.log(toyota.model);
console.log(toyota.price);
```

## Object Properties

An object's properties are often primitive data-types, as seen in the previous example. However, an object's properties can also be other objects. Let's take a look at an example.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe
			src="https://www.youtube.com/embed/leXkMbThfy8"
			width="100%" height="100%" frameborder="0" allowfullscreen
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
		></iframe>
	</div>
</details>

```javascript
const john = {
	ID: 120333241,
	FirstName: "John",
	LastName: "Smith",
	City: "Appleton",
	State: "WI",
	Phone: "920-722-5013"
	Course: {
		Title: "Data Access for Programmers",
		Instructor: "Ryan Appel",
		Room: "Appleton Campus C125",
		Credits: 3,
		Start: {
			Date: "8/24",
			Time: "10:30"
		}
	}
}
```

# Persisting Data

Most computer applications use data persistence, in one form or another. When you save a file, you are persisting data. When you save a game, you are persisting data. When you sign up for a website, again, you are persisting data.

Persisting data is going to be a large part of what we do in this course. Let's take a closer look.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe
			src="https://www.youtube.com/embed/fg0EvwCUUW4"
			width="100%" height="100%" frameborder="0" allowfullscreen
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
		></iframe>
	</div>
</details>

## Ways to Persist Data

There are many ways to persist data. Three of the most common ways are:

1. Files
2. Databases
3. Key Value Stores

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe
			src="https://www.youtube.com/embed/O2I8OQSBnC0"
			width="100%" height="100%" frameborder="0" allowfullscreen
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
		></iframe>
	</div>
</details>

## File Storage

The first way to persist data is by using files. Files are the most common way to persist data. They are easy to use, and they are supported by every programming language.

### CSV Files

One common file type is called a CSV file. CSV stands for "comma-separated values". CSV files are used to store tabular data. They are easy to read and write, and they are supported by major every programming language.

Here's an example of a CSV file:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe
			src="https://www.youtube.com/embed/69G8Ts69PDo"
			width="100%" height="100%" frameborder="0" allowfullscreen
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
		></iframe>
	</div>
</details>

You can see/download the CSV file [here](https://github.com/RDAppel/courses/blob/master/support-files/dap/objects-and-file-types/example.csv).


### XML Files

Another common file type is called an XML file. XML stands for "extensible markup language". XML files are used to store hierarchical data.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe
			src="https://www.youtube.com/embed/PCt51OMi4v4"
			width="100%" height="100%" frameborder="0" allowfullscreen
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
		></iframe>
	</div>
</details>

You can see/download the XML file [here](https://github.com/RDAppel/courses/blob/master/support-files/dap/objects-and-file-types/example.xml).

### JSON Files

The last common file type is called a JSON file. JSON stands for "JavaScript Object Notation". JSON files are also used to store hierarchical data. They are very similar to XML files, but they are easier to read and write, and they are a little more compact.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe
			src="https://www.youtube.com/embed/a-LexOly3Jo"
			width="100%" height="100%" frameborder="0" allowfullscreen
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
		></iframe>
	</div>
</details>

You can see/download the JSON file [here](https://github.com/RDAppel/courses/blob/master/support-files/dap/objects-and-file-types/example.json).

# Exercise 1

Time to create your first object! Create a CSV, XML, and JSON file that contains the following information:

```ebnf
Course ID: 10-152-168
Course Name: Data Access for Programmers
Instructor Name: Ryan Appel
Credits: 3
```

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe
			src="https://www.youtube.com/embed/ptJgn9UdjdM"
			width="100%" height="100%" frameborder="0" allowfullscreen
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
		></iframe>
	</div>
</details>

The solution files for this demo can be found here: [CSV File](https://github.com/RDAppel/courses/blob/master/support-files/dap/objects-and-file-types/exercise1.csv), [XML File](https://github.com/RDAppel/courses/blob/master/support-files/dap/objects-and-file-types/exercise1.xml), [JSON File](https://github.com/RDAppel/courses/blob/master/support-files/dap/objects-and-file-types/exercise1.json).

# RESTful APIs

REST stands for "representational state transfer". It's a software architectural style that defines a set of constraints to be used for creating web services. A RESTful API is an application program interface (API) that uses HTTP requests to GET, PUT, POST and DELETE data. In this course, we will be using RESTful APIs to retrieve data from the internet.

## Star Wars API Example

Let's take a look at an example.

> [!NOTE] swapi.dev is no longer accessable. A new version of the API is available at [https://swapi.tech/](https://swapi.tech/). I have updated the links on this page, but the video still uses the old API. The new API is very similar, so you should be able to follow along with the video.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe
			src="https://www.youtube.com/embed/DUQkz-JgjV4"
			width="100%" height="100%" frameborder="0" allowfullscreen
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
		></iframe>
	</div>
</details>

I recommend that you take a few minutes to check out the [Star Wars API](https://swapi.tech/). It's a great example, and as I mentioned in the video, it's near and dear to my heart.

## Running Demo 2

Let's take a look at a JavaScript program that uses a RESTful API to retrieve the text crawl from a few of the Star Wars movies.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe
			src="https://www.youtube.com/embed/oZjavtjEOfQ"
			width="100%" height="100%" frameborder="0" allowfullscreen
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
		></iframe>
	</div>
</details>

# Exercise 2

Search the internet for a RESTful API that interests you, and determine if it:
- Supports JSON/XML/Other?
- Free/Paid?
- What kind of application would you build with it?

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe
			src="https://www.youtube.com/embed/9Y3-2-6DSrE"
			width="100%" height="100%" frameborder="0" allowfullscreen
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
		></iframe>
	</div>
</details>

# Review Questions

1. Why do we use objects?
<details>
  <summary>Answer</summary>
  Objects are used to represent real-world things. They combine all of the attributes of that entity, making it easier to work with.
</details>

2. What is a property?
<details>
  <summary>Answer</summary>
  A property is a value that is stored in an object. It's also called a field or attribute.
</details>

3. True or False: An object's properties can be other objects.
<details>
  <summary>Answer</summary>
  True
</details>

4. What are the three common ways to persist data?
<details>
  <summary>Answer</summary>
  Files, databases, and key-value stores.
</details>

5. What is a CSV file?
<details>
  <summary>Answer</summary>
  A CSV file is a comma-separated values file. It's used to store tabular data.
</details>

6. What is an XML file?
<details>
  <summary>Answer</summary>
  An XML file is an extensible markup language file. It's used to store hierarchical data.
</details>

7. What is a JSON file?
<details>
  <summary>Answer</summary>
  A JSON file is a JavaScript object notation file. It's similar to an XML file, but it's less verbose.
</details>

8. What does REST stand for?
<details>
  <summary>Answer</summary>
  Representational state transfer.
</details>

9. What is a RESTful API?
<details>
  <summary>Answer</summary>
  A RESTful API is an application program interface (API) that uses HTTP requests to GET, PUT, POST and DELETE data.
</details>

10. What are some examples of RESTful APIs?
<details>
  <summary>Answer</summary>
  The Star Wars API, the Marvel API, the Pokemon API, the Chuck Norris API, etc.
</details>
