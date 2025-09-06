---
title: Assignment 4 - Object Timer Project
subtitle: C# Intermediate Programming
hide-nav: false

live: https://fvtc.software/appel/csharp-intermediate-programming/assignments/object-timer
dev: http://localhost:3006/appel/csharp-intermediate-programming/assignments/object-timer
repo: https://github.com/rdappel/courses
---

# Assignment 4 - Object Timer Project

Design a timer class to track the time spent on phone calls. Create a 2-tier application with one User Interface (Windows Forms App) and one Business Layer (Class Library). Use this class to time the number of hours, minutes, and seconds.

# Timer Class Requirements

## Public Properties
- **ElapsedTime** (Read Only): Returns a string in the format `Hours:Minutes:Seconds` (e.g., `12:23:34`).

> [!TIP] Use `.ToString("hh\\:mm\\:ss")` to format a TimeSpan as `Hours:Minutes:Seconds`.

## Private Fields
- `startTime` – DateTime
- `endTime` – DateTime
- `isRunning` – Boolean

## Methods
- `StartClock()`
- `StopClock()`

## Exceptions
- `StartException`
- `StopException`

# Specifications

- The class must have the above properties, methods, and exceptions.
- The application architecture must be correct (2-tier: UI and Business Layer).
- If the user attempts to stop the clock without starting, a `StopException` is raised.
- If the user attempts to start the clock when it is already running, a `StartException` is raised.
- The elapsed time can be read at any time while the clock is running.
- Use proper control naming conventions.
- Include appropriate comments in your code.

> [!NOTE] There is no `Reset` method requirement. To reset the timer, stop it and start it again.

# Extra Credit (10 Points)

Add a split time function that displays split times (time since beginning or last split time). Extra credit will only be allowed if the base functionality of the application is working correctly.

# Submission

Push your code to the Azure DevOps repository and submit the URL to Blackboard.
