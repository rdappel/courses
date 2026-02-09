# AGENTS.md - AI Agent Instructions for Course Content Repository

## Repository Overview

This repository contains course materials for Ryan Appel's programming courses. The content is organized as Markdown files with front matter (YAML), structured in a course curriculum format with lessons, assignments, and resources.

### Repository Purpose

- Educational platform for multiple programming courses
- Deployment across live (`fvtc.software`) and dev (`localhost:3006`) environments
- Version control and collaboration via GitHub (`rdappel/courses`)

### Active Courses

1. **Version Control Essentials** (`vce/`) - Git and version control fundamentals
2. **Data Access for Programmers** (`dap/`) - SQL, databases, and data modeling
3. **Modern JavaScript** (`mjs/`) - JavaScript fundamentals and DOM manipulation
4. **Advanced JavaScript** (`ajs/`) - React, Hooks, State Management, and routing
5. **Computer Programming C++** (`cpp/`) - Object-oriented programming in C++
6. **C# Introduction to Programming** (`cs-intro/`) - C# basics
7. **C# Intermediate Programming** (`cs-intermed/`) - Advanced C# concepts

## Directory Structure

```plaintext
courses/
├── pages/                              # All course content
│   ├── index.md                        # Main course listing page
│   ├── advanced-javascript/            # React/JavaScript course
│   │   ├── index.md                    # Course overview and week schedule
│   │   ├── [lesson files].md           # Individual lesson pages
│   │   └── assignments/                # Assignment specifications
│   |       └── [assignment files].md   # Individual assignments
│   ├── data-access-for-programmers/
│   ├── modern-javascript/
│   ├── computer-programming-cpp/
│   ├── csharp-introduction-to-programming/
│   ├── csharp-intermediate-programming/
│   ├── version-control-essentials/
│   ├── php/
│   └── general/
├── support-files/                         # Supporting materials by course abbrev
│   ├── ajs/   (Advanced JavaScript)
│   ├── cpp/   (C++)
│   ├── cs-intermed/ (C# Intermediate)
│   ├── cs-intro/    (C# Introduction)
│   ├── dap/   (Data Access for Programmers)
│   ├── mjs/   (Modern JavaScript)
│   └── vce/   (Version Control Essentials)
└── .vscode/                        # VS Code configuration
    └── md.code-snippets          # Markdown snippet definitions
```

## File Format Standards

### Front Matter (YAML)

All `.md` files follow this standard structure:

```yaml
---
title: [Course/Lesson Title]
subtitle: [Author or Course Name]
[optional fields]:
  - hideNav: boolean
  - live: https://...
  - dev: http://localhost:...
  - repo: https://github.com/...
---
```

### Content Structure

- **Index Files**: Course overview with weekly breakdowns
- **Lesson Files**: Educational content with explanations and examples
- **Assignment Files**: Detailed specifications with requirements and acceptance criteria

### Common Markdown Elements

- `<details>` blocks for expandable video content
- Link format: `[Link Text](./course/path/to/page)`
- Headers: H1 for main title, H2 for sections, H3+ for subsections
- Code blocks with language specification
- Specification sections with numbered requirements

## Key Content Patterns

### Assignment Structure

1. **Title** - Assignment number and topic
2. **Video Section** - Optional expandable YouTube embed
3. **Specifications** - Numbered requirements
4. **Acceptance Criteria** - What constitutes completion
5. **Additional Resources** - Links to relevant lesson content

### Lesson Structure

1. **Title** - Topic and context
2. **Overview** - What students will learn
3. **Explanation** - Detailed content with examples
4. **Code Examples** - Working code snippets
5. **Practice Exercises** - Interactive learning opportunities
6. **Key Takeaways** - Summary of main points

### Exercise Hint Format

- Hints for exercises should use a <details> block for each hint, with a descriptive <summary> for the hint's focus (e.g., "How do I start?", "How do I access notifications?").
- Place all hint <details> blocks under a `## Hints {#exercise-x-hints}` header, where `x` is the exercise number if applicable.
- Example:

