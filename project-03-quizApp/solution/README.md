# 🧠 Project 3: Simple Quiz App — Solution

**Difficulty:** ★★☆☆☆ (Beginner → Intermediate)
**Concept Focus:** Conditional rendering, event handling, passing props, basic state management

---

# Overview of Implementation

The Simple Quiz App is built using a small set of Vue components that divide responsibilities clearly between **presentation and state management**.

The application presents one question at a time with multiple-choice answers. When the user selects an option, the app evaluates the answer, updates the score if correct, and moves to the next question. After the final question, the results screen displays the user's score and allows restarting the quiz.

The parent component manages quiz progress while child components focus on displaying information and emitting user actions.

Core features implemented:

* Multiple-choice questions
* Answer validation
* Score tracking
* Question progression
* Final results display
* Quiz restart functionality

---

# Architecture Explanation

The application uses a **parent-child component architecture**.

```
App.vue
 ├─ QuizQuestion.vue
 └─ QuizResults.vue
```

### App.vue

The central controller of the application.

Responsibilities:

* Stores quiz state
* Determines which component to display
* Evaluates answers
* Tracks score
* Handles quiz completion

### QuizQuestion.vue

Handles displaying the current question and available answers.

Responsibilities:

* Render question text
* Render answer options
* Capture user selection
* Emit the selected answer to the parent

### QuizResults.vue

Displays final results after the quiz finishes.

Responsibilities:

* Show score
* Provide a restart button

This separation allows each component to focus on a single responsibility.

---

# Key Patterns Used

### 1. Parent-Controlled State

All critical state lives in the parent component.

Example state variables:

```javascript
const currentQuestionIndex = ref(0)
const score = ref(0)
const quizFinished = ref(false)
```

This prevents conflicting sources of truth.

---

### 2. Props Down

Child components receive data through props.

Example:

```javascript (vue)
<QuizQuestion
  :question="questions[currentQuestionIndex]"
  :questionIndex="currentQuestionIndex"
  :totalQuestions="questions.length"
/>
```

Props allow the parent to control what children display.

---

### 3. Events Up

Child components notify the parent about user actions.

Example from the question component:

```javascript
emit('answer-selected', option)
```

The parent listens and updates the state accordingly.

---

### 4. Conditional Rendering

The interface switches between quiz and results using conditional rendering.

Example:

```vue
<QuizQuestion v-if="!quizFinished" />
<QuizResults v-if="quizFinished" />
```

This pattern keeps the UI reactive to state changes.

---

# State Flow Explanation

The quiz operates through a predictable state cycle.

### 1. App loads

Initial state:

```
currentQuestionIndex = 0
score = 0
quizFinished = false
```

The first question is displayed.

---

### 2. User selects an answer

The `QuizQuestion` component emits an event:

```javascript
emit('answer-selected', selectedOption)
```

---

### 3. Parent processes the answer

The parent component evaluates the selection.

Example logic:

```javascript
function handleAnswer(selectedOption) {
  const current = questions[currentQuestionIndex.value]

  if (selectedOption === current.answer) {
    score.value++
  }

  if (currentQuestionIndex.value < questions.length - 1) {
    currentQuestionIndex.value++
  } else {
    quizFinished.value = true
  }
}
```

---

### 4. UI updates automatically

Because Vue tracks reactive state:

* Question index changes → next question renders
* Quiz finished → results component renders

No manual DOM manipulation is required.

---

### 5. Quiz restart

Restart resets the core state variables.

```javascript
function restartQuiz() {
  currentQuestionIndex.value = 0
  score.value = 0
  quizFinished.value = false
}
```

The UI automatically returns to the first question.

---

# Why This Approach

This implementation follows a common frontend architecture principle:

**Single Source of Truth**

All quiz logic and data live in the parent component. Child components remain simple and reusable.

Benefits include:

* Easier debugging
* Predictable data flow
* Clear separation of responsibilities
* Reusable UI components

This approach mirrors patterns used in larger applications such as dashboards, learning platforms, and survey systems.

---

# Possible Improvements

Several enhancements could extend this project further.

### Question Feedback Highlighting

Display whether the selected answer was correct before moving to the next question.

---

### Progress Indicator

Show quiz progress visually.

Example:

```
Question 2 / 5
```

Or a progress bar.

---

### Question Shuffle

Randomize the order of questions to increase replay value.

---

### Timer Per Question

Add a countdown timer that automatically advances if the user does not answer.

---

### Persistent Score Storage

Store quiz results using:

* Local storage
* A backend API

This could allow tracking past attempts.

---

### Animation Between Questions

Smooth transitions can improve the user experience.

Example using Vue transition components.