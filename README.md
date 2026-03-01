# proven-origin

An [artifact origin](https://github.com/provenimpact/proven-skillsets-claude) for [proven](https://github.com/provenimpact/proven-skillsets-claude) — the artifact manager for AI coding assistants.

## Usage

```bash
proven origin add provenimpact/proven-origin
proven update
proven search skills
proven install proven-testskills
```

## Artifacts

| Artifact | Description |
|---|---|
| `proven-testskills` | 14 AI coding assistant skills (proven-needs, needs-*, ears-requirements, conventional-commits) |

## How releases work

When a new version of [proven-testskills](https://github.com/provenimpact/proven-testskills) is tagged and released, its release pipeline:

1. Builds a tarball of all skills
2. Computes the SHA256 checksum
3. Creates a GitHub Release with the tarball as an asset
4. Dispatches an `artifact-released` event to this repository

This repository's `update-definition` workflow receives that event and updates `artifacts/proven-testskills/definition.cue` with the new version URL and SHA256, then commits and pushes.

Users running `proven update` will pick up the new version automatically.
