# solid-like-a-rock Action

Lint your Swift architecture boundaries in CI — [solid-like-a-rock](https://github.com/nenadvulic/solid-like-a-rock)
enforces Clean Architecture / SOLID import rules on every pull request, with
inline annotations.

## Usage

```yaml
name: Architecture
on: [pull_request]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: nenadvulic/solid-like-a-rock-action@v1
        with:
          paths: Sources
          exclude: .build Pods
```

## Inputs

| Input | Default | Description |
|-------|---------|-------------|
| `version` | `latest` | solid-like-a-rock release to use (e.g. `0.6.0`). Linux binaries start at 0.6.0. |
| `paths` | `.` | Directories or files to lint (space-separated; individual paths must not contain spaces). |
| `config` | _(tool discovery)_ | Path to `.solid.yml`; by default the tool walks up from the working directory. |
| `baseline` | _(none)_ | Path to a baseline JSON; only new violations fail. |
| `exclude` | _(none)_ | Space-separated path fragments to skip (e.g. `.build Pods checkouts`); added to the config's own `exclude`. Fragments must not contain spaces. |

## Runners

Works on `ubuntu-latest`, `ubuntu-24.04-arm`, and `macos-*` runners. The
binary is downloaded from the release, checksum-verified, and cached.

## Versioning

Pin `@v1` to always get the latest compatible action. The action resolves the
latest `solid-like-a-rock` release at runtime, so `@v1` users automatically
pick up new tool versions — no action upgrade needed. To pin the tool itself,
set the `version` input. Each `solid-like-a-rock` release auto-publishes a new
`vX.Y.Z` action tag and advances the floating `v1` tag.
