<template>
  <div class="counter" :class="status.toLowerCase()">
    <h3>Counter</h3>

    <div class="display-section">
      <p class="status-label">Status: <span>{{ status }}</span></p>
    </div>

    <div class="button-grid">
      <button v-if="buttonSwitchFour === 3" class="btn-3" @click="biggerStepDecrement">-{{ secondStep }}</button>
      <button v-if="buttonSwitchFour === 1 || buttonSwitchFour === 3" class="btn-1" @click="stepDecrement">-{{ firstStep }}</button>
      <button @click="decrement">−</button>
      <p class="count-value">{{ count }}</p>
      <button @click="increment">＋</button>
      <button v-if="buttonSwitchFour === 1 || buttonSwitchFour === 2" class="btn-2" @click="stepIncrement">+{{ firstStep }}</button>
      <button v-if="buttonSwitchFour === 2" class="btn-3" @click="biggerStepIncrement">+{{ secondStep }}</button>
    </div>
    <button class="reset-btn" @click="reset">Reset</button>
  </div>
</template>


<script setup lang="ts">
import { ref, computed } from 'vue'

const count = ref<number>(0)
const firstStep = ref<number>(5)
const secondStep = ref<number>(10)

/** * buttonSwitchFour handles UI state:
 * 0: Reset/Initial, 1: Single Step, 2: Multi-Increment, 3: Multi-Decrement 
 */
const buttonSwitchFour = ref<number>(1)

const status = computed<string>(() => {
  if (count.value === 0) return "Idle"
  if (count.value < 10) return "Low"
  if (count.value < 20) return "Medium"
  return "High"
})

function increment (): void {
  buttonSwitchFour.value = 1;
  count.value++;
}

function decrement (): void {
  if (count.value > 0) {
    buttonSwitchFour.value = 1;
    count.value--
  }
}

function stepIncrement (): void {
  buttonSwitchFour.value = 2;
  count.value += firstStep.value
}

function stepDecrement (): void {
  if (count.value-firstStep.value >= 0) {
    buttonSwitchFour.value = 3;
    count.value -= firstStep.value
  }
}

function biggerStepIncrement (): void {
  count.value += secondStep.value
}

function biggerStepDecrement (): void {
  if (count.value-secondStep.value >= 0) {
    count.value -= secondStep.value
  }
}

function reset (): void {
  count.value = 0
  buttonSwitchFour.value = 0;
}

</script>

<style scoped>
.counter {
  border: 2px solid;
  padding: 1.5rem;
  border-radius: 12px;
  text-align: center;
  transition: all 0.3s ease;
  margin: 1rem auto;
}

/* Dynamic Border Colors based on Status */
.counter.idle {
  border-color: #bdc3c7;
}

.counter.low {
  border-color: #3498db;
}

.counter.medium {
  border-color: #f1c40f;
}

.counter.high {
  border-color: #e74c3c;
}

.count-value {
  font-size: 3rem;
  font-weight: bold;
  margin: 0;
  font-family: 'Courier New', Courier, monospace;
}

.status-label span {
  font-weight: bold;
  text-transform: uppercase;
}

/* Grid Layout for buttons */
.button-grid {
  display: flex;
  flex-direction: row;
  gap: 10px;
  margin: 1.5rem 0;
}

button {
  padding: 8px 16px;
  border-radius: 6px;
  background-color: #ecf0f1;
  color: #2c3e50;
  border: 1px solid #bdc3c7;
  cursor: pointer;
  transition: all 0.2s;
}

button:hover:not(:disabled) {
  background-color: #dfe6e9;
}

button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

.button-grid button {
  padding: 12px 24px;
  font-size: 1.2rem;
  background-color: #42b983;
  color: white;
  border: none;
}

.reset-btn {
  width: 100%;
  background-color: #e74c3c;
  color: white;
  border: none;
  font-weight: bold;
}
</style>