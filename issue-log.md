# Issue Log: HantaSim Full Native Desktop Build

Use this file to track failure points, scope changes, blocked tasks, and performance findings during the Loop Manager run.

## Open issues

- 2026-06-27 full-build launch failed before producing usable task PRs.
  - Affected task branches:
    - `task/hantasim-full-build-001-scaffold`
    - `task/hantasim-full-build-002-sim-domain`
    - `task/hantasim-full-build-003-world-generation`
  - Observed behavior:
    - Task 001 reached `needs_human` after 3 attempts.
    - Task 002 reached `needs_human` after 3 attempts.
    - Task 003 reached `needs_human` after 3 attempts.
    - Task 004 had a local worktree/branch when the run was stopped.
    - No remote task branches were pushed.
  - Failure details:
    - Oracle sometimes returned invalid JSON: `Expecting value: line 1 column 1`.
    - Oracle sometimes returned malformed JSON: `Unterminated string`.
    - Oracle returned corrupt unified diffs that failed `git apply --check`.
    - Denbuntu SSH checks intermittently timed out connecting to port 22.
  - Likely cause:
    - The implementer prompt/model path is not yet reliable enough for large
      multi-file unified diffs.
    - The checker path still depends on Denbuntu SSH availability.
    - Loop Manager correctly blocked corrupt patches, but the full build should
      not proceed to later tasks after earlier task failures.
  - Current mitigation:
    - Full run was stopped manually.
    - Bluefin `GITEA_DRY_RUN` was reset to `true`.
    - Keep this as the first real production failure point before relaunching.
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
