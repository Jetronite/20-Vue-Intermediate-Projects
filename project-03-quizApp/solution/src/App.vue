<template>
  <div class="app">
    <h1>Simple Quiz App</h1>

    <!-- Quiz section -->
    <QuizQuestion v-if="!quizFinished" :question="currentQuestion" :questionIndex="currentQuestionIndex"
      :totalQuestions="questions.length" @answer-selected="handleAnswer" />

    <!-- Results section -->
    <QuizResults v-if="quizFinished" :score="score" :total="questions.length" @restart="restartQuiz" />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import QuizQuestion from './components/QuizQuestion.vue'
import QuizResults from './components/QuizResults.vue'
import questions from './data/Questions'

const currentQuestionIndex = ref(0)
const score = ref(0)
const quizFinished = ref(false)

const currentQuestion = questions[currentQuestionIndex.value]

function handleAnswer(selectedOption) {
  // TODO:
  // 1. Check if answer is correct
  // 2. Update score if correct
  // 3. Move to next question
  // 4. Mark quizFinished when quiz ends
}

function restartQuiz() {
  // TODO:
  // Reset quiz state
}
</script>

<style>
.app {
  font-family: Arial, sans-serif;
  max-width: 600px;
  margin: auto;
  text-align: center;
}
</style>
