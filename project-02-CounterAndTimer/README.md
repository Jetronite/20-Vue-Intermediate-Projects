# Project 2: Counter & Timer

**Difficulty:** ★☆☆☆☆ (Beginner)
**Core Concepts:** Computed properties, methods, lifecycle hooks (`mounted`)
**Features:** Increment/decrement counter, start/stop timer
**Focus:** Understanding reactive updates and side effects

---

## Screenshot

*(Insert a screenshot or GIF of the counter and timer UI here to give learners a visual reference)*

---

## Overview

In this project, you will build two foundational interactive components:

1. A **Counter** that can increment and decrement
2. A **Timer** that can start and stop

This project emphasizes understanding how Vue’s reactivity system automatically updates the UI and how to manage side effects safely with lifecycle hooks. You will learn to structure components so that state and behavior remain predictable and maintainable.

---

## Learning Objectives

By completing this project, you should be able to:

* Manage reactive state using `ref`
* Derive dynamic values with computed properties
* Encapsulate logic with methods
* Update the UI automatically via reactivity
* Handle side effects (like timers) responsibly
* Understand when and why lifecycle hooks are used

---

## Feature Requirements

### Counter

* Display a number starting at 0
* Increment button (+)
* Decrement button (–)
* Optional: prevent counter from going below 0
* Display a derived status message based on the count value

### Timer

* Display elapsed time in seconds
* Start button
* Stop button
* Ensure timer updates the UI reactively
* Prevent multiple intervals from running simultaneously
* Clean up timer on component unmount

---

## Optional Challenge

Once you complete the base requirements, consider these optional challenges:

* Add a **reset** button for the counter and timer
* Format the timer display (e.g., MM:SS)
* Display a "Running" or "Stopped" label for the timer using a reactive boolean.
* Disable decrement when count is 0
* Apply dynamic styling based on counter value
* Display a "Running" or "Stopped" label for the timer using a reactive boolean.
* Add configurable step sizes for counter increment/decrement.
* Convert to TypeScript for stronger type guarantees.
* Add unit tests using Vue Test Utils.


Stretch goals help you explore beyond the core concepts and experiment with best practices.

---

## Evaluation Checklist

Before moving on, confirm that:

* All state is managed via Vue’s reactivity system (`ref`/`reactive`)
* The UI updates automatically when state changes
* Derived values react correctly without manual DOM manipulation
* Timer stops correctly and cleans up intervals on unmount
* Counter and timer behave as expected under rapid input
* No direct DOM manipulation is used

---

## Reflection Questions

After completing the project, consider:

* How does reactive state trigger UI updates?
* What is the difference between modifying state and deriving state?
* Why must intervals be cleaned up?
* What would happen if multiple timers ran simultaneously?
* How could you refactor this project to support multiple counters?
* Where should side-effect logic reside in a component?

Reflecting on these questions deepens your understanding beyond simply making the app work.

---

## Learning Flow

1. Read this Root README to understand the project goals
2. Navigate to the `starter/` folder and follow its README for setup and guidance
3. Attempt the project implementation on your own
4. Compare your solution with the `solution/` folder after finishing
5. Use the Reflection Questions to analyze your approach and learn from the solution

---

## Estimated Time

**30–45 minutes** – enough to implement and test the counter and timer while reflecting on core concepts.

---

## Prerequisites

* Basic Vue knowledge: template syntax, `ref`, event handling
* Understanding of JavaScript fundamentals (variables, functions, intervals)
* Familiarity with running a Vue development server

---