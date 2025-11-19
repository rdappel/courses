---
title: Inheritance and Polymorphism
subtitle: Computer Programming C++
hideNav: false

live: https://fvtc.software/appel/computer-programming-cpp/inheritance-and-polymorphism
---

# Inheritance and Polymorphism

In this unit, we will explore two important concepts in object-oriented programming: inheritance and polymorphism. These concepts allow us to create more flexible and reusable code by defining relationships between classes and allowing objects to be treated as instances of their base class.

We are going to continue this lesson by building on top of the "ClassesDemo" solution that we created in the last unit. If you don't have that code available, you can fork and clone the following repository: [CPP-ClassesDemo](https://github.com/FVTC/RDA.ClassesDemo).

Before we get started with inheritance and polymorphism, let's go over the Pillars of Object-Oriented Programming.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/6s00ystgwOs" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

1. **Encapsulation** - The bundling of data and the methods that operate on that data into a single unit.

2. **Inheritance** - Extend the functionality of a class by using a relationship.

3. **Polymorphism** - Allows objects to be treated as instances of their base type.

4. **Abstraction** - Hiding the implementation details of a class from the user.


# Inheritance

Inheritance is a fundamental concept in object-oriented programming that allows us to create new classes based on existing classes. The new class, called a derived class, inherits the properties and behaviors of the existing class, called a base class. This allows us to reuse code and define relationships between classes.

This video provides an overview of inheritance in C++:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/ZcSMh7O2xBw" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code in `Dog.h`:

```cpp
#pragma once

#include "Animal.h"

class Dog : public Animal
{
};
```

And here is the code that we added to `Main.cpp`:

```cpp
#include "Dog.h" // changed from "Animal.h"

Dog daisy;
daisy.SetName("Daisy");
daisy.SetAge(7);
daisy.Display();
```

## Extending the Base Class

When we create a derived class, we can extend the functionality of the base class by adding new properties and methods. In the example above, the `Dog` class inherits the `Name` and `Age` properties from the `Animal` class, but it also has its own properties and methods that are specific to dogs.

Let's add the ability for a dog to bark:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/gfyZ_x3KXdg" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code that we added to `Dog.h`:

```cpp
void Speak() const { std::cout << GetName() << " says woof!\n"; }
```

And in `Main.cpp`:

```cpp
daisy.Speak();
```

# Exercise 1

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/O4a6mQm6CP8" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

For this exercise, you will create a new class called `Cat` that inherits from the `Animal` class. The `Cat` class should have a method called `Speak` that prints "Meow!" to the console.

## Hints {#exercise-1-hints}

<details>
	<summary>How do I create a class that inherits from another class?</summary>

Use the following syntax to create a class that inherits from another class:

```cpp
class DerivedClass : public BaseClass
{
};
```

</details>

## Solution {#exercise-1-solution}

<details>
	<summary>Show the Answer</summary>

```cpp
#pragma once

#include "Animal.h"

class Cat : public Animal
{

public:

	void Speak() const { std::cout << GetName() << " says meow!\n"; }
};
```

</details>

<details>
	<summary>Walkthrough Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/FsFgbEggoWE" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

# Constructors

When we create a derived class, we can also define constructors for the derived class. These constructors can initialize the properties of the derived class and call the constructor of the base class to initialize the properties of the base class.

Take a look at an example:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/i7XwAH2KyjM" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here are the constructors that we added to `Cat.h`:

```cpp
Cat() { }
Cat(const std::string name, const int age)
	: Animal(name, age) { }
```

# Polymorphism

Polymorphism is another key concept in object-oriented programming that allows us to treat objects of different classes as instances of a common base class. This allows us to write code that is more flexible and reusable, as we can work with objects at a higher level of abstraction.

This video provides an overview of polymorphism in C++:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/gShraoZj2K8" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the updated code in `Main.cpp`:

```cpp
Cat luke("Luke", 8);
//luke.Move();

std::vector<Animal*> animals;
animals.push_back(new Cat("Whiskers", 5));
animals.push_back(&luke);

Dog d;
d.SetName("Daisy");
d.SetAge(7);
animals.push_back(&d);

for (Animal* pAnimal : animals)
{
	pAnimal->Display();
}
```

## Virtual Methods

To enable polymorphism in C++, we need to use virtual methods. A virtual method is a method that is declared in a base class and can be overridden in a derived class. When we call a virtual method on an object, the method that is called is determined by the type of the object at runtime.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/9yhN8LR7nGw" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is our virtual `Speak` method in `Animal.h`:

```cpp
// virtual means method CAN be overridden
virtual void Speak() const { }
```

> [!TIP] I generally make all of my methods virtual in a base class. This allows me to override them in derived classes if needed. If I don't need to override a method, I can just leave it empty in the derived class. There is a small performance cost to making a method virtual, but it is usually negligible.

> [!WARNING] If you use `virtual` on a method, you should also make the destructor virtual. This is important when you are deleting objects through a pointer to the base class. If the destructor is not virtual, the derived class destructor will not be called, and you may have memory leaks.

## Pure Virtual Methods

In some cases, we want to define a method in a base class that must be overridden in a derived class. We can achieve this by using pure virtual methods. A pure virtual method is a method that is declared in a base class but has no implementation. Any class that inherits from the base class must provide an implementation for the pure virtual method.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/egwcycegvMQ" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is our pure virtual `Move` method in `Animal.h`:

```cpp
// A pure-virtual method MUST be overridden
virtual void Move() const = 0;
```

# Exercise 2

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/7HDF_ryag9U" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

For this exercise, you will create a new class called `RobotCat` that inherits from the `Cat` class. The `RobotCat` class should override the `Speak` method to print "beep boop meow!" to the console.

## Hints {#exercise-2-hints}

<details>
	<summary>How do I override the Speak method in the RobotCat class?</summary>

Use the following syntax to override the Speak method in the RobotCat class:

```cpp
void Speak() const { std::cout << GetName() << " says beep boop meow!\n"; }
```

</details>

## Solution {#exercise-2-solution}

<details>
	<summary>Show the Answer</summary>

RoboCat.h:

```cpp
#pragma once

#include "Cat.h"

class RobotCat : public Cat
{

public:

	void Speak() const { std::cout << GetName() << " says beep boop meow!\n"; }

};
```

Main.cpp:

```cpp
RobotCat rc;
rc.SetName("Buster");
rc.Speak();
```

</details>

<details>
	<summary>Walkthrough Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/vQRnkpvwpGk" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

