<template>
  <div>
    <button @click="handleClick">
      {{ isCompleted ? "Not Done" : "Mark Done" }}
    </button>
  </div>
</template>

<script setup>
import { ref } from 'vue'
const emit = defineEmits(['toggle'])

const props = defineProps({
  initial: { type: Boolean, default: false }
})

const isCompleted = ref(props.initial)

function handleClick() {
  isCompleted.value = !isCompleted.value
}
</script>