# Setup Notes

## 2026-06-27

- Added `plan-contract.bluefin.yaml` for the eventual Bluefin managed build.
- Pushed `feature/hantasim-full-build` to Gitea as the task PR target branch.
- Confirmed Bluefin does not currently have Gitea SSH access for
  `git@appliedsci.tail90eacc.ts.net:411`; cloning `hantasim-test` from Bluefin
  failed with `Permission denied (publickey)`.
- Configured Bluefin token-backed HTTPS access through `~/.netrc` using the
  local `GITEA_BLUEFIN_TOKEN`.
- Cloned `hantasim-test` on Bluefin at `/var/home/j/code/hantasim-test`.
- Launched the full PlanContract once, then stopped it after early task
  failures. See `issue-log.md`.
- Reset Bluefin `GITEA_DRY_RUN=true` after stopping the failed run.
- Removed failed local Bluefin task worktrees/branches for tasks 001-004 so the
  same branch names can be reused on relaunch.

The PlanContract intentionally uses Bluefin's intended local checkout path:

```text
/var/home/j/code/hantasim-test
```

Bluefin currently uses token-backed HTTPS rather than Gitea SSH for this repo.
