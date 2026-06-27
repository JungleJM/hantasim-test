# Proof Plan: HantaSim Full Native Desktop Build

## Feature preview target

Native desktop app launched from the repository with:

```sh
cargo run
```

## Proof standards

- Terminal proof: use asciinema or captured command output for `cargo fmt`, `cargo clippy`, `cargo check`, `cargo test`, and `cargo build`.
- UI proof: use screenshots or short screen recordings for visible simulation, UI controls, charts, selection, save/load, and stress scenarios.
- Every proof record must include commit SHA, command, machine, and any known gaps.

## Required feature-level proof

- Build and test proof for the final feature branch.
- Screenshot or short recording of the simulation running with visible humans, mice, POIs, clouds, stats, and controls.
- Proof that changing speed/pause/settings affects the running simulation.
- Proof that save/load round-trips a world snapshot.
- Proof that the issue log contains any encountered failures or a clear "none observed" entry.

## Task proof entries

Each task spec defines its proof requirement. If proof is not applicable, the task PR must explain why.
