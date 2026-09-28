# Changelog

## v0.1.0 (2026-09-28)

First release, after the Miri `target/` environment disclosure
([advisory](https://blog.rust-lang.org/2026/09/21/github-actions-leaking-secrets-when-miri-output-is-cached/)).

- R1 `secret-in-job-env` (high): a secret in workflow-level or job-level
  `env:` of a PR-reachable workflow.
- R2 `pr-cache-save` (low; medium under `pull_request_target`): a PR run
  can write the cache.
- R3 `cargo-with-secret-in-scope` (high): a step runs `cargo` with a secret
  in scope, under any trigger. `cargo publish` with only a registry token
  in its own `env:` is exempt.
- R4 `miri-with-cache` (high): `cargo miri` and a cache step in the same
  workflow.
- GitHub annotations, a step-summary table, `--format json`; exit 0/1/2;
  `--min-severity` and `--no-fail` (`fail: "false"` in the action).
