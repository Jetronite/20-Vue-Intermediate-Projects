<script setup>
import { ref } from 'vue'

// TODO: Create a reactive array to store tasks
// const tasks = ?

// TODO: Create a reactive variable for the input value
// const newTask = ?

// TODO: Create a function to add a task
// function addTask() {}
</script>

<template>
  <div class="app">
    <h2>To Do List</h2>

    <input
      v-model="newTask"
      type="text"
      placeholder="Add a new task"
    />

    <button @click="addTask">Add</button>

    <ul>
      <!-- TODO: Render tasks using v-for -->
    </ul>
  </div>
</template>