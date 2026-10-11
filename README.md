# Lion Lift

Lion Lift connects Claude to your own [Lion Lift](https://lionlift.app/) workout history so it can plan, review, and schedule training across running, pool swimming, cycling, and strength lifting.

## What it does

The plugin bundles eleven skills and one remote MCP server.

**Plan a workout (read-only proposals)**
- `propose-run-workout`: a specific run based on recent load, goals, and time available
- `propose-swim-workout`: a pool session with distances, strokes or drills, and rest
- `propose-bike-workout`: a ride with effort-based targets, without inventing an FTP
- `propose-lift-workout`: a strength session with sets, reps, rest, and a plain-language explanation of the muscle groups worked

**Schedule an approved workout**
- `schedule-run-workout`, `schedule-swim-workout`, `schedule-bike-workout`, `schedule-lift-workout`: turn a workout you approved into a structured Lion Lift session. Claude shows you the exact record and waits for your explicit confirmation before anything is written.

**Review and report**
- `lion-lift-analyzer`: progress and trends over any period, for one sport or all of them
- `compare-workout-to-plan`: what was planned versus what you actually logged
- `generate-report`: an in-depth PDF training report with charts and tables

## Example prompts

- "I have 40 minutes to run tomorrow. Look at my recent training and suggest one workout."
- "What should I lift today? I have 50 minutes and want to get stronger."
- "Review my run, swim, bike, and lift progress over the last 4 weeks."
- "Compare my most recent completed workout with its plan."
- "Please schedule this lift for 2026-11-12: Barbell Back Squat 3 sets of 5 at 95 lb. Show me exactly what will be saved first."

## What data the plugin reads, sends, and writes

The plugin's only network connection is the Lion Lift MCP server declared in `.mcp.json`. It runs no local code, no scripts, and no hooks.

- **Reads:** your own Lion Lift records (lifts, runs, rides, swims, core work, goals, preferences, and daily log entries) are fetched from the Lion Lift server on request so Claude can answer your question. Every call is scoped to the signed-in Lion Lift user.
- **Writes:** the only write actions are scheduling a new lift, run, ride, or pool swim. Each is created only after you confirm the exact details. The plugin cannot delete or edit completed workouts.
- **Not supported:** open-water swims with GPS pace alerts, and deleting workouts.

Privacy policy: https://lionlift.app/privacy/ · Terms: https://lionlift.app/terms/ · Support: https://lionlift.app/support/

## Install

Once the plugin is listed in the Claude plugin directory, install it from there. To try it from a clone of this repository in Claude Code:

```bash
claude --plugin-dir ./lion-lift-plugin
```

## Safety note

Workout suggestions are general training guidance, not medical advice. If you have pain, illness, dizziness, or other concerning symptoms, pause or modify training and consult a qualified professional.

## License

Apache License 2.0. See [LICENSE](LICENSE).
