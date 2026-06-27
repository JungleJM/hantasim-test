# Feature Brief: HantaSim Full Native Desktop Build

## Feature slug

`hantasim-full-build`

## Original request

Build HantaSim from scratch as a native desktop Rust/Bevy application. Implement the full overview feature set, not only a minimal demo. The interface should be polished and educational, assuming users are not familiar with advanced epidemiology or statistics. The goal is also to evaluate how well Loop Manager performs on a broad build, so issues, failure points, and unresolved risks must be tracked.

## Product goal

Create an interactive 2D top-down educational simulation showing environmental hantavirus spread in a closed population. Mice contaminate the environment, humans become infected only by entering contaminated areas, and the UI explains what is happening in plain language.

## Priorities

1. Preserve the core model invariant: no person-to-person transmission.
2. Build the complete native desktop experience described in `HantaSim-Overview`.
3. Keep the simulation understandable to non-expert users through labels, legends, and plain-language explanations.
4. Track performance, implementation failures, and scope risks as first-class output.

## In scope

- Native desktop Rust application using Bevy 0.18.
- 2D top-down simulation world with humans, mice, POIs, contamination clouds, disease progression, statistics, charting, controls, and save/load.
- Polished educational UI with approachable terms and contextual explanations.
- Reproducible generation from a seed.
- Persistent user settings and full world snapshot save/load.
- Proof artifacts showing the app running and the main workflows working.

## Out of scope

- Web/WASM target.
- Medical, public health, or forecasting claims.
- Person-to-person infection.
- Real-world data ingestion.
- Multiplayer or networked simulation.
- Platform-specific app packaging beyond `cargo run`/`cargo build`.

## Architecture constraints

- Browser/client concerns do not apply; this is native desktop only.
- Use Bevy ECS patterns and keep simulation, rendering, UI, statistics, and persistence separated.
- Avoid hiding simulation rules in UI-only code; model behavior should be testable without rendering.
- Keep random generation deterministic when given the same seed.
- Keep task PRs small enough for local-LLM implementation and review.

## Branches and PRs

- Feature branch: `feature/hantasim-full-build`
- Draft feature PR target: `main`
- Task PR target: `feature/hantasim-full-build`

## Interactive test checkpoint

The feature is worth human preview testing once a user can run the app, see a generated world with humans/mice/POIs/clouds, pause/resume, adjust core parameters, observe infection and recovery/death counts changing, and read plain-language explanations of the environmental infection model.

## Acceptance criteria

- [ ] `cargo run` opens a native desktop Bevy app.
- [ ] The app shows a 2D top-down world with humans, mice, POIs, contamination clouds, and death markers.
- [ ] Humans do not infect other humans under any code path.
- [ ] Mice create environmental contamination, and humans can only become infected from that contamination.
- [ ] Users can pause/resume, change simulation speed, move/zoom the camera, restart, save, and load.
- [ ] Users can configure the population, world, virus, cloud, wind, and POI parameters from the UI.
- [ ] Day/night behavior changes human destinations in an understandable way.
- [ ] Statistics and charts show health counts, disease progression, and an R0 estimate with plain-language explanation.
- [ ] Selecting a human shows detailed state in non-expert language.
- [ ] Settings persist between launches, and full world snapshots round-trip.
- [ ] Performance remains acceptable with the default population and a larger stress scenario documented by the manager.
- [ ] Known issues, failed attempts, and unresolved risks are recorded in `issue-log.md`.

## Risks and unknowns

- Bevy 0.18 APIs may have changed enough that local agents need extra iteration.
- GUI/chart implementation may be the highest-risk area because Bevy UI and plotting choices can add complexity.
- Save/load of ECS state can become brittle unless model state is represented with serializable plain data.
- Performance may degrade if cloud-human intersection checks are naive at larger populations.
- Native GUI proof is less automatable than web proof; require command logs plus screenshot or short screen recording.

## Planner notes

The request intentionally asks for the whole build to evaluate Loop Manager behavior. Do not shrink the feature to a toy demo without recording the scope reduction as a failure point. If a task fails twice for similar reasons, narrow or re-split it and record the failure in `issue-log.md`.
