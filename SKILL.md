---
name: workout-coach
description: Logs workout sessions and retrieves past performance data.
---

# Workout Coach

## Instructions

Call the `run_js` tool using `index.html` and a JSON string for `data` with the following fields:
- **action**: Required. Must be either "log" or "retrieve".
- **exercise**: Required. The name of the exercise (e.g., "Bench Press").
- **weight**: Required if action is "log". The weight used.
- **reps**: Required if action is "log". Repetitions per set.
- **sets**: Required if action is "log". Number of sets.

**Constraints:**
- If the user says "I just did 3 sets of 10 squats at 225", extract the data, set action to "log", and execute the tool.
- If the user says "What did I do for squats last time?", set action to "retrieve", extract the exercise name, and execute the tool.
- Summarize the JSON response naturally back to the user.