```markdown
## Hints {#exercise-1-hints}

<details>
  <summary>How do I start?</summary>

Hint content here.

</details>
```

## VS Code Configuration

### Code Snippets

- Location: `.vscode/md.code-snippets`
- Purpose: Quick templates for Markdown content creation
- Usage: Type snippet prefix in `.md` files for rapid content generation

## Important Conventions

### URLs and Links

- **Live Site**: `https://fvtc.software/appel/[course-slug]`
- **Dev Server**: `http://localhost:3006/appel/[course-slug]`
- **GitHub Repo**: `https://github.com/rdappel/courses`

### Course Slug Mappings

- `advanced-javascript` → Advanced JavaScript course
- `data-access-for-programmers` → Data Access course
- `modern-javascript` → Modern JavaScript course
- `computer-programming-cpp` → C++ course
- `version-control-essentials` → Git/Version Control course
- `csharp-introduction-to-programming` → C# Intro course
- `csharp-intermediate-programming` → C# Intermediate course

## Git Configuration

- User: Ryan Appel
- Standard ignore patterns: Ignore `*_fail/` directories (failed attempts)

## Common Tasks for AI Agents

### Content Creation Tasks

1. **Create new lesson pages** - Follow format in existing lesson files
2. **Create assignments** - Use assignment template structure
3. **Update course index** - Add new lessons to week breakdowns
4. **Add support materials** - Place in `support-files/[course-abbrev]/`

### Content Modification Tasks

1. **Update front matter** - Ensure YAML validity
2. **Refactor lessons** - Maintain structure while improving clarity
3. **Update links** - Verify all internal links remain valid
4. **Add examples** - Include code blocks with language specification

### Quality Assurance Tasks

1. **Verify link integrity** - Check all `[text](path)` references are valid
2. **Validate YAML** - Ensure front matter is properly formatted
3. **Check consistency** - Verify naming conventions across files
4. **Test content** - Validate code examples are accurate

## Notes for AI Agents

### When Creating/Editing Content

- **Always preserve YAML front matter** - It controls page metadata and displays
- **Maintain relative links** - Use `./course/path` format for internal navigation
- **Follow existing patterns** - Match the structure and style of similar existing files
- **Verify course abbreviations** - Use correct mapping between course names and `support-files/` directories
- **Test links before committing** - Ensure references are accurate

### When Working with Assignments

- Assignments are numbered sequentially per course
- Include clear specifications with acceptance criteria
- Reference related lesson materials
- Consider adding practice exercises before main assignment

### When Updating Index Files

- Index files control course navigation
- Format: `[Link Text](./course/path)` with brief summaries
- Structure by week/module with clear hierarchies
- Keep summaries concise (one sentence preferred)

### File Naming Conventions

- Use kebab-case for all filenames
- Spell out words (no abbreviations in filenames)
- Be descriptive but concise
- Examples: `theme-switcher.md`, `data-fetching-with-useeffect.md`

## Deployment Information

- **Repository**: Public GitHub repository for version control
- **Live Environment**: FVTC server at `fvtc.software`
- **Development**: Local environment on `localhost:3006`
- **Build Process**: Likely static site generator (content appears to support SSG)

## Technology Stack

- **Content Format**: Markdown
- **Front Matter**: YAML
- **Version Control**: Git via GitHub
- **Development Server**: Node.js based (`localhost:3006`)
- **Editor Config**: VS Code snippets for rapid content creation

---

## Quick Reference for Common Agent Tasks

| Task | Key Files | Pattern |
| ---- | --------- | ------- |
| Add new lesson | `pages/[course]/[lesson].md` | Copy structure from existing lesson |
| Add assignment | `pages/[course]/assignments/[name].md` | Use assignment specification template |
| Update course nav | `pages/[course]/index.md` | Add entry to appropriate week section |
| Add support files | `support-files/[abbrev]/` | Organize by course abbreviation |
| Fix links | Any `.md` file | Verify `./course/path` references exist |

---

**Last Updated**: January 29, 2026
**Repository Owner**: Ryan Appel
