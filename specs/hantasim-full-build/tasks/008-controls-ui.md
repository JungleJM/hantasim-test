# Task Spec: 008 Build Controls and Configuration UI

## Task slug

`controls-ui`

## Parent feature

`hantasim-full-build`

## Branches

- Base branch: `feature/hantasim-full-build`
- Task branch: `task/hantasim-full-build-008-controls-ui`
- Task PR target: `feature/hantasim-full-build`

## Manager intent

Create the main user control surface for running, pausing, speeding up, restarting, and configuring the simulation.

## Scope

### In scope

- Pause/resume button and Space shortcut.
- Speed presets from seconds-per-second through hours-per-second.
- Restart/regenerate control.
- UI controls for world size, humans, mice, movement speed, POI counts, humans per home, virus timings, mortality, cloud interval/probability, cloud radius/lifetime/diffusion, wind, cloud visibility, and static mouse circle mode.
- Plain-language labels and tooltips.

### Out of scope

- Final charts.
- Save/load buttons if persistence is not ready.

## Expected files or areas

- `src/ui/controls.rs`
- `src/settings.rs`

## Implementation requirements

- Use controls appropriate to value types: toggles for booleans, sliders/inputs for numbers, menus or segmented controls for presets.
- Do not use unexplained statistical jargon in labels.
- Changes should either apply live where safe or clearly require restart/regenerate.
- Text must fit in the panel at common desktop sizes.

## Tests to add or update

- Settings validation/clamping tests.
- Speed preset mapping tests.

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

Reason: settings logic needs tests and UI proof must show controls working.

## Acceptance criteria

- [ ] Users can pause/resume and change speed.
- [ ] Users can edit core settings without code changes.
- [ ] Restart applies generation settings.
- [ ] Labels are understandable to users unfamiliar with statistics.

## Auto-merge eligibility

Task PR may auto-merge into the feature branch only when all standard gates pass.

## Notes for code review node

Check UI density and wording. Do not accept labels that only make sense to domain experts.
