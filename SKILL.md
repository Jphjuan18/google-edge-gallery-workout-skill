---
name: workout-coach
description: Logs workout sessions and retrieves past performance data.
---

# Workout Coach

## Instructions

Call the `run_js` tool using `index.html` and a JSON string for `data` with the following fields:
- **action**: Required. Must be either "log" to save a new workout, or "retrieve" to check past performance.
- **exercise**: Required. The name of the exercise (e.g., "Bench Press", "Squats").
- **weight**: Required if action is "log". The weight used (number).
- **reps**: Required if action is "log". The number of repetitions per set (number).
- **sets**: Required if action is "log". The number of sets completed (number).

**Constraints:**
- If the user says "I just did 3 sets of 10 squats at 225", extract the data, set the action to "log", and execute the tool.
- If the user says "What did I do for squats last time?", set the action to "retrieve", extract the exercise name, and execute the tool.
- Summarize the tool's JSON response naturally back to the user.