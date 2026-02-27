# Project 2: Counter & Timer – Starter

**Difficulty:** ★☆☆☆☆ (Beginner)
**Core Concepts:** Computed properties, methods, lifecycle hooks (`mounted`)
**Features:** Increment/decrement counter, start/stop a timer
**Focus:** Understanding reactive updates and side effects

---

## Setup Instructions

1. Ensure you have Node.js installed.
2. Create a new Vue project (if not already done):

```bash
npm create vue@latest
```

3. Install dependencies:

```bash
npm install
```

4. Start the development server:

```bash
npm run dev
```

5. Open the project in your browser at the URL provided by the dev server.

---

## Project Structure

Your starter project contains the following scaffolded files:

```
src/
 ├── components/
 │     ├── Counter.vue       # Component to implement the counter logic
 │     └── Timer.vue         # Component to implement the timer logic
 ├── App.vue                 # Main application file, imports Counter and Timer
 └── main.js                 # Vue entry point
```

Implement counter logic inside Counter.vue.
Implement timer logic inside Timer.vue.

---

## Your Task

1. **Counter Feature**

   * Display a number starting at 0
   * Increment and decrement buttons
   * Optional: prevent the counter from going below 0
   * Display a derived status message based on the count

2. **Timer Feature**

   * Display elapsed time in seconds
   * Start and Stop buttons
   * Ensure timer updates the UI reactively
   * Prevent multiple timers from running at once
   * Clean up the timer when the component is unmounted

You must implement these features using Vue’s reactivity system. Avoid direct DOM manipulation.

---

## Constraints

* Use `ref` for reactive state
* Use **methods** to modify state
* Use **computed properties** for derived values
* Manage side effects responsibly with lifecycle hooks (`mounted`/`onUnmounted`)
* Do not hardcode values into the template or manipulate the DOM manually

---

## Hints (High-Level Only)

* Consider creating one reactive variable for the counter and one for the timer.
* Use a computed property to derive the counter’s status message.
* For the timer, `setInterval` will help, but think about how to stop it safely.
* Lifecycle hooks are useful for cleaning up intervals to prevent memory leaks.

---

## Common Pitfalls

* Accidentally starting multiple intervals for the timer
* Directly changing the DOM instead of updating reactive state
* Forgetting to clear intervals when stopping the timer or unmounting the component
* Overwriting computed properties or reactive variables incorrectly
* Updating state outside methods or outside Vue’s reactive system

---

Build it carefully.
Test behavior intentionally.
That’s where real engineering begins.
Good Luck 😉

----