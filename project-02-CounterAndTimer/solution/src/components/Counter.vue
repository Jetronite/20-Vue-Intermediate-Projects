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
  return "Idle"
})

// Methods
function increment() {
  // TODO: increment count
}

function decrement() {
  // TODO: decrement count (optional: prevent below 0)
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