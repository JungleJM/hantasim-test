# Task Spec: 003 Generate World, POIs, Humans, and Mice

## Task slug

`world-generation`

## Parent feature

`hantasim-full-build`

## Branches

- Base branch: `feature/hantasim-full-build`
- Task branch: `task/hantasim-full-build-003-world-generation`
- Task PR target: `feature/hantasim-full-build`

## Manager intent

Generate a reproducible simulation world containing POIs, humans assigned to homes, and mice within bounds.

## Scope

### In scope

- World bounds and configurable counts.
- POI generation for Home, Work, Shop, Cafe, and Park.
- Human spawning with home assignment and initial health state.
- Mouse spawning within world bounds.
- Restart/regenerate hook from settings.

### Out of scope

- Advanced movement behavior.
- Infection logic.
- Final UI for editing every setting.

## Expected files or areas

- `src/simulation/generation.rs`
- `src/simulation/components.rs`
- early rendering/debug visualization if useful.

## Implementation requirements

- Same seed plus same settings must produce the same entity layout.
- Every human must have a valid home.
- Generated positions must be inside world bounds.

## Tests to add or update

- Deterministic generation test.
- Bounds test.
- Home assignment test.

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

Reason: command proof for tests and screenshot proof that generated entities are visible if rendering exists by this point.

## Acceptance criteria

- [ ] Default world generation creates all required entity categories.
- [ ] Re-running with the same seed is reproducible.
- [ ] Restart/regeneration clears old entities and creates a fresh world.

## Auto-merge eligibility

Task PR may auto-merge into the feature branch only when all standard gates pass.

## Notes for code review node

Check for off-by-one entity counts and nondeterministic RNG usage.
