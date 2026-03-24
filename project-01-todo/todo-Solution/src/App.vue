<script setup>
import { ref } from 'vue'

const tasks = ref([])
const newTask = ref("")

function addTask() {
  if (!newTask.value.trim()) return
  tasks.value.push(newTask.value.trim())
  newTask.value = ""
}

</script>

<template>
  <div class="app">
    <h2>To Do List</h2>

    <form class="input-group" @submit.prevent="addTask">
      <input v-model="newTask" @keyup.enter="addTask" type="text" placeholder="Add a new task" />
      <button type="submit">Add</button>
    </form>

    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        {{ task }}
      </li>
    </ul>

  </div>
</template>

<style>
/* Container styling */
.app {
  max-width: 600px;
  margin: 50px auto;
  padding: 2rem;
  background: #ffffff;
  border-radius: 12px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

h2 {
  color: #2c3e50;
  text-align: center;
  margin-bottom: 1.5rem;
}

/* Input Group layout */
.input-group {
  display: flex;
  gap: 10px;
  margin-bottom: 2rem;
}

input {
  flex: 1;
  padding: 12px;
  border: 2px solid #e0e0e0;
  border-radius: 6px;
  outline: none;
  transition: border-color 0.3s;
}

input:focus {
  border-color: #42b983;
  /* Vue Green */
}

button {
  padding: 6px 12px;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-weight: bold;
  transition: background 0.3s, transform 0.1s;
}

button:hover {
  background-color: #3aa876;
}

button:active {
  transform: scale(0.98);
}

/* List styling */
ul {
  list-style: none;
  padding: 0;
}

li {
  padding: 12px;
  background: #f8f9fa;
  border-radius: 6px;
  margin-bottom: 8px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-left: 4px solid #42b983;
  animation: fadeIn 0.3s ease;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>