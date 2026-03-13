<template>
  <div class="results">
    <h2>Quiz Complete!</h2>

    <p>Your Score: {{ score }} / {{ total }}</p>

    <button @click="$emit('restart')">
      Restart Quiz
    </button>
  </div>
</template>

<script setup>
defineProps({
  score: Number,
  total: Number
})
</script>

<style>
.results {
  margin-top: 30px;
}
</style>