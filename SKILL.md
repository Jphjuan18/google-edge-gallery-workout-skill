---
name: workout-coach-ultimate
description: Logs sessions with strict numeric data, retrieves history, and visualizes progress.
---

# Workout Coach Ultimate

## Instructions

Call the `run_js` tool using `index.html` and a JSON string for `data` with the following fields:
- **action**: Required. Must be "log_workout" or "get_history".
- **workout_name**: Required. The name of the routine (e.g., "Leg Day").
- **show_dashboard**: (boolean) Set to true if the user wants to see their charts or visual history.
- **workout_data**: Required if action is "log_workout". An array of objects:
  - `name`: (string) The exercise name.
  - `sets`: (array of objects) MUST contain strict numbers for `weight` and `reps`.
    - Example: `[{"weight": 50, "reps": 12}, {"weight": 20, "reps": 12}]`
    - If bodyweight, set weight to 0. 
  - `notes`: (string) Optional.

**Constraints & Logic:**
- If the user asks for their previous workout or asks to see their progress/charts, use action "get_history", set `show_dashboard` to true, extract `workout_name`, and execute.
- **Coach Logic:** When retrieving history, analyze the past few sessions returned by the tool. Suggest a small weight/rep increase if appropriate.
- **Analytics Formatting:** Convert conversational lists of weights (e.g., "weights used: 50, 20") into individual set objects. NEVER use strings for weight or reps.
- Summarize the JSON response naturally back to the user.
