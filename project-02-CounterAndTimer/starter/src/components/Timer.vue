<template>
  <div class="timer">
    <h3>Timer</h3>
    <p>Time: {{ time }} seconds</p>
    <button @click="startTimer">Start</button>
    <button @click="stopTimer">Stop</button>
  </div>
</template>

<script setup>
import { ref, onUnmounted } from 'vue'

// Reactive state
const time = ref(0)
let timerInterval = null

// Methods
function startTimer() {
  // TODO: start timer interval
}

function stopTimer() {
  // TODO: stop timer interval
}

// Clean up interval on unmount
onUnmounted(() => {
  // TODO: clear timerInterval
})
</script>

<style scoped>
.timer {
  border: 2px solid #42b983;
  padding: 1rem;
  border-radius: 8px;
  text-align: center;
}

button {
  padding: 6px 12px;
  margin: 0 4px;
  border-radius: 4px;
  background-color: #42b983;
  color: white;
  border: none;
  cursor: pointer;
}
</style>