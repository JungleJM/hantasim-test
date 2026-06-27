# Setup Notes

## 2026-06-27

- Added `plan-contract.bluefin.yaml` for the eventual Bluefin managed build.
- Pushed `feature/hantasim-full-build` to Gitea as the task PR target branch.
- Confirmed Bluefin does not currently have Gitea SSH access for
  `git@appliedsci.tail90eacc.ts.net:411`; cloning `hantasim-test` from Bluefin
  failed with `Permission denied (publickey)`.
- Full build was not launched.

The PlanContract intentionally uses Bluefin's intended local checkout path:

```text
/var/home/j/code/hantasim-test
```

Before production worktree execution on Bluefin, either configure Bluefin's
Gitea SSH key, use a token-based clone/push path, or provide a local checkout
with a push-capable remote.
