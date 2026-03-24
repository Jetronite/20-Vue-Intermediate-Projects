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
  /* Layout & Container */
  max-width: 300px;
  margin: 2rem auto;
  padding: 2rem;
  border: 2px solid #42b983;
  border-radius: 16px;
  text-align: center;
  background-color: #f9f9f9;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  font-family: 'Inter', sans-serif;
}

h3 {
  margin-top: 0;
  color: #2c3e50;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-size: 1.2rem;
}

/* Typography for Count and Status */
p:nth-of-type(1) {
  font-size: 2rem;
  font-weight: bold;
  margin: 10px 0;
  color: #42b983;
}

p:nth-of-type(2) {
  font-style: italic;
  color: #7f8c8d;
  margin-bottom: 1.5rem;
  font-size: 0.9rem;
}

/* Buttons */
button {
  width: 45px;
  height: 45px;
  font-size: 1.5rem;
  font-weight: bold;
  margin: 0 8px;
  border-radius: 50%; /* Circular buttons */
  background-color: #42b983;
  color: white;
  border: none;
  cursor: pointer;
  transition: all 0.2s ease;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}

button:hover {
  background-color: #33a06f;
  transform: translateY(-2px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

button:active {
  transform: translateY(0);
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.2);
}

/* Specific styling for the minus button to differentiate */
button:last-of-type {
  background-color: #e74c3c;
}

button:last-of-type:hover {
  background-color: #c0392b;
}
</style>