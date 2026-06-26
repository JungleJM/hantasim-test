# Task Spec: 007 Render Top-Down Educational Simulation View

## Task slug

`rendering`

## Parent feature

`hantasim-full-build`

## Branches

- Base branch: `feature/hantasim-full-build`
- Task branch: `task/hantasim-full-build-007-rendering`
- Task PR target: `feature/hantasim-full-build`

## Manager intent

Render the simulation clearly enough that users can identify humans, mice, POIs, clouds, disease states, and death markers.

## Scope

### In scope

- Top-down sprites/shapes for all entity categories.
- Distinct visual states for human health.
- Cloud visuals with radius/intensity cues and optional visibility.
- POI markers by type.
- Camera pan and zoom controls.
- Human click selection hook.

### Out of scope

- Final control panel and charts.
- Save/load.

## Expected files or areas

- `src/rendering/`
- `src/input.rs` if needed.

## Implementation requirements

- Visuals should prioritize legibility over decorative complexity.
- Avoid a one-color UI; use clear category colors.
- Text and markers must not overlap incoherently at default zoom.
- Selection should be robust enough for crowded scenes.

## Tests to add or update

- Non-rendering selection math tests if possible.
- Compile/check coverage for rendering systems.

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

Reason: command proof must show the app builds, and visual behavior must be proven with screenshot or short screen recording because this is a native desktop app.

## Acceptance criteria

- [ ] Default app view shows all core world elements.
- [ ] Camera pan/zoom works.
- [ ] Human selection hook works.
- [ ] Visual categories are distinguishable.

## Auto-merge eligibility

Task PR may auto-merge into the feature branch only when all standard gates pass.

## Notes for code review node

Block if the scene is technically rendered but not understandable to a non-expert user.
