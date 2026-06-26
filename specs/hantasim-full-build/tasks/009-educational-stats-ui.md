# Task Spec: 009 Build Charts, Selected-Human Panel, and Plain-Language Explanations

## Task slug

`educational-stats-ui`

## Parent feature

`hantasim-full-build`

## Branches

- Base branch: `feature/hantasim-full-build`
- Task branch: `task/hantasim-full-build-009-educational-stats-ui`
- Task PR target: `feature/hantasim-full-build`

## Manager intent

Turn simulation data into an educational interface that explains what the user is seeing without assuming stats knowledge.

## Scope

### In scope

- Real-time count display for healthy, incubating, symptomatic, recovered, and deaths.
- SIR/history chart or equivalent visual trend display.
- R0 estimate display with plain-language explanation and caveat.
- Selected-human detail panel.
- Legend explaining colors, entities, clouds, and the no-direct-transmission rule.

### Out of scope

- Save/load.
- New simulation rules.

## Expected files or areas

- `src/ui/stats_panel.rs`
- `src/ui/legend.rs`
- `src/stats/`

## Implementation requirements

- Use plain-language terms alongside technical labels where needed.
- R0 must be described as an estimate for this toy simulation, not a medical claim.
- Charts should be readable at normal desktop window sizes.

## Tests to add or update

- Formatting/helper tests for plain-language status text.
- Stats history bounds or retention tests if applicable.

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

Reason: tests can cover data formatting; screenshot/recording must show readable panels and chart behavior.

## Acceptance criteria

- [ ] Health counts update during simulation.
- [ ] Trend visualization is visible and understandable.
- [ ] Selected human panel shows state and relevant details.
- [ ] UI clearly states that humans are infected by contaminated areas, not each other.

## Auto-merge eligibility

Task PR may auto-merge into the feature branch only when all standard gates pass.

## Notes for code review node

Review wording as product behavior, not decoration. Confusing wording is a functional bug here.
