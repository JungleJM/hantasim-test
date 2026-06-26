# Task Spec: 001 Scaffold Rust/Bevy App Architecture

## Task slug

`scaffold`

## Parent feature

`hantasim-full-build`

## Branches

- Base branch: `feature/hantasim-full-build`
- Task branch: `task/hantasim-full-build-001-scaffold`
- Task PR target: `feature/hantasim-full-build`

## Manager intent

Create a runnable native desktop Rust/Bevy 0.18 application with a clean module layout for simulation, rendering, UI, statistics, and persistence.

## Scope

### In scope

- Add `Cargo.toml`, source tree, app startup, plugin/module structure, and a blank Bevy window.
- Add initial resources for app state, simulation clock, and deterministic seed.
- Add minimal tests that compile non-rendering helpers.

### Out of scope

- Full simulation behavior.
- Polished visuals or final UI.
- Save/load implementation.

## Expected files or areas

- `Cargo.toml` - Rust package and Bevy dependencies.
- `src/main.rs` - app bootstrap.
- `src/simulation/`, `src/rendering/`, `src/ui/`, `src/stats/`, `src/persistence/` - module skeletons.

## Implementation requirements

- Use Bevy 0.18.
- Keep app state resources separate from rendering systems.
- The app must launch with `cargo run`.
- The window title should identify HantaSim.

## Tests to add or update

- Add at least one small unit test for deterministic seed/resource initialization.

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

Reason: prove the project builds, tests, and launches far enough for a native window smoke test.

## Acceptance criteria

- [ ] `cargo run` opens a Bevy window.
- [ ] Required check commands pass.
- [ ] Module boundaries exist for later tasks.
- [ ] No placeholder dependency or generated junk is committed.

## Auto-merge eligibility

Task PR may auto-merge into the feature branch only when:

- [ ] tests passed
- [ ] secret scan passed
- [ ] Codex/OpenAI PR review decision is `approve`
- [ ] local-LLM review decision is `approve`
- [ ] no blocking findings remain
- [ ] task acceptance criteria are satisfied

## Notes for code review node

Focus on dependency correctness, Bevy 0.18 compatibility, and whether the structure supports future tasks without a rewrite.
