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

const isRunning = ref<boolean>(false)

// Methods
function startTimer(): void {
  // TODO: start timer interval
  if (!timerInterval) {
    isRunning.value = true
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
    isRunning.value = false
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
  let seconds = time.value;

  // Define our units in descending order
  const units = [
    { label: 'year',   seconds: 31536000 },
    { label: 'day',    seconds: 86400 },
    { label: 'hour',   seconds: 3600 },
    { label: 'minute', seconds: 60 },
    { label: 'second', seconds: 1 }
  ];

  const parts: string[] = [];

  for (const unit of units) {
    if (seconds >= unit.seconds || (unit.label === 'second' && parts.length === 0)) {
      const value = Math.floor(seconds / unit.seconds);
      seconds %= unit.seconds;
      // Add "s" for plural if value is not 1
      parts.push(`${value} ${unit.label}${value !== 1 ? 's' : ''}`);
    }
  }

  return parts.join(' ');
});

// Clean up interval on unmount
onUnmounted((): void => {
  // TODO: clear timerInterval
  pauseTimer()
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