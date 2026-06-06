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
```

## Inputs

| Input | Default | Description |
|-------|---------|-------------|
| `version` | `latest` | solid-like-a-rock release to use (e.g. `0.6.0`). Linux binaries start at 0.6.0. |
| `paths` | `.` | Directories or files to lint. |
| `config` | _(tool discovery)_ | Path to `.solid.yml`; by default the tool walks up from the working directory. |
| `baseline` | _(none)_ | Path to a baseline JSON; only new violations fail. |

## Runners

Works on `ubuntu-latest`, `ubuntu-24.04-arm`, and `macos-*` runners. The
binary is downloaded from the release, checksum-verified, and cached.
