---
title: Getting Started with Vite
subtitle: Advanced JavaScript
hideNav: false

live: https://fvtc.software/appel/advanced-javascript
dev: http://localhost:3006/appel/advanced-javascript
repo: https://github.com/rdappel/courses
---

# What is Vite?

Vite is a modern build tool that provides a fast and efficient development experience for web applications.

## Hot Module Replacement (HMR)

Vite supports hot module replacement (HMR). This is going to be very useful for us as we develop our React applications. HMR allows you to see changes in your code immediately without having to refresh the entire page.

## Bundling

Bundling is the process of combining multiple JavaScript files into a single file. This is important for performance, as it reduces the number of HTTP requests made by the browser. Bundling also allows for minification, which reduces the size of the JavaScript file by removing whitespace and comments.

Vite uses Rollup under the hood for bundling, and it supports ES Modules out of the box.

# Getting Started with Vite

Let's turn our JavaScript files into a bundle using Vite.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

Here is the command that I ran to initialize Vite in my project:

```bash
npm create vite@latest .
```

This command creates a new Vite project in the current directory. It also installs all the necessary dependencies.

> [!NOTE] You could run `npm create vite@latest` (without the dot) to create a new project in a new directory, but then you would need to navigate into that directory before running the development server.

---

After that, I ran the following command to start the development server:

```bash
npm run dev
```

This command starts the Vite development server, which watches for changes and reloads the browser automatically.

---

After that, I ran the following command to build the project for production:

```bash
npm run build
```

