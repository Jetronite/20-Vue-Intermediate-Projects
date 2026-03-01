<template>
  <div class="timer">
    <h3>Timer</h3>
    <p>Time: {{ formattedTime }}</p>
<button v-if="!isRunning && time === 0" @click="startTimer">Start</button>
<button v-if="isRunning" @click="pauseTimer">Pause</button>
<button v-if="!isRunning && time > 0" @click="resumeTimer">Resume</button>
<button v-if="time > 0" @click="resetTimer">Reset</button>
  </div>
</template>

<script setup lang="ts">
import { ref, onUnmounted, computed } from 'vue'

// Reactive state
const time = ref<number>(0)
let timerInterval: ReturnType<typeof setInterval> | null = null

const isRunning = computed<boolean>(() => timerInterval !== null)

// Methods
function startTimer(): void {
  // TODO: start timer interval
  if (!timerInterval) {
    timerInterval = setInterval(() => {
      time.value++
    }, 1000)
  }
}

function pauseTimer(): void {
  // TODO: pause timer interval
  if (timerInterval) {
    clearInterval(timerInterval)
    timerInterval = null
  }
}

function resumeTimer(): void {
  startTimer()
}

function resetTimer(): void {
  time.value = 0
  pauseTimer()
}

const formattedTime = computed<string>(() => {
  const seconds = time.value
  if (seconds < 60) {
    return `${seconds} seconds`
  } else if (seconds < 3600) {
    const minutes = Math.floor(seconds / 60)
    const secs = seconds % 60
    return `${minutes} minutes ${secs} seconds`
  } else if (seconds < 86400) {
    const hours = Math.floor(seconds / 3600)
    const minutes = Math.floor((seconds % 3600) / 60)
    const secs = seconds % 60
    return `${hours} hours ${minutes} minutes ${secs} seconds`
  } else if (seconds < 31536000) {
    const days = Math.floor(seconds / 86400)
    const hours = Math.floor((seconds % 86400) / 3600)
    const minutes = Math.floor((seconds % 3600) / 60)
    const secs = seconds % 60
    return `${days} days ${hours} hours ${minutes} minutes ${secs} seconds`
  } else {
    const years = Math.floor(seconds / 31536000)
    const days = Math.floor((seconds % 31536000) / 86400)
    const hours = Math.floor((seconds % 86400) / 3600)
    const minutes = Math.floor((seconds % 3600) / 60)
    const secs = seconds % 60
    return `${years} years ${days} days ${hours} hours ${minutes} minutes ${secs} seconds`
  }
})

// Clean up interval on unmount
onUnmounted((): void => {
  // TODO: clear timerInterval
  if (timerInterval) {
    clearInterval(timerInterval)
  }
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