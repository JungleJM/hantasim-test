# Task Spec: 006 Implement Disease Progression, Statistics, and R0

## Task slug

`disease-stats`

## Parent feature

`hantasim-full-build`

## Branches

- Base branch: `feature/hantasim-full-build`
- Task branch: `task/hantasim-full-build-006-disease-stats`
- Task PR target: `feature/hantasim-full-build`

## Manager intent

Progress infected humans through disease states and maintain educational statistics.

## Scope

### In scope

- Incubation period, symptomatic duration, mortality probability, recovery, death markers, and immunity duration.
- Counts for healthy, incubating, symptomatic, recovered, and dead humans.
- SIR-style history storage.
- R0 estimate based on tracked environmental infection sources.

### Out of scope

- Final chart rendering.
- Save/load serialization.

## Expected files or areas

- `src/simulation/disease.rs`
- `src/stats/`

## Implementation requirements

- Dead humans must leave active movement/infection participation and create a visible marker hook.
- R0 must be labeled as an estimate in UI-facing data.
- Use plain names where possible so UI can explain them later.

## Tests to add or update

- Incubating to symptomatic transition.
- Symptomatic to recovered/dead transition with deterministic mortality settings.
- Immunity expiration if supported.
- Stats counts match entity states.

## Verification commands

```sh
cargo fmt --all -- --check
cargo clippy --all-targets -- -D warnings
cargo check --all-targets
cargo test --all-targets
cargo build
```

## Proof requirement

`asciinema_required`

Reason: behavior can be primarily proven with deterministic tests and command output.

## Acceptance criteria

- [ ] Disease state progression follows configured timings.
- [ ] Death/recovery behavior is deterministic under controlled settings.
- [ ] Statistics reflect the current world state.
- [ ] R0 estimate data is available for display.

## Auto-merge eligibility

Task PR may auto-merge into the feature branch only when all standard gates pass.

## Notes for code review node

Check for confusing terminology and unsupported epidemiological claims.
