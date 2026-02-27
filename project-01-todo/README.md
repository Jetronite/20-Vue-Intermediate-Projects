# Project 1: Todo List App

## Difficulty

★☆☆☆☆ (Beginner)

## Concept Focus

* `v-model` for two-way data binding
* `v-for` for rendering lists dynamically
* `v-if` for conditional rendering
* Event handling with `@click`
* Reactive state and automatic DOM updates

---

## Screenshot

![Todo List App Preview](starter/src/assets/list%20Project%201--To-do-list.png)

---

## Overview

The Todo List App is your first structured exercise in building a reactive Vue interface.

This project is intentionally simple in logic but powerful in teaching. You will build a system where user input updates state, state updates the DOM, and the interface reacts immediately — without manually touching the DOM.

This is your first encounter with Vue’s declarative model: you describe *what* the UI should look like based on state, and Vue handles *how* it changes.

Mastering this mental model is foundational. Every advanced Vue concept builds on it.

---

## Learning Objectives

By completing this project, you should be able to:

* Bind input values using `v-model`
* Render lists using `v-for`
* Conditionally render elements using `v-if`
* Respond to user events using `@click`
* Update reactive state and observe automatic DOM updates
* Think in terms of state → view synchronization

If you can explain *why* the DOM updates when state changes without manually manipulating it, you’ve crossed an important threshold.

---

## Feature Requirements

Your application must support:

* Adding new tasks via an input field
* Displaying all tasks in a list
* Removing individual tasks
* Marking tasks as completed with visible visual feedback
* Keeping the UI reactive at all times

Functional correctness is more important than visual complexity.

---

## Evaluation Checklist

Before moving on, confirm:

* Adding a task updates the list immediately
* Removing a task updates state and DOM correctly
* Completed tasks visually differ from incomplete ones
* No direct DOM manipulation is used
* No page reload is required for updates
* State drives the UI — not the other way around

If something only works after refresh, re-examine your reactive state.

---

## Reflection Questions

After finishing:

* What part of the app is responsible for storing tasks?
* How does Vue know when to update the DOM?
* What would happen if tasks were not reactive?
* Why is `v-model` more convenient than manually syncing input values?
* Where could this architecture break down in larger applications?

The point is not just building it. It’s understanding why it works.

---

## Learning Flow

1. Navigate to the `starter/` folder
2. Implement the required features yourself
3. Test all behaviors intentionally
4. Only after completing your attempt, review the `solution/` folder
5. Compare architectural decisions, not just syntax

Treat the solution as a reference implementation — not a shortcut.

---

## Estimated Time

45–90 minutes depending on experience.

If it takes longer, that’s not failure — that’s friction forging understanding.

---

## Prerequisites

* Basic understanding of Vue project structure
* Familiarity with reactive state using `ref()`
* Comfort using template directives like `v-if` and `v-for`
* Basic JavaScript array manipulation

If those feel uncertain, revisit fundamentals before proceeding.

---