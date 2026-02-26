## Project 2: Counter & Timer

Difficulty: ★☆☆☆☆ (Beginner)
Focus: Reactive updates, computed properties, lifecycle hooks, and managing side effects

---

## 📌 Overview

This project introduces reactive state management in Vue through two core features:

1. A counter with increment and decrement controls
2. A timer that can start and stop

---

## 🎯 Learning Objectives

* Understand Vue’s reactivity system using `ref`
* Use methods to modify reactive state
* Use computed properties to derive values
* Observe how UI updates automatically when state changes
* Build clean, predictable state logic

---

## 🛠️ Project Setup

Create a new Vue project (if not already created):

```bash
npm create vue@latest
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

---

## 📂 Suggested File Structure

```
src/
 ├── components/
 │     └── CounterTimer.vue
 ├── App.vue
 └── main.js
```

You may implement everything inside `App.vue`, but creating a dedicated component keeps things structured.

---

# 🔢 Counter Feature

## Requirements

* Display a number starting at 0
* Increment button (+)
* Decrement button (–)
* Prevent the counter from going below 0 (optional stretch goal)
* Display a derived message based on the count (example: “High”, “Low”, etc.)

---

## 🧠 Core Concepts

### 1. Reactive State

Use `ref` to create reactive state:

```js
const count = ref(0)
```

Whenever `count.value` changes, Vue automatically updates the DOM.

---

### 2. Methods

Use methods to modify state:

```js
function increment() {
  count.value++
}

function decrement() {
  if (count.value > 0) {
    count.value--
  }
}
```

Methods directly cause side effects (changing state).

---

### 3. Computed Properties

Computed properties derive values from state:

```js
const status = computed(() => {
  if (count.value === 0) return 'Idle'
  if (count.value < 5) return 'Low'
  return 'High'
})
```

Computed values automatically update when dependencies change.

---

### 🖥️ 4. Expected UI Behavior

* Clicking “+” increases the number instantly
* Clicking “–” decreases it
* The derived status updates automatically
* The UI remains in sync without manual DOM manipulation

---

### 5. ✅ What to Validate Before Moving On

* Counter increments and decrements correctly
* Computed message updates without manual triggers
* No direct DOM manipulation is used
* All logic is contained within Vue’s reactivity system


---


# ⏱️ Timer Feature

In this part, we’ll add a **start/stop timer** alongside the counter. This introduces **side effects** and the use of **lifecycle hooks** in Vue.

---

### Requirements

* Display a timer in seconds (starting at 0)
* “Start” button to begin counting every second
* “Stop” button to pause the timer
* Resetting the timer is optional
* Timer should continue updating the UI reactively

---

### 1. Reactive State for Timer

```js id="t1r4kz"
const time = ref(0)
let timerInterval = null
```

`time` is reactive; the DOM updates automatically when it changes.
`timerInterval` will hold the interval ID so we can clear it later.

---

### 2. Methods to Control the Timer

```js id="t2q0fw"
function startTimer() {
  if (timerInterval) return // prevent multiple intervals
  timerInterval = setInterval(() => {
    time.value++
  }, 1000)
}

function stopTimer() {
  clearInterval(timerInterval)
  timerInterval = null
}
```

Key idea: **side effects must be managed carefully** to avoid memory leaks.

---

### 3. Lifecycle Hook: `onUnmounted`

If the component is removed from the DOM, we should stop the timer to prevent it from running in the background:

```js id="t3v9ld"
import { onUnmounted } from 'vue'

onUnmounted(() => {
  clearInterval(timerInterval)
})
```

---

### ✅ Key Takeaways

* **Reactive state** updates the DOM automatically (`count` and `time`)
* **Methods** encapsulate logic for user actions
* **Computed properties** derive dynamic values from state (`status`)
* **Lifecycle hooks** manage side effects (cleaning up intervals)
* Side effects must be cleaned up to avoid memory leaks and bugs

---

This project teaches **two essential Vue concepts**:

1. **Reactivity + computed values** (counter)
2. **Side effects + lifecycle management** (timer)

Mastering these prepares you for more complex features like API polling, form validation, and dynamic animations.

---