---
title: Assignment 5 - Math Quiz
subtitle: Computer Programming C++
hideNav: false

live: https://fvtc.software/appel/computer-programming-cpp/assignments/math-quiz
---

# Assignment 5 - Math Quiz

For this assignment, you will create a math quiz program in C++. The program will generate random math problems for the user to solve. The user will be prompted to enter the answer to each problem, and the program will keep track of the user's score.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/N0cl0FQiAQg" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

You can use the following text file as a template for your questions:

```plaintext
1 + 1
2 * 3
4 / 2
5 - 3
6 + 4
8 * 2
10 / 5
7 - 2
9 + 1
3 * 5
```

## Specifications

Your program should include the following tasks:

1. Read the questions from the text file and store them in memory.

2. Generate three random math problems for the user to solve:
   - Use the questions stored in memory to generate random math problems.
   - Display the math problem to the user.
   - Prompt the user to enter the answer to the problem.
   - Use `cin` to read the user's input.

3. Save the question, along with the user's answer, to a text file called `QuizResults.txt`.
   - The file should look similar to the following example:

<div class="no-copy">

```plaintext
4 / 2 = 2
6 + 4 = 10
7 - 2 = 5
```

</div>

## Generating Random Numbers

To generate random numbers in C++, you can use the `rand()` function. Here is an example of how to generate a random number between 1 and 10:

```cpp
// call this once before you call rand()
srand(time(NULL)); // initialize the random number generator

// get a random number between 1 & 10
int randomNumber = rand() % 10 + 1;
```

> [!NOTE] It is possible that the `rand()` function will generate the same number multiple times, so the user may be asked the same question more than once. That's okay for this assignment.

## Example Output

<div class="no-copy">

```plaintext
Welcome to the Math Quiz!

Question 1: 1 + 1 =
Enter your answer: 2

Question 2: 2 * 3 =
Enter your answer: 6

Question 3: 4 / 2 =
Enter your answer: 2

Results saved to QuizResults.txt
```

</div>

The `QuizResults.txt` file should contain the questions and the user's answers:

<div class="no-copy">

```plaintext
1 + 1 = 2
2 * 3 = 6
4 / 2 = 2
```

</div>

# Submission

Create a new repository on GitHub and push your code to it. Then submit the link to your repository to Blackboard.
