---
title: Abstract Classes
subtitle: Computer Programming, C++
hideNav: false

live: https://fvtc.software/appel/computer-programming-cpp/abstract-classes
---

# Abstract Classes

As you saw in the last unit, we can use inheritance to create a hierarchy of classes. This allows us to create a base class that defines common behavior, and then create derived classes that add or modify that behavior.

Sometimes, we want to create a base class that defines behavior, but we don't want to allow objects of that class to be created. We only want to use the class as a base for other classes. In C++, we can do this by creating an **abstract class**.

We also saw in the last unit that we can use virtual, and pure virtual functions to create polymorphic behavior. This is a key feature of abstract classes. Take a look:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/yX7oOo5mTFo" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Again, the way to make a class abstract is to declare a pure virtual function. This is done by adding `= 0` to the end of the function declaration. Here is an example:

```cpp
class Animal
{
public:
	virtual void Move() = 0;
};
```

# Calling Parent Methods

When you have a derived class that overrides a virtual function, you can still call the parent class's version of the function. This is done by using the scope resolution operator `::`. Let's take a look:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/-27vCi6gy4k" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code that we added to the `Dog` class in the video:

```cpp
virtual void Display() const
{
	std::cout << "Dog: ";
	Animal::Display(); // Call the parent class's version of Display
}
```

# Interfaces

In C++, we can create an interface by using an abstract class that only contains pure virtual functions. This is a way to define a contract that other classes must follow. Take a look:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/0H5zcY09KYw" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is an example of an interface for something that can be charged:

```cpp
#pragma once

class IChargeable
{
public:

	virtual void ChargeBattery() = 0;

};
```

And here is an example of a class that implements the interface:

```cpp
#pragma once

#include "Cat.h"
#include "IChargeable.h"

// RobotCat is a Cat (inheritance) that can be charged (implementation)
class RobotCat : public Cat, public IChargeable
{

private:

	int m_batteryPercent = 99;

public:

	virtual void Speak() const { std::cout << GetName() << " says beep boop meow!\n"; }

	virtual void ChargeBattery()
	{
		m_batteryPercent++;
		if (m_batteryPercent > 100) m_batteryPercent = 100;
	}

};
```

# Exercise 1

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/8YLIS0i-DwA" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

For this exercise, create an interface called `IPowerable` that has a pure virtual function called `PowerOn`, and a pure virtual function called `PowerOff`. Then, modify your `RobotCat` class to implement the `IPowerable` interface.

## Hints {#exercise-1-hints}

<details>
	<summary>How do I create an interface?</summary>

An interface, is just a class that contains only pure virtual functions. For example:

```cpp
class IMyInterface
{
public:

	virtual void MyFunction() = 0;

};
```

</details>

<details>
	<summary>How do I implement an interface?</summary>

To implement an interface, you just need to add the interface to the list of base classes for your class. For example:

```cpp
class MyClass : public IMyInterface
{
public:

	virtual void MyFunction() { std::cout << "MyFunction called!\n"; }

};
```

</details>

## Solution {#exercise-1-solution}

<details>
	<summary>Show the Answer</summary>

```cpp
#pragma once

class IPowerable
{
public:

	virtual void PowerOn() = 0;
	virtual void PowerOff() = 0;

};
```

```cpp
#pragma once

#include "Cat.h"
#include "IPowerable.h"

// add the IPowerable interface to the list of base classes
class RobotCat : public Cat, public IChargeable, public IPowerable
{

private:

	int m_batteryPercent = 99;
	bool m_isPoweredOn = false;

public:

	virtual void Speak() const { std::cout << GetName() << " says beep boop meow!\n"; }

	virtual void ChargeBattery()
	{
		m_batteryPercent++;
		if (m_batteryPercent > 100) m_batteryPercent = 100;
	}

	virtual void PowerOn() { m_isPoweredOn = true; }
	virtual void PowerOff() { m_isPoweredOn = false; }

};
```

</details>

<details>
	<summary>Walkthrough Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/hDuVTya0qrQ" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>