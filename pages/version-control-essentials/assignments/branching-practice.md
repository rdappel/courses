---
title: Assignment 6 - Branching Practice
subtitle: Version Control Essentials
hideNav: false

live: https://fvtc.software/appel/version-control-essentials/assignments/branching-practice
dev: http://localhost:3006/appel/version-control-essentials/assignments/branching-practice
repo: https://github.com/rdappel/courses
---

# Assignment 6 - Branching Practice

For this assignment, you will practice Git branching, cautious merging, and making simple HTML/CSS updates.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/vUaRNbRK910" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

# Instructions

1. **Clone this repository:**

```bash
git clone https://github.com/fvtc/vce-branching-practice.git
```

> You can fork this repository if you want, but it's not necessary for this assignment.

2. **Create a `dev` branch**

3. **Create and complete the following feature branches:**

- `feature/link-color`

- `feature/purpose-style-update`

- `feature/new-section`

> The instructions for each feature branch can be found below.

4. **Merge all of your branches into `dev` and then into `main`**

> Remember to use the Cautious Merge strategy when merging your branches.

## Feature Branches

### Feature: Link Color Update 

*branch: `feature/link-color`*

Open the `css/styles.css` file and update the `.link` code to match the following:

```css
.link {
    color: #006600;
    text-decoration: underline;
    font-weight: bold;
}
```

This will change the link color to a dark green.

### Feature: Purpose Style Update 

*branch: `feature/purpose-style-update`*

Open the `css/styles.css` file if it's not already open, and update the `.purpose` code to match the following:

```css
.purpose {
    font-style: italic;
    color: #555;
    margin-bottom: 2rem;
    font-size: 1.1rem;
}
```

This will change the style of the purpose section to be italicized, a lighter gray color, and slightly larger font size.

### Feature: New Section 

*branch: `feature/new-section`*

Open the `index.html` file and add a new section with the following content:

Place this section after the closing `</ul>` tag and before the closing `</body>` tag:

```html
<section>
    <h2>Latest News</h2>
    <p class="news">We just learned how to use Git branches!</p>
</section>
```

Open the `css/styles.css` file and add the following CSS to style the new section:

```css
.news {
    color: #005577;
    font-size: 1rem;
}
```

## Submitting Your Assignment

Once you have completed all the tasks, run the following command:

1. **Paste the output of the following command in Blackboard:**

```bash
git log --oneline
```

2. Answer the following:

- Why is it helpful to use separate branches for each feature?

- What does merging dev into a feature branch help prevent?

- Did you encounter any conflicts? How did you resolve them?

