---
name: workout-coach-ultimate
description: Logs sessions with strict numeric data, retrieves history, and suggests progressive overload.
---

# Workout Coach Ultimate

## Instructions

Call the `run_js` tool using `index.html` and a JSON string for `data` with the following fields:
- **action**: Required. Must be "log_workout" or "get_history".
- **workout_name**: Required. The name of the routine (e.g., "Leg Day").
- **workout_data**: Required if action is "log_workout". An array of objects, each representing an exercise:
  - `name`: (string) The exercise name.
  - `sets`: (array of objects) Each object MUST contain strict numbers for `weight` and `reps`. 
    - Example: `[{"weight": 50, "reps": 12}, {"weight": 20, "reps": 12}]`
    - If bodyweight, set weight to 0. 
    - If cardio, leave the array empty.
  - `notes`: (string) Optional. Use this for things like "30 mins", "to failure", or equipment notes.

**Constraints & Logic:**
- If the user asks for their previous workout, use action "get_history", extract `workout_name`, and execute.
- **Coach Logic:** When retrieving history, analyze the past few sessions returned by the tool. If the user has hit the same weight and reps for multiple consecutive sessions, proactively suggest a small weight or rep increase (progressive overload) before reading the rest of the list.
- **Analytics Formatting:** You must convert conversational lists of weights (e.g., "weights used: 50, 20, 50, 50 for 12 reps") into individual set objects within the `sets` array. NEVER use strings for weight or reps.
- The user may reference history: "I did the same as last time but upped my squats to 30lbs." Update the numeric data array accordingly, set action to "log_workout", and execute.
- Summarize the JSON response naturally back to the user.
