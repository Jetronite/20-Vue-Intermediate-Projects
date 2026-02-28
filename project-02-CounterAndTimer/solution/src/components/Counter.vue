<template>
  <div class="counter">
    <h3>Counter</h3>
    <p>Count: {{ count }}</p>
    <p>Status: {{ status }}</p>
    <button @click="increment">+</button>
    <button @click="decrement">-</button>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

// Reactive state
const count = ref(0)

// Computed property placeholder
const status = computed(() => {
  // TODO: derive a status message from count
  if (count.value === 0) {
    return "Idle"
  } else if (count.value > 0 && count.value < 10) {
    return "Low"
  } else if (count.value >= 10 && count.value < 20) {
    return "Medium"
  } else {
    return "High"
  }
})

// Methods
function increment() {
  // TODO: increment count
  count.value++
}

function decrement() {
  // TODO: decrement count (optional: prevent below 0)
  if (count.value > 0) {
    count.value--
  }
}
</script>

<style scoped>
.counter {
  border: 2px solid #42b983;
  padding: 1rem;
  border-radius: 8px;
  text-align: center;
  margin-bottom: 1rem;
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