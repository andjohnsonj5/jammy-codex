# jammy-codex

This repository automates building the Codex binaries for Ubuntu 22.04 (glibc) whenever a new stable Codex release is published. A GitHub Actions workflow runs on a schedule or manual dispatch to:

- Detect the latest Codex release from `openai/codex` that is not marked as a prerelease and whose tag does not contain `alpha` or `beta`.
- Skip work if the release is already published in this repository.
- Clone the upstream source at that tag, build on `ubuntu-22.04` (GNU toolchain), package the binaries, and attach them to a release in this repository using the same tag.

The main workflow lives at `.github/workflows/release.yml`. Trigger it with “Run workflow” in the Actions tab to force a fresh build, or let the schedule pick up new upstream releases automatically.
