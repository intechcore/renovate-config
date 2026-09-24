# renovate-config

[![CI](https://github.com/intechcore/renovate-config/actions/workflows/ci.yml/badge.svg)](https://github.com/intechcore/renovate-config/actions/workflows/ci.yml)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/intechcore/renovate-config/badge)](https://scorecard.dev/viewer/?uri=github.com/intechcore/renovate-config)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

Shared [Renovate](https://docs.renovatebot.com/) preset for the public repositories under
[intechcore](https://github.com/intechcore).

## Usage

Put this in the `renovate.json` of a repository:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>intechcore/renovate-config"]
}
```

Add only the rules that belong to that repository below `extends`: its own custom
managers, versioning, groups, `lockFileMaintenance`. A repository setting overrides the
preset. Do not repeat a preset setting in a repository.

## What the preset does

It extends [grigoriev/renovate-config](https://github.com/grigoriev/renovate-config), the
one source of the common rules for both owners. Its README lists what they do:
automerge through pull requests, digest pins, the dependency dashboard, OSV alerts,
Conventional Commit titles without a scope, one group for GitHub Actions, the workflow and
Makefile managers, and the zizmor rules.

Rules that apply to intechcore only go into `default.json` here, after the `extends`:

| Rule | Effect |
|---|---|
| `java-jdk` disabled | Renovate never moves the JDK of the workflows. The JDK follows `maven.compiler.release` and the Java runtime of Polarion; moving it is a decision, not an automatic update |

Both preset repositories are public. Renovate fetches a public preset from GitHub without
extra access, so the Mend Renovate app of this organization can read the grigoriev one.

## Changes

A change here reaches every repository that extends the preset on its next Renovate run.

1. Open a pull request. CI runs `renovate-config-validator --strict` on the preset.
2. Before the merge, run a local dry run in one affected repository:

   ```sh
   docker run --rm -v "$PWD":/repo -w /repo -e RENOVATE_PLATFORM=local \
     -e RENOVATE_DRY_RUN=lookup -e LOG_LEVEL=debug -e GITHUB_COM_TOKEN="$(gh auth token)" \
     renovate/renovate
   ```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Report vulnerabilities privately, see
[SECURITY.md](SECURITY.md).

## Disclaimer

This preset is provided "as is", without warranty of any kind, as the [LICENSE](LICENSE)
states. Use it at your own risk. Intechcore GmbH is not liable for damage from its use, as
far as the law allows. It is published free of charge, outside of any commercial offering,
with no obligation to support it. Security reports are welcome, see
[SECURITY.md](SECURITY.md).

## License

MIT, see [LICENSE](LICENSE).
