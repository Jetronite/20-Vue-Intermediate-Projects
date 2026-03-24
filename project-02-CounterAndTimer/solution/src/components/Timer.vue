<template>
  <div class="timer">
    <h3>Timer</h3>
    <p :class="{ 'active': isRunning }">{{ isRunning ? 'Running' : 'Paused' }}</p>
    <p class="time-display">{{ formattedTime }}</p>
    
    <div class="controls">
      <button @click="toggleTimer">{{ isRunning ? 'Pause' : 'Start' }}</button>
      <button :disabled="time === 0" @click="resetTimer">Reset</button>
    </div>
  </div>
</template>

<script setup>
import { ref, onUnmounted, computed } from 'vue'

const time = ref(0)
const isRunning = ref(false)
let interval = null

// Simple HH:MM:SS formatter
const formattedTime = computed(() => {
  const h = Math.floor(time.value / 3600).toString().padStart(2, '0')
  const m = Math.floor((time.value % 3600) / 60).toString().padStart(2, '0')
  const s = (time.value % 60).toString().padStart(2, '0')
  return `${h}:${m}:${s}`
})

const toggleTimer = () => {
  if (isRunning.value) {
    clearInterval(interval)
  } else {
    interval = setInterval(() => time.value++, 1000)
  }
  isRunning.value = !isRunning.value
}

const resetTimer = () => {
  clearInterval(interval)
  isRunning.value = false
  time.value = 0
}

onUnmounted(() => clearInterval(interval))
</script>

<style scoped>
.timer {
  border: 2px solid #42b983;
  padding: 1rem;
  border-radius: 8px;
  text-align: center;
  transition: border-color 0.3s ease;
}

h3 {
  margin-top: 0;
  color: #2c3e50;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-size: 1.2rem;
}

/* Dynamic Status Styles */
.active {
  color: #42b983; /* Green */
  font-weight: bold;
}

.paused {
  color: #e67e22; /* Orange/Yellow */
  font-weight: bold;
}

.time-display {
  font-family: monospace;
  font-size: 1.2rem;
}

button {
  padding: 6px 12px;
  margin: 0 4px;
  border-radius: 4px;
  background-color: #42b983;
  color: white;
  border: none;
  cursor: pointer;
  transition: opacity 0.2s;
}

button:hover {
  opacity: 0.8;
}
</style>