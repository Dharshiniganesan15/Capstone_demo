# Codebase Documentation

This document provides a comprehensive overview of the codebase, adhering strictly to the provided files and their contents without inferring or inventing features.

## Overview

This codebase consists of a single HTML file, `task_manager.html`, which implements a client-side "Advanced Task Manager". It utilizes embedded HTML for structure, CSS for styling, and JavaScript for dynamic functionality. The application allows users to add, edit, delete, and mark tasks as complete, with task data persisting in the browser's local storage.

## File Structure

- `task_manager.html`

## File: task_manager.html

This file contains the entire application, comprising the HTML structure, embedded CSS styles within a `<style>` tag in the `<head>`, and embedded JavaScript functionality within a `<script>` tag at the end of the `<body>`.

The HTML defines the basic page structure, a main container, an input area for new tasks, and an unordered list (`<ul>`) to display tasks.
The CSS provides styling for layout, typography, and visual appearance of the task manager components, including specific styles for buttons and completed tasks.
The JavaScript manages the task data, interacts with local storage for persistence, and dynamically renders the tasks on the page, handling user interactions like adding, editing, deleting, and marking tasks as complete.

## HTML Structure

The `task_manager.html` file defines the following key elements and their structure:

-   **Document Type and Language**: HTML5 doctype and `lang="en"` for English.
-   **Head Section**:
    -   `meta charset="UTF-8"`: Specifies character encoding.
    -   `title`: "Advanced Task Manager" sets the page title.
    -   `style` tag: Contains all CSS rules for the application's appearance.
-   **Body Section**:
    -   `div class="container"`: The main wrapper for the task manager interface.
        -   `h2`: Displays "Task Manager" as the application title.
        -   `div class="input-area"`: Contains elements for adding new tasks.
            -   `input type="text" id="taskInput"`: An input field for entering task text, with a placeholder "Enter task".
            -   `button class="add" onclick="addTask()"`: An "Add" button that triggers the `addTask()` JavaScript function when clicked.
        -   `ul id="taskList"`: An unordered list where tasks will be dynamically rendered by JavaScript.
    -   `script` tag: Contains all JavaScript code for the application's functionality.

## CSS Styling

The embedded CSS styles define the visual presentation of the task manager:

-   **`body`**:
    -   `font-family: Arial`: Sets a common sans-serif font.
    -   `background:#f4f4f4`: Light gray background color.
    -   `display:flex`, `justify-content:center`, `align-items:center`, `height:100vh`: Centers the content vertically and horizontally on the page.
-   **`.container`**:
    -   `background:white`, `padding:25px`, `width:420px`: White background, padding, and fixed width for the main application box.
    -   `border-radius:10px`, `box-shadow:0 4px 10px rgba(0,0,0,0.2)`: Rounded corners and a subtle shadow for a card-like effect.
-   **`h2`**:
    -   `text-align:center`: Centers the "Task Manager" heading.
-   **`.input-area`**:
    -   `display:flex`, `gap:10px`: Arranges the input field and add button in a row with spacing.
-   **`input`**:
    -   `flex:1`: Allows the input field to take up available space.
    -   `padding:8px`: Internal padding.
-   **`button`**:
    -   `padding:6px 10px`, `border:none`, `border-radius:4px`, `cursor:pointer`: Basic styling for all buttons, including padding, no border, rounded corners, and a pointer cursor on hover.
-   **`.add`**:
    -   `background:#007bff`, `color:white`: Blue background and white text for the "Add" button.
-   **`.delete`**:
    -   `background:red`, `color:white`: Red background and white text for "Delete" buttons.
-   **`.edit`**:
    -   `background:orange`, `color:white`: Orange background and white text for "Edit" buttons.
-   **`li`**:
    -   `display:flex`, `justify-content:space-between`, `align-items:center`: Arranges task text and action buttons in a row, with space between them and vertical alignment.
    -   `background:#eee`, `margin-top:8px`, `padding:8px`, `border-radius:5px`: Light gray background, margin, padding, and rounded corners for individual task items.
