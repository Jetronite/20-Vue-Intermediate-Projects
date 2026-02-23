---

# Project 1: Todo List App

**Difficulty:** ★☆☆☆☆ (Beginner)

---

## Overview

In this project, you’ll build a simple Todo List using Vue’s Composition API (`<script setup>`).

The goal isn’t just to make a list work — it’s to understand **how Vue reactivity connects your data to the DOM**.

When your state changes, the UI updates automatically. That’s the core idea you’re practicing here.

You’ve been given a structured starter template with TODO comments. Your task is to complete the logic step by step.

---

## Your Mission

You need to implement:

1. A reactive array to store tasks
2. A reactive variable for the input field
3. A function that adds a task to the array
4. Rendering the tasks using `v-for`

The template already contains:

* An input bound with `v-model`
* A button that triggers `addTask`
* A `<ul>` waiting for dynamic content

Your job is to wire everything together.

---

## Concepts You’ll Practice

### 1. `ref()` — Creating Reactive State

Vue doesn’t magically track normal variables.
To make a value reactive, you use `ref()`.

Example concept:

```js
const count = ref(0)
```

When `count.value` changes, Vue updates the DOM automatically.

You’ll use this idea for:

* The tasks array
* The input field value

---

### 2. `v-model` — Two-Way Data Binding

`v-model` connects your input field to a reactive variable.

When a user types:

* The variable updates.
  When the variable updates:
* The UI reflects it.

That’s two-way binding.

Your input is already written as:

```html
v-model="newTask"
```

You just need to make sure `newTask` actually exists and is reactive.

---

### 3. Handling Events with `@click`

The button calls:

```html
@click="addTask"
```

Your job is to define the `addTask` function so it:

* Takes the current input value
* Adds it to your tasks array
* Clears the input afterward

---

## Implementation Strategy (Think Before Coding)

Before touching the keyboard, answer this mentally:

* What data do I need?
* How will tasks be stored?
* What should happen when the button is clicked?

Programming rewards structured thinking.

Don’t rush into typing.

Design first.

---

# Part 2: Rendering, Debugging, and Stretching

Now that you’ve created:

* A reactive `tasks` array
* A reactive `newTask` variable
* An `addTask()` function

It’s time to make the list appear on the screen.

---

## Rendering Tasks with `v-for`

Vue renders lists using the `v-for` directive.

Conceptually:

```html
<li v-for="item in items" :key="something">
  {{ item }}
</li>
```

You’ll use this pattern to loop over `tasks`.

Inside your `<ul>`, render one `<li>` per task.

Important rule:
Always provide a `:key`.

The `key` helps Vue track elements efficiently.
You can use the array index for now (we’ll improve this in later projects).

---

## What Should Happen When You Click “Add”?

When the user clicks:

1. The current `newTask` value should be pushed into `tasks`.
2. The input field should reset to empty.
3. The UI should update automatically.

If it doesn’t update:

* Your variable might not be reactive.
* You might be forgetting `.value` in `<script setup>` when using refs.

Remember:
Inside `<script>`, refs use `.value`.
Inside `<template>`, Vue unwraps them automatically.

That subtle distinction matters.

---

## Common Beginner Mistakes

Here are a few things that trip people up:

1. Forgetting to initialize the array as reactive.
2. Trying to push to `tasks` without using `.value`.
3. Forgetting to clear `newTask` after adding.
4. Not binding `v-model` to a defined variable.

If your list doesn’t render, log things:

```js
console.log(tasks.value)
```

Debugging is not failure.
Debugging is understanding reality.

---

## Optional Challenge (Recommended)

Once the basic list works, try adding:

⭐ Prevent empty tasks
⭐ A remove button per task
⭐ A “Clear All” button
⭐ A task counter (`You have 3 tasks`)
⭐ Store tasks in `localStorage`
⭐ Replace index key with unique ID
⭐ Add keyboard support (Enter to submit)
⭐ A toggle to mark tasks as completed
⭐ Replace index key with unique ID


Each small feature deepens your understanding of:

* Event handling
* Array manipulation
* Conditional rendering

---

## What You Should Understand Before Moving On

Before jumping to Project 2, you should be comfortable with:

* Creating reactive state using `ref()`
* Updating arrays in reactive state
* Rendering dynamic lists with `v-for`
* Connecting inputs using `v-model`
* Triggering logic using `@click`

If any of these feel fuzzy, revisit them.