# extension

Verified ATGV AIATECH Assist VSIX packages and SHA-256 checksums are available under [Releases](https://github.com/aidilazharo/extension/releases).

Published packages are mirrored from the verified source release after build checks pass.

ATGV extension update discovery uses this public distribution repository; the development source repository is not included in the release lookup list.

## Automated release sync

The `Publish public ATGV extension releases` GitHub Actions workflow copies the
newest **verified** VSIX and matching SHA-256 checksum from the private source
repository. It runs every 15 minutes and can also be started using
**Actions → Publish public ATGV extension releases → Run workflow**.

**One-time repository secret required:** In
`aidilazharo/extension` open **Settings → Secrets and variables → Actions →
New repository secret**, and add `ATGV_SOURCE_READ_TOKEN`.

Use a fine-grained GitHub token authorized only for the private
`aidilazharo/aiatech-assist` repository with **Contents: Read-only** permission
and access approved by the repository owner (if required). No workflow needs
a token hardcoded in source, bundled in the VSIX, or displayed in diagnostic
logs. The public repository's own GitHub Actions token already provides
**Contents: Write** for publishing.

Without the private source secret, GitHub returns HTTP 404 and release sync
stops safely. No older release is republished, and ATGV never downgrades an
installed extension because the mirror is behind.

## v0.0.0 release history reset

The Extension source component restarts at semantic version `0.0.0`. This repository is a public distribution mirror: legacy 0.4.x GitHub Releases and release tags are removed by a one-time, explicitly marked GitHub Actions cleanup. The mirror's own source history is retained. New v0.0.0 release assets are published only after their upstream checksums have been verified.

The source v0.0.1 verified build includes an empty VS Code description, 14 `.memory` JSON decision categories, strict 0.0.0–99.99.99 version increments and the single overwritten `RELEASE.md`.
