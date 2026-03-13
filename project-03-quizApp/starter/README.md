# 🧠 Project 3: Simple Quiz App

**Difficulty:** ★★☆☆☆ (Beginner → Intermediate)
**Concept Focus:** Conditional rendering, event handling, passing props, basic state management

---

## 📦 Setup Instructions

1. Clone the repository.

```bash
git clone <your-repo-url>
```

2. Navigate into the project folder.

```bash
cd simple-quiz-app
```

3. Install dependencies.

```bash
npm install
```

4. Start the development server.

```bash
npm run dev
```

5. Open the local development URL shown in your terminal.

---

## 📁 Project Structure

```
src/
 ├─ components/
 │   ├─ QuizQuestion.vue
 │   ├─ QuizResults.vue
 │
 ├─ data/
 │   └─ questions.js
 │
 ├─ App.vue
 ├─ main.js
```

**Overview**

* **questions.js** – Contains the quiz questions and answers.
* **QuizQuestion.vue** – Responsible for displaying a single question and answer options.
* **QuizResults.vue** – Displays the final score and feedback.
* **App.vue** – Manages quiz state and coordinates communication between components.

Think of **App.vue** as the conductor of an orchestra. The components play their instruments, but the conductor keeps everything in rhythm.

---

## 🎯 Your Task

Build a functioning quiz application with the following behavior:

1. Display one question at a time.
2. Show multiple-choice answers for each question.
3. Allow the user to select an answer.
4. Provide feedback indicating whether the selected answer is correct.
5. Move to the next question after answering.
6. Track the user’s score.
7. Display the final score after all questions are answered.

The application should update the interface dynamically based on user actions.

---

## ⚙️ Constraints

* Use **Vue components** to separate responsibilities.
* Pass data between components using **props**.
* Communicate actions back to the parent using **events**.
* Use **conditional rendering** to control which parts of the UI appear.
* Do **not modify the question data structure**.

Avoid building everything inside one component. The purpose of this exercise is learning **component communication**.

---

## 🧭 Hints

Think about **where the main state should live**.

The score, the current question index, and quiz progress usually belong in a central place (often the parent component).

A typical interaction flow looks like this:

User selects answer →
Component emits event →
Parent updates score/state →
Parent passes new data down →
UI updates.

The magic of reactive frameworks happens when **state drives the interface**.

---

## 🚀 Optional Challenges

If the basic quiz works, experiment further.

Try adding:

* A **progress indicator** (Question 2 of 5)
* A **restart quiz button**
* Highlighting the **correct answer after selection**
* Simple **animations between questions**
* A **timer for each question**

Small features like these sharpen your understanding of state transitions.

---

## ⚠️ Common Pitfalls

**Putting all logic in one component**

This defeats the learning objective. Split responsibilities.

**Mutating props directly**

Props should be treated as read-only. Emit events instead.

**Forgetting to reset state**

When restarting the quiz, ensure the score and question index reset.

**Rendering everything at once**

Use conditional rendering to show only the relevant section.

---

## 💡 Advice

Programming skill grows through small, deliberate experiments. A project like this may look simple, but inside it hides the core ideas used in large-scale applications:

state → events → UI updates.

Master this loop and frameworks like Vue start feeling less like magic and more like well-behaved machinery.

Ship the first version quickly. Improve it afterward. Progress beats perfection every time.