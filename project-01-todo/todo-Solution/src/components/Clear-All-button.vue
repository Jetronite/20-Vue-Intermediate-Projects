<template>
  <div class="delete-button-div">
    <button @click="handleClick">
      <div>
        Delete All Tasks
      </div>
    </button>
  </div>

  <div v-if="showModal" class="modal-overlay">
    <div class="modal">
      <p>Do you want to delete all tasks?</p>
      <button @click="confirmRemoval">Yes</button>
      <button @click="showModal = false">No</button>
    </div>
  </div>

</template>

<script setup>
import { ref } from 'vue'
const showModal = ref(false)
const emit = defineEmits(['clear'])

function handleClick() {
  showModal.value = true
}

function confirmRemoval() {
  emit('clear')
  showModal.value = false
}
</script>

<style scoped>
.delete-button-div {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 30px;
}

.delete-button-div>button {
  background-color: red;
  padding: 6px 11px;
}

.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal {
  background: white;
  padding: 20px;
  border-radius: 8px;
  text-align: center;
}

.modal button {
  margin: 10px;
  padding: 6px 12px;
}
</style>