# Task Spec: 012 Performance, Stress Testing, and Release Hardening

## Task slug

`performance-hardening`

## Parent feature

`hantasim-full-build`

## Branches

- Base branch: `feature/hantasim-full-build`
- Task branch: `task/hantasim-full-build-012-performance-hardening`
- Task PR target: `feature/hantasim-full-build`

## Manager intent

Evaluate how well the full app runs, fix practical performance problems, and prepare the feature for human review.

## Scope

### In scope

- Run default and larger stress scenarios.
- Record performance observations in `issue-log.md`.
- Optimize obvious hot paths, especially cloud-human checks, without changing model behavior.
- Verify all documented controls and workflows.
- Prepare final proof results.

### Out of scope

- Rewriting the app architecture unless a severe blocker is recorded.
- Platform-specific installers.
- New feature scope.

## Expected files or areas

- `src/simulation/`
- `src/rendering/`
- `specs/hantasim-full-build/issue-log.md`
- `specs/hantasim-full-build/proof/`

## Implementation requirements

- Keep optimizations behavior-preserving.
- Record any performance limitation that remains.
- Do not weaken checks to pass.
- This task is not auto-merge eligible by default; manager should inspect results before feature review.

## Tests to add or update

- Regression tests for any optimized behavior.
- Add simple benchmark-like diagnostics only if they do not destabilize CI.

## Verification commands

```sh
cargo fmt --all -- --check
cargo clippy --all-targets -- -D warnings
cargo check --all-targets
cargo test --all-targets
cargo build
cargo run
```

## Proof requirement

`both_required`

Reason: command proof, final UI proof, and stress/performance evidence are required.

## Acceptance criteria

- [ ] Default scenario runs smoothly enough for interactive testing.
- [ ] A larger stress scenario is documented with observed behavior.
- [ ] Any remaining performance or correctness issues are listed.
- [ ] Final proof artifacts and readiness notes are complete.

## Auto-merge eligibility

No. Manager should hold this task for explicit review before feature-level human testing.

## Notes for code review node

Focus on whether performance claims are backed by evidence and whether any optimization changed model behavior.
