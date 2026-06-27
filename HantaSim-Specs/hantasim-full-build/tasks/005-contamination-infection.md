# Task Spec: 005 Implement Contamination and Environmental Infection

## Task slug

`contamination-infection`

## Parent feature

`hantasim-full-build`

## Branches

- Base branch: `feature/hantasim-full-build`
- Task branch: `task/hantasim-full-build-005-contamination-infection`
- Task PR target: `feature/hantasim-full-build`

## Manager intent

Implement the core model: mice contaminate the environment, and humans become infected only by entering contaminated areas.

## Scope

### In scope

- Mouse cloud spawning interval.
- Cloud radius, intensity, lifetime, diffusion, decay, and wind drift.
- Static contamination circle mode around mice.
- Human infection probability from clouds/circles.
- Infection source tracking for later R0/statistics.

### Out of scope

- Full disease progression after infection.
- Final chart UI.
- Performance optimization beyond reasonable baseline.

## Expected files or areas

- `src/simulation/contamination.rs`
- `src/simulation/infection.rs`
- `src/simulation/wind.rs`

## Implementation requirements

- No direct human-to-human infection system.
- Infection checks must ignore dead/recovered immune humans where appropriate.
- Cloud decay and expiration must remove or deactivate old clouds.
- Wind behavior must be deterministic under seed/settings.

## Tests to add or update

- Susceptible human inside cloud can become incubating under deterministic high-probability settings.
- Human outside cloud does not become infected.
- Human near infected human but outside cloud does not become infected.
- Cloud lifetime/decay behavior.

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

Reason: this is the central behavioral invariant and should have tests plus visual proof of clouds/infection.

## Acceptance criteria

- [ ] Mice create contamination according to settings.
- [ ] Clouds expand, drift, decay, and expire.
- [ ] Static circle mode works as an alternative model.
- [ ] Humans become infected only through environmental contamination.
- [ ] Tests protect against accidental direct transmission.

## Auto-merge eligibility

Task PR may auto-merge into the feature branch only when all standard gates pass.

## Notes for code review node

This is the most important model correctness task. Block if any path allows humans to infect humans.
