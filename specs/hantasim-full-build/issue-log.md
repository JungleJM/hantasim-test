# Issue Log: HantaSim Full Native Desktop Build

Use this file to track failure points, scope changes, blocked tasks, and performance findings during the Loop Manager run.

## Open issues

- Native desktop proof is less deterministic than browser proof. Require exact commands plus screenshot or short recording for UI-facing tasks.
- Bevy 0.18 UI and camera APIs should be verified early in task 001 to avoid propagating bad patterns.
- Full save/load should be designed around serializable simulation snapshots, not raw ECS internals.
- Cloud-human collision checks may become a performance bottleneck. Task 012 must measure and optimize if needed.

## Resolved issues

- None yet.

## Failure points to record

For each failure, add:

- date;
- task branch;
- command or action that failed;
- observed behavior;
- likely cause;
- resolution or next split.

## Performance observations

Record default and stress scenario results here. Include machine, command, population/mouse/cloud counts, approximate FPS if available, and subjective UI responsiveness.
