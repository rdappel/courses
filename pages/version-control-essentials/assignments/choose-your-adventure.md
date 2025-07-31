---
title: Assignment 8 - Final Project
subtitle: Version Control Essentials
hideNav: false

live: https://fvtc.software/appel/version-control-essentials/assignments/choose-your-adventure
dev: http://localhost:3006/appel/version-control-essentials/assignments/choose-your-adventure
repo: https://github.com/rdappel/courses
---

# Final Project: Choose Your Own Adventure

For your final project, you will work with a partner to create an interactive "Choose Your Own Adventure" story using Markdown and demonstrate all the Git skills you've learned throughout this course.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

# Project Overview

You will create an interactive story where readers make choices that lead to different outcomes. The story will be built using Markdown files that link to each other, creating a branching narrative experience.

**Example Story:** [https://github.com/FVTC/choose-your-adventure/blob/master/space-battles/_start-here.md](Space Battles - Episode IV: A New Spark)

**Project Repository**: [https://github.com/fvtc/choose-your-adventure](https://github.com/fvtc/choose-your-adventure)

> [!NOTE] Make sure to read the README file in the repository carefully - it explains how the choose-your-own-adventure format works and provides examples.

# Instructions

## Part 1: Find a Partner and Set Up

1. **Find a partner**: Use the [Teams channel](https://teams.microsoft.com/l/channel/19%3Aaa6ad81494264deba8b288e24f4091de%40thread.tacv2/Find%20a%20Partner?groupId=db69ef1e-3c6a-4ac8-8636-f800a33a72ab&tenantId=ae888c53-4d60-47da-a75a-c8a10f1d47b0) for this course to find a partner. Make sure to specify that you are looking for a partner for the Final Project.

2. **Decide who will create the fork**: One partner should fork the [choose-your-adventure repository](https://github.com/fvtc/choose-your-adventure) to their GitHub account.

3. **Add your partner as a collaborator**: The person who created the fork should add their partner as a collaborator:
   - Go to your forked repository on GitHub
   - Click "Settings" → "Manage access" 
   - Invite your partner by their GitHub username or email address

4. **Both partners clone the repository**: Both partners should clone the forked repository to their local machines.

## Part 2: Plan Your Story

Before you start coding, plan your story together:

1. **Choose a theme**: Decide on a setting/theme for your story (adventure, mystery, sci-fi, fantasy, etc.)
   
   > [!IMPORTANT] Keep your story appropriate for school - no inappropriate content or offensive material. Some action/adventure violence is acceptable (think Star Wars level).

2. **Create a story outline**: Plan out at least 12-15 different "scenes" or pages for your story. Your story should have:
   - A clear beginning
   - Multiple branching paths with meaningful choices
   - At least 3 different endings
   - Interesting consequences for different decisions

3. **Divide the work**: Decide who will work on which parts of the story, but make sure both partners contribute to the actual writing and Git operations.

## Part 3: Development Workflow

Use proper Git workflow throughout your development:

### Initial Setup

1. **Create a dev branch** from main:
```bash
git checkout -b dev
```

2. **Plan your branching strategy**: You'll create feature branches for different parts of your story.

### Feature Development

For each major section of your story, use this workflow:

1. **Create feature branches** from dev (not main):
```bash
git checkout dev
git checkout -b feature/opening-scene
```

2. **Work on your story sections**: Create and edit Markdown files for your story.

3. **Use proper commit messages**: Write clear, descriptive commit messages:
```bash
git commit -m "Add opening scene with character introduction"
git commit -m "Create forest path choice with two outcomes"
```

4. **Merge using the cautious approach**:
   - First merge dev into your feature branch
   - Test your story links
   - Then merge feature branch into dev

5. **Regularly push your changes** and **pull your partner's updates**

6. **Use stashing when needed** if you need to switch contexts quickly

### Collaboration Requirements

> [!IMPORTANT] Both partners must contribute meaningfully to the project. I expect to see commits from both team members throughout the development process. No "I helped my partner but they submitted it" - both partners must have visible Git contributions.

## Part 4: Story Requirements

Your story must include:

- **At least 12-15 different scenes/pages**
- **Multiple branching paths** (not just linear)
- **At least 3 different endings**
- **Proper Markdown formatting** (headers, links, emphasis, etc.)
- **Clear navigation** between scenes
- **A starting point**
- **Consistent file naming** (lowercase, hyphens for spaces)

### Example Story Structure:
```
start.md → choice-1.md → path-a.md → ending-1.md
         → choice-2.md → path-b.md → ending-2.md
                      → path-c.md → ending-3.md
```

## Part 5: Technical Requirements

Your project must demonstrate these Git skills:

- [x] **Branching**: Use dev branch and feature branches
- [x] **Merging**: Use cautious merge approach  
- [x] **Collaboration**: Both partners making commits
- [x] **Pull Requests**: Create a PR to the original repository
- [x] **Proper Commits**: Clear, descriptive commit messages
- [x] **Conflict Resolution**: Handle any merge conflicts properly
- [x] **Remote Operations**: Pushing, pulling, and syncing work

## Part 6: Final Steps

1. **Merge dev into main** when your story is complete:
```bash
git checkout main
git merge dev
```

2. **Push your final version**:
```bash
git push origin main
```

3. **Create a pull request** to the original `fvtc/choose-your-adventure` repository

4. **Test your story thoroughly**: Make sure all links work and lead to the correct scenes

# Submission

Submit the following in Blackboard:

1. **URL of your forked repository**

2. **URL of your pull request** to the original repository

3. **Git log output**: Run `git log --oneline --graph` and paste the output

4. **Team reflection** (one submission per team): Answer these questions:
   - Describe how you divided the work between partners
   - What Git features did you find most helpful during collaboration?
   - Did you encounter any merge conflicts? How did you resolve them?
   - What was the most challenging part of the project?
   - How did using branches help organize your work?

# Assessment Criteria (40 Points Total)

## Git Skills (20 Points)
- **Branching & Merging** (5 points): Proper use of dev and feature branches with cautious merging
- **Collaboration** (5 points): Both partners have meaningful commits throughout the project
- **Commit Quality** (4 points): Clear, descriptive commit messages
- **Pull Request** (3 points): Successfully created PR to original repository
- **Repository Management** (3 points): Clean repository structure, proper pushes/pulls

## Story Content (15 Points)
- **Completeness** (6 points): At least 12-15 scenes with multiple paths and 3+ endings
- **Quality** (4 points): Engaging story with meaningful choices and consequences
- **Appropriateness** (3 points): School-appropriate content and themes
- **Navigation** (2 points): All links work correctly

## Technical Implementation (5 Points)
- **Markdown Formatting** (2 points): Proper use of headers, links, emphasis
- **File Organization** (2 points): Consistent naming and logical structure
- **Functionality** (1 point): Story flows properly from start to endings

## Bonus Opportunities (Up to 5 Extra Points)
- **Creative Use of Markdown** (2 points): Images, tables, or advanced formatting
- **Complex Story Structure** (2 points): More than 20 scenes or innovative branching
- **Exceptional Collaboration** (1 point): Evidence of sophisticated Git workflow

> [!NOTE] This project is worth 40 points and represents the culmination of everything you've learned about Git and version control. Take your time, plan well, and demonstrate your skills!

# Tips for Success

- **Start early** - don't wait until the last week
- **Communicate regularly** with your partner
- **Test your story frequently** as you build it
- **Make small, frequent commits** rather than large ones
- **Use meaningful branch names** like `feature/dragon-encounter`
- **Pull your partner's changes regularly** to avoid conflicts
- **Ask for help** if you get stuck with Git commands

Good luck, and have fun creating your adventure!
