# Project 2 – Counter & Timer (Starter Version)

## 🎯 Purpose of This Starter

This repository provides a **structured scaffold** for the Counter & Timer project.

It does **not** include the completed logic.

Instead, it gives you:

* A prepared component structure
* Reactive state declarations
* Empty method stubs
* Clean layout placeholders

Your task is to implement the logic yourself.

This approach isolates the core learning goals:

* Understanding Vue reactivity
* Writing state-modifying methods
* Deriving values with computed properties
* Managing side effects safely with lifecycle hooks

The goal is conceptual clarity — not copying code.

---

## 🧠 Why Use a Starter?

When learning, it helps to control difficulty.

This starter removes setup friction so you can focus entirely on:

* How reactive values update the DOM
* How computed properties track dependencies
* How timers (side effects) must be cleaned up

In real-world development, you rarely start from zero.
You usually work inside an existing structure.

This starter mirrors that reality.

---

## 📦 What’s Included

Inside `CounterTimer.vue` you will find:

* Basic template layout (headings and empty UI placeholders)
* `<script setup>` structure
* Imported Vue APIs:

  * `ref`
  * `computed`
  * `onUnmounted`
* Reactive state variables (e.g., `count`, `time`)
* Empty method stubs:

  * `increment()`
  * `decrement()`
  * `startTimer()`
  * `stopTimer()`

---

## 🚫 What Is NOT Included

The following logic is intentionally **not implemented**:

* Counter increment/decrement behavior
* Protection against negative values
* Computed status message logic
* Interval-based timer logic
* Lifecycle cleanup implementation

You must implement these yourself.

---

## 🛠 Your Tasks

### Counter

* Implement increment logic
* Implement decrement logic
* (Optional) Prevent negative values
* Create a computed status based on count

### Timer

* Implement start logic using `setInterval`
* Prevent multiple intervals from stacking
* Implement stop logic
* Ensure cleanup using `onUnmounted`

---

## ✅ How to Validate Your Work

Before moving forward, ensure:

* The counter updates instantly without manual DOM manipulation
* The computed status changes automatically
* Only one timer interval runs at a time
* The timer stops properly when the component unmounts
* No memory leaks occur

If everything works without directly touching the DOM, you are successfully working within Vue’s reactivity system.

---

## 🧩 Skill Focus

This starter trains two critical frontend skills:

1. State → UI synchronization
2. Managing side effects safely

These patterns appear everywhere:

* API polling
* Animations
* Form validation
* Live dashboards

Mastering them here prepares you for significantly more complex applications.

---

## Optional Challenge (Recommended)
If you want, you may add the following features

⭐ A Reset Button (Counter & Timer)
⭐ Add a Maximum Limit to Counter
⭐ Disable Buttons Based on State
⭐ Format the Timer
⭐ Auto-Stop Timer at X Seconds
⭐ Persist Counter to Local Storage

---

Build it carefully.
Test behavior intentionally.
Think about what happens when components mount and unmount repeatedly.

That’s where real engineering begins.
Good Luck 😉