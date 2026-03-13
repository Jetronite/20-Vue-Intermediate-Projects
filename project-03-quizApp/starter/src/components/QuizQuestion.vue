<template>
  <div class="question-card">
    <p>Question {{ questionIndex + 1 }} / {{ totalQuestions }}</p>

    <h2>{{ question.question }}</h2>

    <div class="options">
      <button v-for="option in question.options" :key="option" @click="selectAnswer(option)">
        {{ option }}
      </button>
    </div>

    <!-- Feedback placeholder -->
    <p v-if="feedback">{{ feedback }}</p>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const props = defineProps({
  question: Object,
  questionIndex: Number,
  totalQuestions: Number
})

const emit = defineEmits(['answer-selected'])

const feedback = ref('')

function selectAnswer(option) {
  // TODO:
  // Determine if the answer is correct
  // Update feedback message
  // Emit event to parent

  emit('answer-selected', option)
}
</script>

<style>
.question-card {
  margin-top: 20px;
}

.options {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
</style>