# Task Spec: 004 Implement Movement and Day/Night Behavior

## Task slug

`movement-day-night`

## Parent feature

`hantasim-full-build`

## Branches

- Base branch: `feature/hantasim-full-build`
- Task branch: `task/hantasim-full-build-004-movement-day-night`
- Task PR target: `feature/hantasim-full-build`

## Manager intent

Make humans and mice move believably, with virtual time and day/night behavior influencing human destinations.

## Scope

### In scope

- Human movement between POIs using weighted destination selection.
- Night behavior that sends humans home.
- Symptomatic movement slowdown hook if disease state exists.
- Mouse random/smooth movement within bounds.
- Simulation clock and speed multiplier integration.

### Out of scope

- Contamination spawning.
- Disease progression.
- Final UI controls for all speed presets.

## Expected files or areas

- `src/simulation/movement.rs`
- `src/simulation/time.rs`

## Implementation requirements

- Movement must respect world bounds.
- Dead humans must not continue normal movement.
- Speed multiplier must affect movement consistently.
- Destination choice should be understandable and configurable later.

## Tests to add or update

- Bounds tests for mouse movement.
- Night destination/home behavior test.
- Symptomatic speed helper test if implemented here.

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

Reason: tests prove helper behavior; visual proof should show movement and day/night changes.

## Acceptance criteria

- [ ] Humans move between destinations.
- [ ] Mice move smoothly and remain in bounds.
- [ ] Night behavior changes human destinations toward home.
- [ ] Simulation speed changes movement rate.

## Auto-merge eligibility

Task PR may auto-merge into the feature branch only when all standard gates pass.

## Notes for code review node

Watch for frame-rate dependent movement and random behavior that breaks reproducibility.
