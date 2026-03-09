# Codebase Documentation

This document provides a comprehensive overview of the codebase, adhering strictly to the provided files and their contents without inferring or inventing features.

## Overview

This codebase consists of a single HTML file that implements a simple web-based Task Manager application. It's a self-contained front-end application with its HTML structure, CSS styling, and JavaScript logic all embedded within `task_manager.html`. Users can add new tasks, mark existing tasks as complete, and delete tasks.

## File Structure

- `task_manager.html`

## File: task_manager.html

This file serves as the complete application. It contains the following components:

-   **HTML Structure**: Defines the layout and elements of the task manager interface.
-   **CSS Styling**: Embedded within a `<style>` tag in the `<head>`, providing visual presentation and responsiveness.
-   **JavaScript Functionality**: Embedded within a `<script>` tag in the `<body>`, implementing the interactive logic for task management.

## HTML Structure

The `task_manager.html` file defines a standard HTML5 document.

-   The `<!DOCTYPE html>` declaration and `<html>` root element with `lang="en"`.
-   The `<head>` section includes:
    -   `meta` tag for `charset="UTF-8"`.
    -   `<title>` set to "Simple Task Manager".
    -   An embedded `<style>` block containing all the CSS rules for the page.
-   The `<body>` section contains the main content:
    -   A `div` with the class `container` which acts as the main wrapper for the task manager interface.
    -   An `<h2>` heading displaying "Task Manager".
    -   A `div` with the class `input-area` containing:
        -   An `input` field of type `text` with `id="taskInput"` and a `placeholder="Enter new task"`.
        -   A `button` labeled "Add" which, when clicked, executes the `addTask()` JavaScript function.
    -   An unordered list (`<ul>`) with `id="taskList"`, which will dynamically hold the added tasks.
    -   An embedded `<script>` block containing all the JavaScript logic for the application.

## CSS Styling

The embedded CSS styles define the visual appearance of the Task Manager.

-   **`body`**: Sets `Arial, sans-serif` as the font, a light grey background (`#f4f6f8`), and uses flexbox (`display: flex`, `justify-content: center`, `align-items: center`, `height: 100vh`) to center the container both horizontally and vertically on the page.
-   **`.container`**: Styles the main application box with a white background, padding, a fixed width of `400px`, rounded corners (`border-radius: 10px`), and a subtle `box-shadow`.
-   **`h2`**: Centers the main heading text.
-   **`.input-area`**: Uses flexbox to arrange the input field and add button side-by-side with a `10px` gap and `15px` bottom margin.
-   **`input`**: Occupies available space within `.input-area` (`flex: 1`) and has `8px` padding.
-   **`button`**: Provides basic styling for buttons: padding, no border, blue background (`#007bff`), white text, rounded corners (`border-radius: 5px`), and a pointer cursor.
-   **`button:hover`**: Darkens the button background to `#0056b3` on hover.
-   **`ul`**: Removes default list styling (`list-style: none`) and padding.
-   **`li`**: Styles individual task items with a light grey background (`#f1f1f1`), bottom margin, padding, rounded corners, and uses flexbox (`display: flex`, `justify-content: space-between`, `align-items: center`) to align task text and delete button.
-   **`.completed`**: Applies a line-through text decoration and changes text color to `gray` for tasks marked as complete.
-   **`.delete`**: Overrides the default button background to `red` for delete buttons.

## JavaScript Functionality

The embedded JavaScript provides the interactive logic for the task manager.

-   **`addTask()` function**:
    -   Retrieves the `taskInput` element and its trimmed value.
    -   **Input Validation**: If `taskText` is empty, it displays an `alert` message "Please enter a task" and stops execution.
    -   Creates a new `li` element to represent a task item.
    -   Creates a `span` element to hold the task text.
        -   Sets the `textContent` of the `span` to the `taskText`.
        -   Assigns an `onclick` event listener to the `span` that toggles the `completed` CSS class on the `span` itself, allowing tasks to be marked as complete/incomplete.
    -   Creates a `button` element for deleting the task.
        -   Sets its `textContent` to "Delete" and its `className` to "delete" for specific styling.
        -   Assigns an `onclick` event listener to this button that removes its parent `li` element from the DOM, effectively deleting the task.
    -   Appends the `span` (task text) and the `delBtn` (delete button) as children to the `li` element.
    -   Appends the newly created `li` element to the `ul` element with `id="taskList"`.
    -   Clears the `value` of the `taskInput` field, preparing it for the next task entry.

## Features
- Add new tasks to a list.
- Mark tasks as completed by clicking on the task text, which applies a strike-through and changes its color to grey.
- Delete individual tasks using a "Delete" button next to each task.
- Input validation to prevent adding empty tasks.

## How to Use/Run

1.  **Save the code**: Copy the entire code block and save it into a file named `task_manager.html` (or any other `.html` extension).
2.  **Open in Browser**: Navigate to the saved `task_manager.html` file in your file explorer and open it with any modern web browser (e.g., Chrome, Firefox, Edge, Safari).
3.  **Add a Task**: Type a task into the "Enter new task" input field and click the "Add" button. The task will appear in the list below.
4.  **Mark as Complete**: Click on the text of an existing task to toggle its completed status (it will gain a strike-through and turn grey). Click again to revert.
5.  **Delete a Task**: Click the "Delete" button next to any task to remove it from the list.