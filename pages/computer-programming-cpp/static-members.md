---
title: Static Members
subtitle: Computer Programming C++
hideNav: false

live: https://fvtc.software/appel/computer-programming-cpp/static-members
---

# Static Members

Static members are members of a class that are shared by all instances of the class. They are not associated with any particular instance of the class, but rather with the class itself. This means that they are shared by all instances of the class, and can be accessed without creating an instance of the class. In this unit, we will learn about both static member variables and static member functions.

## Static Member Variables

Static member variables are variables that are shared by all instances of a class. They are declared with the `static` keyword, and are typically used to store data that is common to all instances of the class. A common use case for static member variables is to keep track of the number of instances of a class that have been created. Let's look at an example:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/FqGDAi7NbIM" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the code from the video:

In `Animal.h`:

```cpp
static int s_count;

// in the constructors we increment the count:
Animal() { s_count++; }

// in the destructor we decrement the count:
~Animal() { s_count--; }
```

In `Animal.cpp`:

```cpp
// initialize the static member variable:
int Animal::s_count = 0;
```

In `Main.cpp`:

```cpp
#include "Dog.h"
#include "Cat.h"

int main()
{
	std::cout << Animal::s_count << "\n"; // 0
	Dog d;
	std::cout << Animal::s_count << "\n"; // 1

	{
		Dog d2;
		std::cout << Animal::s_count << "\n"; // 2
	}
	std::cout << Animal::s_count << "\n"; // 1

	Cat c;
	std::cout << Animal::s_count << "\n"; // 2

	(void)_getch();
	return 0;
}
```

## Static Member Functions

Just like with member variables, static member functions are functions that are shared by all instances of a class. They are declared with the `static` keyword, and can be called without creating an instance of the class. Static member functions are typically used to perform operations that are common to all instances of the class, and do not depend on the state of any particular instance. Take a look:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/2yLnLZtSSPg" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Here is the function we added to the `Animal` class:

```cpp
static void PrintCount()
{
	std::cout << "Animal count: " << s_count << "\n";
}
```

And here is our updated `Main.cpp`:

```cpp
#include "Dog.h"
#include "Cat.h"

int main()
{
	Animal::PrintCount(); // Animal count: 0
	Dog d;
	Animal::PrintCount(); // Animal count: 1

	{
		Dog d2;
		Animal::PrintCount(); // Animal count: 2
	}
	Animal::PrintCount(); // Animal count: 1

	Cat c;
	Animal::PrintCount(); // Animal count: 2

	(void)_getch();
	return 0;
}
```

