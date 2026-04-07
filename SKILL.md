---
name: workout-coach-pro
description: Logs sessions, retrieves history, and acts as a coach to suggest progressive overload.
---

# Workout Coach Pro

## Instructions

Call the `run_js` tool using `index.html` and a JSON string for `data` with the following fields:
- **action**: Required. Must be "create_template", "log_workout", or "get_history".
- **workout_name**: Required. The name of the routine (e.g., "Leg Day", "Upper Body Day").
- **workout_data**: Required if action is "log_workout". An array of objects, each containing: 
  - `name`: (string) The exercise name.
  - `weight`: (string or number) e.g., 25, "0/3", "bodyweight", "0".
  - `reps`: (string or number) e.g., 15, "failure", "time".
  - `sets`: (string or number) e.g., 3.
  - `duration_or_notes`: (string) Optional. e.g., "30 mins", "Elliptical", "Stretches".

**Constraints & Logic:**
- If the user asks for their previous workout, use action "get_history", extract `workout_name`, and execute.
- **Coach Logic:** When retrieving history, analyze the past few sessions returned by the tool. If the user has hit the same weight and reps for multiple consecutive sessions, proactively suggest a small weight or rep increase (progressive overload) before reading the rest of the list.
- When logging a workout, if an exercise like "Elliptical" has no weights/reps, put that information in `duration_or_notes`.
- The user may reference their history and say "I did the same as last time but upped my squats to 30lbs." Use the context of the conversation to update the data array, set action to "log_workout", and execute.
