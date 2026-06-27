# Task Spec: 010 Implement Save/Load and Settings Persistence

## Task slug

`persistence`

## Parent feature

`hantasim-full-build`

## Branches

- Base branch: `feature/hantasim-full-build`
- Task branch: `task/hantasim-full-build-010-persistence`
- Task PR target: `feature/hantasim-full-build`

## Manager intent

Persist user settings automatically and allow full simulation snapshots to save and load.

## Scope

### In scope

- Save settings to `saves/hantasim_settings.ron`.
- Save full world snapshot to JSON through UI and/or command path.
- Load full world snapshot including humans, mice, clouds, POIs, statistics, settings, RNG-relevant state, and simulation time.
- Save/Load buttons if not already present.
- Error messages for failed save/load.

### Out of scope

- Cloud sync or remote storage.
- Backward compatibility beyond this initial version unless cheap.

## Expected files or areas

- `src/persistence/`
- `src/ui/save_load.rs`
- `saves/` should be gitignored if generated.

## Implementation requirements

- Do not serialize raw ECS internals when a plain snapshot type is more reliable.
- Generated save files must not be committed.
- Load should replace the current world cleanly.

## Tests to add or update

- Settings round-trip test.
- Snapshot round-trip test for representative world state.
- Load replaces existing world without duplicating entities.

## Verification commands

```sh
cargo fmt --all -- --check
cargo clippy --all-targets -- -D warnings
cargo check --all-targets
cargo test --all-targets
cargo build
```

## Proof requirement

`both_required`

Reason: round-trip tests plus command or recording proof of save/load workflow.

## Acceptance criteria

- [ ] Settings persist between launches.
- [ ] Full world snapshot can be saved and loaded.
- [ ] Save/load failures are visible and non-crashing.
- [ ] Generated save artifacts are ignored by Git.

## Auto-merge eligibility

Task PR may auto-merge into the feature branch only when all standard gates pass.

## Notes for code review node

Look for brittle serialization and accidental commits of local save data.
