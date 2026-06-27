# Feature Human Review Readiness

## Interactive preview

- Preview type: native desktop
- Launch command: `cargo run`
- Feature branch: `feature/hantasim-full-build`

## Human test script

1. Launch the app with `cargo run`.
2. Confirm the app explains that infection comes from contaminated environments, not direct human transmission.
3. Start with defaults and observe humans, mice, POIs, clouds, and health counts.
4. Pause and resume.
5. Change speed.
6. Change at least three simulation settings, restart, and confirm the new world reflects them.
7. Select a human and read their state panel.
8. Toggle cloud visibility or static mouse contamination mode.
9. Save a world, change the simulation, load the world, and confirm state returns.
10. Review `issue-log.md` and performance notes.

## Required before human review

- [ ] All required Loop Manager checks pass.
- [ ] Feature-level proof artifacts are recorded.
- [ ] Issue log is updated.
- [ ] Known limitations are listed.
