# Task Breakdown: HantaSim Full Native Desktop Build

## Feature slug

`hantasim-full-build`

## Sizing rule

Prefer small, reviewable task PRs. This project is broad, so each task should own one layer or user-visible workflow. If a task starts touching unrelated layers, split it and update this file.

## Task list

| N | Task | Branch | PR target | Proof | Auto-merge eligible |
|---|------|--------|-----------|-------|---------------------|
| 001 | Scaffold Rust/Bevy app architecture | `task/hantasim-full-build-001-scaffold` | `feature/hantasim-full-build` | asciinema | yes |
| 002 | Build deterministic simulation domain state | `task/hantasim-full-build-002-sim-domain` | `feature/hantasim-full-build` | asciinema | yes |
| 003 | Generate world, POIs, humans, and mice | `task/hantasim-full-build-003-world-generation` | `feature/hantasim-full-build` | screenshot + asciinema | yes |
| 004 | Implement movement and day/night behavior | `task/hantasim-full-build-004-movement-day-night` | `feature/hantasim-full-build` | screenshot + asciinema | yes |
| 005 | Implement contamination and environmental infection | `task/hantasim-full-build-005-contamination-infection` | `feature/hantasim-full-build` | screenshot + asciinema | yes |
| 006 | Implement disease progression, statistics, and R0 | `task/hantasim-full-build-006-disease-stats` | `feature/hantasim-full-build` | asciinema | yes |
| 007 | Render top-down educational simulation view | `task/hantasim-full-build-007-rendering` | `feature/hantasim-full-build` | screenshot | yes |
| 008 | Build controls and configuration UI | `task/hantasim-full-build-008-controls-ui` | `feature/hantasim-full-build` | screenshot + short-screen-recording | yes |
| 009 | Build charts, selected-human panel, and plain-language explanations | `task/hantasim-full-build-009-educational-stats-ui` | `feature/hantasim-full-build` | screenshot + short-screen-recording | yes |
| 010 | Implement save/load and settings persistence | `task/hantasim-full-build-010-persistence` | `feature/hantasim-full-build` | asciinema | yes |
| 011 | Polish UX, defaults, help, and failure tracking | `task/hantasim-full-build-011-polish-issue-log` | `feature/hantasim-full-build` | screenshot + asciinema | yes |
| 012 | Performance, stress testing, and release hardening | `task/hantasim-full-build-012-performance-hardening` | `feature/hantasim-full-build` | asciinema + short-screen-recording | no |

## Human-test checkpoint

Stop for human preview testing when these tasks are merged into the feature branch:

- [ ] 001 scaffold
- [ ] 002 simulation domain
- [ ] 003 world generation
- [ ] 004 movement and day/night
- [ ] 005 contamination and infection
- [ ] 006 disease and statistics
- [ ] 007 rendering
- [ ] 008 controls UI
- [ ] 009 educational stats UI
- [ ] 010 persistence
- [ ] 011 polish and issue log
- [ ] 012 performance hardening

## Dedicated test tasks

No separate test-only task is planned initially. Each task must add tests for its own behavior where possible. If tests lag behind implementation, create a dedicated test task before feature review.

## Re-splitting triggers

Manager should re-split or narrow a task if:

- review fails twice for related reasons;
- Bevy UI code, simulation code, and persistence code are mixed in one PR;
- the developer weakens tests, lint, or checks;
- performance proof cannot be run deterministically;
- native desktop proof cannot show the claimed behavior.
