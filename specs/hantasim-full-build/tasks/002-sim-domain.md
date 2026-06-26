# Task Spec: 002 Build Deterministic Simulation Domain State

## Task slug

`sim-domain`

## Parent feature

`hantasim-full-build`

## Branches

- Base branch: `feature/hantasim-full-build`
- Task branch: `task/hantasim-full-build-002-sim-domain`
- Task PR target: `feature/hantasim-full-build`

## Manager intent

Define the core simulation data model and scheduling without implementing all behavior.

## Scope

### In scope

- Components/resources for humans, mice, POIs, contamination clouds, disease state, settings, and simulation time.
- Health-state enum with Susceptible, Incubating, Symptomatic, Recovered, and Dead.
- Simulation system sets ordered for input/config, movement, contamination, infection, disease progression, stats, rendering sync, and persistence hooks.
- Deterministic RNG handling for reproducible setup.

### Out of scope

- Final generation algorithms.
- Final UI controls.
- Rendering polish.

## Expected files or areas

- `src/simulation/` - domain types, resources, systems, schedule labels.
- `src/settings.rs` or equivalent - serializable simulation settings.

## Implementation requirements

- Make the "humans do not infect humans" invariant explicit in type names, comments, or tests.
- Prefer serializable plain data where it will later be saved.
- Avoid coupling domain state to UI widgets.

## Tests to add or update

- Health-state transition helper tests if helpers exist.
- Deterministic RNG/resource tests.
- A test or documented assertion that no direct human-to-human infection system exists.

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

Reason: this is mostly domain and compile/test proof.

## Acceptance criteria

- [ ] Core components/resources compile.
- [ ] Simulation ordering is explicit.
- [ ] Reproducible seed handling is present.
- [ ] The environmental-only infection invariant is documented and testable.

## Auto-merge eligibility

Task PR may auto-merge into the feature branch only when all standard gates pass.

## Notes for code review node

Look for premature UI/rendering coupling and hidden direct transmission assumptions.
