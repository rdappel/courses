---
title: Assignment 10 - Final Project
subtitle: Modern JavaScript
hideNav: false

live: https://fvtc.software/appel/modern-javascript/assignments/final-project
---

# Assignment 10 - Final Project

For your final project, you and your group will be building a full-stack application for a fictional food truck. The application will allow customers to view the menu, as well as see the events and times that the food truck will be at different locations.

You and your group can choose the name of the food truck, type of food served, and the locations where the food truck will be.

<details open>
    <summary class="video">Show/Hide Video</summary>
    <div class="video-container">
        <iframe src="https://www.youtube.com/embed/LXIPyG3vfgc" width="100%" height="100%" frameborder="0"
            allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
        </iframe>
    </div>
</details>

## Specifications

1. Create a new ExpressJS application called `food-truck`. This application will be the backend for your project. It should have routes for serving static files, as well as an API for getting the menu and events. The back-end will store the menu and events in a MongoDB database.

2. Create API routes for the following:

    - `GET /api/v1/menu` - This route should return a JSON object that contains the menu items for the food truck. The menu should contain at least 5 items, and each item should have a name, description, price, and url for an image.

    - `GET /api/v1/events` - This route should return a JSON object that contains the events for the food truck. The events should contain at least 5 items, and each item should have a name, location, date, and time.

    - `GET api/v1/menu/:id` - This route should return a JSON object that contains the menu item with the specified id.

    - `GET /api/v1/events/:id` - This route should return a JSON object that contains the event with the specified id.

    - `POST /api/v1/menu` - This route should add a new menu item to the database. The request body should contain the name, description, price, and image URL for the new menu item.

    - `POST /api/v1/events` - This route should add a new event to the database. The request body should contain the name, location, date, and time for the new event.

3. For the front-end, create routes for the following pages:
    
    - `/` - This route should display the home page for the food truck. It should contain the menu items and an overview of the events (name and date). When a user clicks on an event, they should be taken to the `/event/:eventId` route.

    - `/event/:eventId` - This route should display the complete details of the event, including the location and time.

    - `/admin` - This route should display a form for adding new menu items and events. The form should have fields for name, description, price, and image URL for menu items, and name, location, date, and time for events.

4. Style your application using CSS. I am not looking for anything fancy, but make sure it is clean, easy to read, and the colors are consistent.

5. Your menu and events should be stored in a MongoDB database. You can use the module that we created in class to connect to the database.

> [!NOTE] You may have to add your partners IP address to the MongoDB Atlas whitelist in order to connect to the database.

# Classroom Students

We will be working on this project in class. You will choose (or I will) groups of 2-3 students to work on the project together. You will have time in class to work on the project, but you will also need to work on it outside of class.

# Online Students

## Finding a Partner/Group

You will need to find a partner (or two) to work on this project with. I have setup a [Teams Channel](https://teams.microsoft.com/l/channel/19%3A178c2bc6d7d4413a8092b7ee19aa374e%40thread.tacv2/Final%20Project%20-%20Online?groupId=2348ea0d-6e05-4e3f-a9a8-1ccb343f71c5&tenantId=ae888c53-4d60-47da-a75a-c8a10f1d47b0) for this purpose.

## Working Collaboratively

Once you have found a partner, you will need to decide who is going to work on what parts of the project. Additionally, who is going to be responsible for setting up the repository on GitHub, and who is going to be responsible for setting up the MongoDB database. If you have any questions or need help, please reach out to me.

# Submission

**In-class students** will be demonstrating their project to the instructor in class. They will then submit the link to their GitHub repository in Blackboard.

**Online students** will need to record a video demonstrating their project, as well as, spending 5-10 minutes explaining their code. You should walk through your implementation of the food truck application, explaining how you structured your code, and how you handled the API routes. You should also discuss any challenges you faced, and how you overcame them. You will submit your video, along with a link to your GitHub repository, in Blackboard.
