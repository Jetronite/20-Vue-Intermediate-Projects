# Project 2: Counter & Timer – Solution README

## Overview of Implementation

This project contains two independent Vue components:

* `Counter.vue`
* `Timer.vue`

Both components rely entirely on Vue’s Composition API and reactive system. No direct DOM manipulation is used. All UI updates are driven by reactive state changes.

The `Counter` component manages a numeric value and derives a status message using a computed property.

The `Timer` component manages elapsed time using `setInterval`, ensures only one timer runs at a time, and properly cleans up side effects when the component is unmounted.

---

## Architecture Explanation

Each feature is isolated into its own component. This separation ensures:

* Single responsibility
* Easier testing
* Clear state boundaries
* Reduced cognitive complexity

Both components follow the same internal pattern:

1. Reactive state declared using `ref`
2. Methods used to modify state
3. Computed properties used for derived values (Counter only)
4. Lifecycle hooks used for side effect cleanup (Timer only)

No cross-component state sharing exists in this version. Each component owns and manages its own state completely.

---

## Key Patterns Used

### 1. Reactive State with `ref`

```js
const count = ref(0)
const time = ref(0)
```

Primitive values are wrapped in `ref` to allow Vue to track reactive dependencies and update the template automatically.

---

### 2. Derived State with `computed`

```js
const status = computed(() => {
  if (count.value === 0) return "Idle"
  if (count.value < 10) return "Low"
  if (count.value < 20) return "Medium"
  return "High"
})
```

The status message is derived from `count`. It is not stored separately. This avoids state duplication and ensures correctness.

---

### 3. Controlled Side Effects

```js
let timerInterval = null

function startTimer() {
  if (!timerInterval) {
    timerInterval = setInterval(() => {
      time.value++
    }, 1000)
  }
}
```

The guard condition prevents multiple intervals from being created.

---

### 4. Cleanup via Lifecycle Hooks

```js
onUnmounted(() => {
  if (timerInterval) {
    clearInterval(timerInterval)
  }
})
```

Any running interval is cleaned up when the component is destroyed, preventing memory leaks.

---

## State Flow Explanation

### Counter State Flow

User clicks → Method executes → `count.value` updates →
Computed `status` recalculates automatically →
Vue updates the template → UI re-renders.

No manual rendering occurs. Vue reactivity manages dependency tracking.

---

### Timer State Flow

User clicks Start → `setInterval` begins →
Every 1000ms → `time.value` increments →
Vue updates DOM automatically.

User clicks Stop → Interval cleared →
State stops changing → UI stabilizes.

If component unmounts → Cleanup removes interval →
No background process continues running.

---

## Why This Approach

This approach aligns with Vue’s reactivity principles:

* Single source of truth for state
* Derived values handled via computed properties
* Explicit state mutations through methods
* Side effects isolated and cleaned up properly

By separating reactive state from side effects, the implementation remains predictable and maintainable.

This also scales well. If additional features are introduced (e.g., reset button, timer status indicator, shared state), the architecture can expand without structural refactoring.

---

## Possible Improvements

1. Add a Reset button for both counter and timer.
2. Format the timer display (e.g., MM:SS)
3. Display a "Running" or "Stopped" label for the timer using a reactive boolean.
4. Disable decrement when count is 0
5. Apply dynamic styling based on counter value
6. Add configurable step sizes for counter increment/decrement.
7. Convert to TypeScript for stronger type guarantees.
8. Add unit tests using Vue Test Utils.

---