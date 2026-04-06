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

## Reflection Questions (answered)

### **1. How does reactive state trigger UI updates?**

In Vue, when you use `ref()` or `reactive()`, Vue wraps your data in its reactivity system.

So when you do something like:

```js
count.value++
```

Vue:

1. Detects the change
2. Re-runs any dependent template code
3. Efficiently updates only the affected DOM

You don’t manually update the UI—Vue does it for you.

👉 Think:
**State changes → Vue reacts → UI updates automatically**

---

### **2. What is the difference between modifying state and deriving state?**

#### **Modifying state**

You are *changing the actual data*:

```js
count.value++
```

---

#### **Deriving state**

You are *calculating something from existing data*:

```js
const status = computed(() => {
  return count.value > 5 ? "High" : "Low"
})
```

---

#### Key difference:

| Type         | Purpose           | Example            |
| ------------ | ----------------- | ------------------ |
| Modify state | Store real data   | `count++`          |
| Derive state | Compute from data | `"High"` / `"Low"` |

👉 Derived state should **never be manually updated**
It updates automatically when the source changes.

---

### **3. Why must intervals be cleaned up?**

Because `setInterval` keeps running **even if your component is gone**.

If you don’t clean it:

* Memory leaks happen
* Background processes keep running
* Bugs appear (like multiple timers ticking at once)

---

### Proper cleanup:

```js
onUnmounted(() => {
  clearInterval(timer)
})
```

👉 Rule:
**If you start something (interval, listener), you must stop it.**

---

### **4. What would happen if multiple timers ran simultaneously?**

Chaos. Fast.

You’d see:

* Time increasing too quickly
* Multiple intervals stacking
* Performance issues
* Hard-to-debug behavior

Example:
Instead of:

```
1 → 2 → 3 → 4
```

You get:

```
1 → 3 → 6 → 10 (accelerating madness)
```

👉 That’s why you guard it:

```js
if (!isRunning.value) {
  startTimer()
}
```

---

### **5. How could you refactor this project to support multiple counters?**

Now you’re stepping into scalable thinking.

#### Option 1: Component reuse

Create a reusable component:

```vue
<Counter />
<Counter />
<Counter />
```

Each instance has its own internal state.

---

### Option 2: Data-driven approach

Store counters in an array:

```js
const counters = ref([0, 0, 0])
```

Render with `v-for`:

```html
<div v-for="(count, index) in counters">
  {{ count }}
</div>
```

---

### Option 3 (advanced):

Turn logic into a **composable**:

```js
function useCounter() {
  const count = ref(0)
  const increment = () => count.value++
  return { count, increment }
}
```

Now you can reuse logic anywhere.

---

### **6. Where should side-effect logic reside in a component?**

Side effects = things that affect the outside world:

* Timers (`setInterval`)
* API calls
* Event listeners

---

#### Correct place:

Inside **lifecycle hooks**, like:

```js
onMounted()
onUnmounted()
```

---

#### Example:

```js
onMounted(() => {
  timer = setInterval(() => {
    time.value++
  }, 1000)
})

onUnmounted(() => {
  clearInterval(timer)
})
```

---

#### Why?

Because lifecycle hooks:

* Control **when** effects start
* Ensure **proper cleanup**
* Keep logic predictable

---

### **Final Insight**

This project is teaching you 3 deep ideas:

* Reactivity (Vue handles updates)
* Separation (state vs derived state)
* Responsibility (who starts/stops side effects)

Once these click, you stop “trying things” and start **engineering behavior**.

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