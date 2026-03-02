# Simple Quiz App

**Difficulty:** ★★☆☆☆ (Beginner → Intermediate)
**Concept Focus:** Conditional rendering, event handling, component communication, basic app state management

---

## Screenshot

*(Add a screenshot of the running application here once complete.)*

---

## Overview

The Simple Quiz App is a step up from basic list and counter projects. It introduces dynamic interfaces driven by user interaction and shared state across components.

Users answer multiple-choice questions, receive instant feedback, and see their final score at the end of the quiz.

This project is designed to strengthen your understanding of how components communicate and how application state flows through a Vue application.

---

## Learning Objectives

By completing this project, you should be able to:

* Render content conditionally based on user interaction.
* Handle user events (clicks, selections).
* Pass data between parent and child components using props.
* Emit events from child components back to parents.
* Manage and update shared application state.
* Track and calculate a score dynamically.
* Display feedback messages based on user answers.

---

## Feature Requirements

Your implementation must include:

* A set of multiple-choice questions.
* Display of one question at a time.
* Clickable answer options.
* Immediate visual or textual feedback indicating correct or incorrect answers.
* Score tracking.
* A final results screen showing total score.
* An option to restart the quiz.

Optional enhancements (stretch goals):

* Timer per question.
* Question progress indicator (e.g., 2 of 5).
* Shuffle questions.
* Store high score locally.

---

## Evaluation Checklist

Use this to evaluate your implementation:

* Questions render correctly.
* Only one question is shown at a time.
* User selection updates state properly.
* Correct answers increment the score.
* Feedback displays accurately.
* Final score calculation is correct.
* Quiz can restart without page refresh.
* Components are logically separated.
* Props and emits are used appropriately.
* State management is clean and predictable.

---

## Reflection Questions

After completing the project, consider:

* Where does application state live, and why?
* What data should remain local to a component?
* How did props and emits help manage data flow?
* What would break if state was misplaced?
* How could this scale if the quiz had 100 questions?
* When would you introduce a global state manager?

---

## Learning Flow

1. Review the Starter Version
2. Build your own implementation
3. Compare with the Solution Version
4. Refactor and improve
5. Extend with bonus features

---

## Estimated Time

2–4 hours

---

## Prerequisites

* Basic Vue fundamentals (ref, reactive state)
* Understanding of props and emits
* Comfort with template syntax
* Experience with basic conditional rendering
* Simple event handling

---

This project is where apps start feeling like actual products instead of exercises. You’re moving from reactive widgets to interactive experiences. That’s a shift.

And remember: small deliberate complexity now builds architecture instincts later.