-   **`.completed`**:
    -   `text-decoration:line-through`, `color:gray`: Strikes through text and changes color to gray for completed tasks.
-   **`.actions button`**:
    -   `margin-left:5px`: Adds left margin to action buttons (Edit, Delete) within a task item.

## JavaScript Functionality

The JavaScript code manages the task list, stores it in local storage, and dynamically updates the UI.

-   **`tasks` array**:
    -   Initializes an array `tasks` by attempting to parse a JSON string from `localStorage.getItem("tasks")`. If no data is found, it defaults to an empty array. This array holds objects, each representing a task with `text` (string) and `completed` (boolean) properties.
-   **`saveTasks()` function**:
    -   Serializes the `tasks` array into a JSON string using `JSON.stringify()`.
    -   Stores this string in `localStorage` under the key `"tasks"`.
-   **`renderTasks()` function**:
    -   Gets a reference to the `ul` element with `id="taskList"`.
    -   Clears its current HTML content (`list.innerHTML=""`).
    -   Iterates through the `tasks` array:
        -   For each `task`, it creates a new `li` element.
        -   Creates a `span` element to display the `task.text`.
        -   If `task.completed` is true, it adds the "completed" CSS class to the `span`.
        -   Attaches an `onclick` event to the `span`: Toggles the `completed` status of the task, saves tasks, and re-renders the list.
        -   Creates a `div` element with `className="actions"` to hold action buttons.
        -   Creates an "Edit" button:
            -   Sets its `textContent` to "Edit" and `className` to "edit".
            -   Attaches an `onclick` event: Prompts the user for new task text, updates the task if input is provided, saves tasks, and re-renders.
        -   Creates a "Delete" button:
            -   Sets its `textContent` to "Delete" and `className` to "delete".
            -   Attaches an `onclick` event: Removes the task from the `tasks` array using `splice()`, saves tasks, and re-renders.
        -   Appends the "Edit" and "Delete" buttons to the `actions` div.
        -   Appends the `span` and `actions` div to the `li`.
        -   Appends the `li` to the `taskList` `ul`.
-   **`addTask()` function**:
    -   Gets a reference to the `input` element with `id="taskInput"`.
    -   Retrieves and trims its `value`.
    -   If the `text` is empty, an `alert` is shown, and the function returns.
    -   Pushes a new task object `{ text: text, completed: false }` to the `tasks` array.
    -   Clears the input field (`input.value=""`).
    -   Calls `saveTasks()` to persist the updated list.
    -   Calls `renderTasks()` to update the UI.
-   **Initial Call**:
    -   `renderTasks()` is called once when the script loads to display any tasks loaded from local storage.

## Features
-   **Add Task**: Users can input text into a designated field and click an "Add" button to add a new task to the list.
-   **Display Tasks**: Tasks are displayed in an unordered list, each with its text and action buttons.
-   **Mark Task as Complete**: Clicking on a task's text toggles its completion status, applying a strikethrough style and changing its color when completed.
-   **Edit Task**: Each task has an "Edit" button that, when clicked, prompts the user to enter new text for the task.
-   **Delete Task**: Each task has a "Delete" button that, when clicked, removes the task from the list.
-   **Task Persistence**: All tasks (including their text and completion status) are saved to and loaded from the browser's local storage, so they persist across browser sessions.

## How to Use/Run

To use or run this application:

1.  Save the provided code into a file named `task_manager.html` (or any `.html` extension).
2.  Open the `task_manager.html` file in any modern web browser (e.g., Chrome, Firefox, Safari, Edge).
3.  The task manager interface will appear.
4.  Enter a task in the input field and click "Add" to add it.
5.  Click on a task's text to mark it as complete/incomplete.
6.  Click the "Edit" button next to a task to modify its text.
7.  Click the "Delete" button next to a task to remove it.