# Project 1: Todo List App – Starter

**Difficulty:** ★☆☆☆☆ (Beginner)
**Focus:** Solidifying reactive state and basic template syntax

---

## Setup Instructions

1. Navigate into the starter folder:

```bash
cd project-1-todo/starter
```

2. Install dependencies:

```bash
npm install
```

3. Start the development server:

```bash
npm run dev
```

4. Open your browser at the local URL shown in your terminal.

You should see the basic layout of the Todo app waiting for logic.

---

## Project Structure

Your starter contains the essential Vue structure:

```
src/
 ├── assets/
 │     └── images used for reference
 ├── App.vue
 ├── main.js
```

The template includes:

* An input field already bound with `v-model`
* A button already wired with `@click="addTask"`
* An unordered list (`<ul>`) ready for dynamic rendering

Your responsibility is to implement the logic inside `<script setup>`.

---

## Your Task

You must implement:

1. A reactive array to store tasks
2. A reactive variable for the input field
3. A function that adds a task to the array
4. Rendering the tasks using `v-for`

When the user types into the input and clicks the button:

* The new task should appear in the list
* The input should clear
* The UI should update automatically

The template is already structured. Your job is to connect state, logic, and rendering.

---

## Constraints

* Use the Composition API with `<script setup>`
* Use `ref()` for reactive variables
* Do not manipulate the DOM directly
* Do not reload the page to update state
* Use `v-for` for rendering lists
* Always include a `:key` when using `v-for`

The goal is to practice reactivity, not shortcuts.

---

## Hints (High-Level Only)

* Vue tracks changes only on reactive values created with `ref()`.
* Inside `<script>`, access ref values using `.value`.
* Inside the `<template>`, Vue unwraps refs automatically.
* To add to a reactive array, push into `tasks.value`.
* If nothing renders, log your state and verify it changes after clicking the button.

Reactivity is not magic — it is structured state tracking.

---

## Optional Challenges (Recommended)

Once the basic list works, try adding:

⭐ Prevent empty tasks
⭐ A remove button per task
⭐ A “Clear All” button
⭐ A task counter (`You have 3 tasks`)
⭐ Store tasks in `localStorage`
⭐ Add keyboard support (Enter to submit)
⭐ A toggle to mark tasks as completed

Each small feature deepens your understanding of:

* Event handling
* Array manipulation
* Conditional rendering

---

## Common Pitfalls

* Forgetting to initialize the array as reactive
* Trying to push to `tasks` without using `.value`
* Not clearing the input after adding a task
* Forgetting to define the variable bound to `v-model`
* Omitting the `:key` in `v-for`

If your list doesn’t update:

* Log your reactive variables
* Check whether you’re correctly using `.value`
* Confirm that state is actually changing

Debugging is not failure. It is observation in action.

---

## A Little Advice Before You Code

Pause before typing.

Ask yourself:

* What data do I need?
* How should it be structured?
* What should happen when the button is clicked?

Programming rewards intention more than speed.

Finish this project only when you truly understand why the UI updates automatically. That understanding is more valuable than the feature itself.

Build carefully. Test deliberately. Move forward with clarity.
