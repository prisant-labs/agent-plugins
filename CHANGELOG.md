# Changelog

Changes to the prisant-labs marketplace catalog: which plugins are listed, and what version each entry is pinned to.

This tracks the *catalog*, not the plugins. Each plugin keeps its own changelog in its own repository.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

## 2026-08-18

### Fixed

- Plugin `source` entries and the README install command switched from the GitHub `owner/repo` shorthand to explicit HTTPS git URLs. The shorthand form clones over SSH by default, which fails with "Permission denied (publickey)" on any machine without an SSH key registered for GitHub, even though every repo listed here is public. HTTPS needs no key.

### Changed

- Repinned `prisant-utilities` from `v0.1.1` to `v0.1.2`. A correctness release for the session pair:
  `plab-wrap-session` 1.4.1 and `plab-continue-session` 1.2.1. Both skills had listed status questions
  ("what did we do?", "where were we?") among their activation triggers, so asking for an answer could
  get you a procedure instead of an answer. Both now decline those and respond directly. Quick-mode and
  blocked-mode wraps also stop emitting session logs that the wrap skill's own self-check rejects. No
  format change: logs written by the previous versions read and parse identically, so nothing already
  written needs migrating. Existing installs pick this up on `/plugin update`.

## 2026-08-17

### Changed

- Repinned `prisant-utilities` from `v0.1.0` to `v0.1.1`.

### Added

- **`prisant-utilities`**, pinned to `v0.1.0`. Five agent skills for session continuity, structured analysis, guide authoring, and cross-LLM peer review, carrying the `plab-` prefix. Source is `github: prisant-labs/prisant-utilities` at the tag, not `main`, so consumers track releases rather than unreleased work.
- README row for the new entry.

## 2026-08-07

### Added

- Initial catalog with `nonfiction-studio`.
