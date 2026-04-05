---
name: smart-alarm
description: Define alarmes e cronômetros integrados ao sistema.
---

# Smart Alarm

## Instructions

Call the `run_intent` tool with the following exact parameters:

- intent: set_alarm
- parameters: JSON string with:
  - action: "set_alarm" or "set_timer"
  - duration_minutes: Number
  - label: String
