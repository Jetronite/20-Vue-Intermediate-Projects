<script setup>
import Counter from './components/Counter.vue';
import Timer from './components/Timer.vue';
</script>

<template>
  <div class="app">
    <h1>Counter & Timer Project</h1>
    <div class="components-container">
      <Counter />
      <Timer />
    </div>
  </div>
</template>

<style>
.app {
  max-width: 600px;
  margin: 50px auto;
  padding: 2rem;
  background: #ffffff;
  border-radius: 12px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  text-align: center;
}

h1 {
  color: #2c3e50;
  margin-bottom: 2rem;
}

.components-container {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}
</style>