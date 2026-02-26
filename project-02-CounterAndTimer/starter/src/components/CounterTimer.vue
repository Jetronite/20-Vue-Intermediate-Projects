<script setup>
import { ref, computed, onUnmounted } from 'vue'

/*
  ======================
  Reactive State
  ======================
*/

const count = ref(0)
const time = ref(0)

let timerInterval = null

/*
  ======================
  Computed Properties
  ======================

  TODO:
  - Derive a status message from count
  - Example states: "Idle", "Low", "High"
*/

const status = computed(() => {
  // implement logic here
})

/*
  ======================
  Counter Methods
  ======================
*/

function increment() {
  // implement increment logic
}

function decrement() {
  // implement decrement logic
  // optional: prevent values below 0
}

/*
  ======================
  Timer Methods
  ======================
*/

function startTimer() {
  // implement interval logic
  // prevent multiple intervals
}

function stopTimer() {
  // implement interval cleanup
}

/*
  ======================
  Lifecycle Cleanup
  ======================
*/

onUnmounted(() => {
  // ensure timer is cleared here
})
</script>

<template>
  <section class="container">
    <div class="counter">
      <h2>Counter</h2>

      <p class="count-display">{{ count }}</p>

      <div class="buttons">
        <button @click="decrement">-</button>
        <button @click="increment">+</button>
      </div>

      <p class="status">
        Status: {{ status }}
      </p>
    </div>

    <div class="timer">
      <h2>Timer</h2>

      <p class="time-display">
        {{ time }} seconds
      </p>

      <div class="buttons">
        <button @click="startTimer">Start</button>
        <button @click="stopTimer">Stop</button>
      </div>
    </div>
  </section>
</template>

<style scoped>
.container {
  display: flex;
  gap: 3rem;
  padding: 2rem;
}

.counter,
.timer {
  border: 1px solid #ccc;
  padding: 1.5rem;
  border-radius: 12px;
  min-width: 200px;
  text-align: center;
}

.count-display,
.time-display {
  font-size: 2rem;
  margin: 1rem 0;
}

.buttons {
  display: flex;
  justify-content: center;
  gap: 1rem;
}

button {
  padding: 0.5rem 1rem;
  cursor: pointer;
}
</style>