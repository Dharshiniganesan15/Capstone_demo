# Codebase Documentation

This document provides a comprehensive overview of the codebase, adhering strictly to the provided files and their contents without inferring or inventing features.

## Overview

This codebase consists of a single HTML file that implements a client-side "Advanced Task Manager" web application. It combines HTML for structure, CSS for styling, and JavaScript for dynamic functionality, including task management and persistence using the browser's local storage.

## File Structure

- `task_manager.html`: The main and only file, containing the HTML structure, embedded CSS styles, and embedded JavaScript logic for the task manager.

## File: task_manager.html

This file serves as the complete application. It defines the webpage's structure, presentation, and interactive behavior.

-   **HTML (Structure):** Defines the basic document type, head section with metadata and title, and the body containing the task manager interface.
-   **CSS (Styling):** An embedded `<style>` block provides all the necessary visual styling for the task manager components, such as layout, colors, and typography.
-   **JavaScript (Functionality):** An embedded `<script>` block contains the logic for managing tasks, including adding, editing, deleting, marking as complete, and saving/loading tasks from local storage.

## HTML Structure

The `task_manager.html` file defines the following key elements and their structure:

-   `<!DOCTYPE html>`: Declares an HTML5 document.
-   `<html lang="en">`: The root element of the page, specifying the language as English.
-   `<head>`:
    -   `<meta charset="UTF-8">`: Specifies the character encoding.
    -   `<title>Advanced Task Manager</title>`: Sets the title of the web page shown in the browser tab.
    -   `<style>`: Contains the CSS rules for styling the application.
-   `<body>`:
    -   `<div class="container">`: A central container for the entire task manager interface.
        -   `<h2>Task Manager</h2>`: The main heading for the application.
        -   `<div class="input-area">`: A container for the task input field and add button.
            -   `<input type="text" id="taskInput" placeholder="Enter task">`: An input field for users to type new tasks, identified by `taskInput`.
            -   `<button class="add" onclick="addTask()">Add</button>`: A button to add tasks, styled with the `add` class, and triggers the `addTask()` JavaScript function when clicked.
        -   `<ul id="taskList">`: An unordered list where tasks will be displayed, identified by `taskList`.
    -   `<script>`: Contains the JavaScript code that handles the application's logic.

## CSS Styling

The embedded `<style>` block in `task_manager.html` provides the following styling:

-   **`body`**: Sets `Arial` font, a light grey background (`#f4f4f4`), uses flexbox to center content vertically and horizontally on the page, and sets the height to 100% of the viewport.
-   **`.container`**: Styles the main application wrapper with a white background, padding, fixed width (`420px`), rounded corners (`10px`), and a subtle box shadow.
-   **`h2`**: Centers the text horizontally.
-   **`.input-area`**: Arranges the input field and button using flexbox with a `10px` gap between them.
-   **`input`**: Makes the input field take up available space within its flex container (`flex:1`) and adds padding.
-   **`button`**: Provides basic styling for all buttons, including padding, no border, rounded corners (`4px`), and a pointer cursor on hover.
-   **`.add`**: Styles the "Add" button with a blue background (`#007bff`) and white text.
-   **`.delete`**: Styles the "Delete" button with a red background and white text.
-   **`.edit`**: Styles the "Edit" button with an orange background and white text.
-   **`li`**: Styles individual task items as flex containers, justifying content to space elements, aligning items vertically, a light grey background (`#eee`), top margin, padding, and rounded corners (`5px`).
-   **`.completed`**: Applies a line-through text decoration and changes text color to gray for completed tasks.
-   **`.actions button`**: Adds a left margin to buttons within the `.actions` container for spacing.

## JavaScript Functionality

The embedded `<script>` block in `task_manager.html` implements the core task management logic:

-   **`tasks` array**: A global array that stores task objects. It is initialized by attempting to load existing tasks from `localStorage` (`"tasks"` key) and parsing them as JSON. If no tasks are found or parsing fails, it defaults to an empty array.
-   **`saveTasks()` function**: Serializes the current `tasks` array into a JSON string and stores it in the browser's `localStorage` under the key `"tasks"`.
-   **`renderTasks()` function**:
    -   Retrieves the `ul` element with `id="taskList"`.
    -   Clears its current HTML content to prevent duplicate entries.
    -   Iterates through the `tasks` array:
        -   For each task, it creates an `<li>` element.
        -   Creates a `<span>` element to display the task's text.
        -   If `task.completed` is true, it adds the `completed` CSS class to the `<span>`.
        -   Sets an `onclick` event handler for the `<span>` to toggle the `completed` status of the task, then calls `saveTasks()` and `renderTasks()` to update the display and persistence.
        -   Creates a `<div>` with `className="actions"` to hold action buttons.
        -   Creates an "Edit" button (`editBtn`), sets its text and class, and assigns an `onclick` handler. The handler prompts the user for new text, updates the task if input is provided, then calls `saveTasks()` and `renderTasks()`.
        -   Creates a "Delete" button (`delBtn`), sets its text and class, and assigns an `onclick` handler. The handler removes the task from the `tasks` array using `splice()`, then calls `saveTasks()` and `renderTasks()`.
        -   Appends the "Edit" and "Delete" buttons to the `actions` div.
        -   Appends the `<span>` and `actions` div to the `<li>`.
        -   Appends the constructed `<li>` to the `ul#taskList`.
-   **`addTask()` function**:
    -   Retrieves the input element with `id="taskInput"`.
    -   Gets the trimmed value of the input field.
    -   If the input is empty, it displays an alert and exits.
    -   Creates a new task object `{ text: text, completed: false }` and pushes it to the `tasks` array.
    -   Clears the input field.
    -   Calls `saveTasks()` and `renderTasks()` to update persistence and display.
-   **Initial Call**: `renderTasks()` is called once when the script loads to display any tasks already stored in `localStorage`.

## Features
-   Displaying a list of tasks.
-   Adding new tasks via an input field and button.
-   Marking tasks as completed or uncompleted by clicking on the task text.
-   Editing existing tasks through a prompt dialog.
-   Deleting individual tasks.
-   Persistence of tasks across browser sessions using the browser's local storage.

## How to Use/Run

To use this Task Manager:

1.  Save the provided code into a file named `task_manager.html`.
2.  Open the `task_manager.html` file in any modern web browser (e.g., Chrome, Firefox, Edge, Safari).
3.  The task manager interface will appear, displaying any previously saved tasks.
4.  Type a task into the "Enter task" input field and click the "Add" button to add a new task.
5.  Click on a task's text to toggle its completion status (strike-through and grey text).
6.  Click the "Edit" button next to a task to modify its text.
7.  Click the "Delete" button next to a task to remove it from the list.