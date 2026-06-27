# Task Spec: 011 Polish UX, Defaults, Help, and Failure Tracking

## Task slug

`polish-issue-log`

## Parent feature

`hantasim-full-build`

## Branches

- Base branch: `feature/hantasim-full-build`
- Task branch: `task/hantasim-full-build-011-polish-issue-log`
- Task PR target: `feature/hantasim-full-build`

## Manager intent

Make the app feel like a polished educational simulation and ensure project issues/failures are tracked.

## Scope

### In scope

- Improve default settings so infection dynamics are visible in a short run.
- Add or refine help/legend copy.
- Add keyboard control hints without clutter.
- Improve visual hierarchy and UI spacing.
- Update `specs/hantasim-full-build/issue-log.md` with observed failures, limitations, and open risks.
- Add README run instructions if no project README exists yet.

### Out of scope

- New major simulation mechanics.
- Platform packaging.

## Expected files or areas

- `src/ui/`
- `src/rendering/`
- `README.md`
- `specs/hantasim-full-build/issue-log.md`

## Implementation requirements

- Assume the user does not know epidemiology terms.
- Avoid overclaiming medical realism.
- Keep the first screen immediately usable.
- Document known issues honestly.

## Tests to add or update

- Any helper tests needed for settings defaults or copy formatting.
- Existing tests should remain stable.

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

Reason: command proof plus screenshot proof of the polished default experience.

## Acceptance criteria

- [ ] First-run experience is understandable without reading source files.
- [ ] Default run produces observable simulation dynamics.
- [ ] Help/legend copy explains entities, colors, and infection route.
- [ ] Issue log is updated with real observations or explicit "none observed" notes.

## Auto-merge eligibility

Task PR may auto-merge into the feature branch only when all standard gates pass.

## Notes for code review node

Treat vague, expert-only wording as a blocker. The UI is part of the educational product.
