<template>
  <div>
    <button @click="handleClick">Remove</button>
  </div>
</template>

<script setup>
const emit = defineEmits(['remove'])

function handleClick() {
  emit('remove')
}
</script>

<style scoped>
  button {
    background-color: yellow;
  }
</style>