# Changelog

All notable changes to this preset are documented here. The format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/). The preset has no releases:
Renovate reads it from `main`. Changes of the common rules are listed in
[grigoriev/renovate-config](https://github.com/grigoriev/renovate-config/blob/main/CHANGELOG.md).

## [Unreleased]

### Added
- Renovate never updates `java-jdk` in the workflows. Moving the JDK is a decision, not an
  automatic update. The Java repositories no longer need their own rule.
- OpenSSF Scorecard workflow and badge, CONTRIBUTING.md and this changelog.

### Changed
- CI cancels an older run of the same pull request, and every job has a timeout.
