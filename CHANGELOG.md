# Changelog

Changes to the prisant-labs marketplace catalog: which plugins are listed, and what version each entry is pinned to.

This tracks the *catalog*, not the plugins. Each plugin keeps its own changelog in its own repository.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

## 2026-08-26

### Changed

- **Marketplace renamed from `agent-plugins` to `prisant-labs`.** The manifest registered itself
  after its repository, while the sibling `product-on-purpose` marketplace in an identically-named
  repository registers after its organisation. A marketplace is keyed by its manifest name, so the
  two displayed inconsistently and this one's install target read `@agent-plugins`.

  The repository slug is unchanged, so `/plugin marketplace add prisant-labs/agent-plugins` still
  reads the same. Only the install target moves, to `/plugin install <plugin>@prisant-labs`.

  **This is an identity change, not a display change.** An install registered under the old name
  must be removed and reinstalled; it does not migrate on update.

- Repinned `prisant-utilities` from `v0.4.2` to `v0.4.3`, which carries the matching install-line
  corrections across its README and eight skill usage docs, plus a new `docs/status-skills.md`.

## 2026-08-25 (CI only)

### Changed

- Repinned `prisant-utilities` from `v0.4.1` to `v0.4.2`. CI moved its SARIF upload to
  codeql-action v4; the v3 action targets Node 20 and its line deprecates in December 2026. No skill
  or plugin surface change, so nothing about installing or using the plugin differs.

## 2026-08-25 (later)

### Changed

- Repinned `prisant-utilities` from `v0.4.0` to `v0.4.1`. Session-log body prose is no longer
  hard-wrapped, which matters most for the continuation prompt: it is meant to be pasted into a chat
  box, and hard wraps arrived ragged. It also restores grep, since a search for any phrase longer
  than the wrap width had been failing silently.

## 2026-08-25

### Changed

- Repinned `prisant-utilities` from `v0.3.0` to `v0.4.0`, the "gates that cannot fail open" release.
  Both `plab-wrap-session` self-check detectors are now committed, canary-verified scripts that
  report clean, findings, or broken, and refuse to report clean when they cannot prove they still
  work. The path-citation gate also stopped flagging prose: measured on a real log it went from 6
  false positives out of 7 flags to 2 out of 4.
- Also in this pin: the session-log format gained a `(blocked since YYYY-MM-DD)` contract on Waiting
  on You items with carry-forward across wraps, same-arc log supersession, and capture-lite
  consumption. `plab-wrap-session` 1.6.0, `plab-continue-session` 1.4.0.

## 2026-08-24

### Changed

- Repinned `prisant-utilities` from `v0.2.0` to `v0.3.0`. Three skills migrated in from a private
  library and are now installable: `plab-spec` 1.2.1 writes a feature specification with numbered
  acceptance criteria each cited to a source, `plab-release-plan` 1.3.0 scopes a release and gates
  the tag on hygiene checks plus a doc-update checklist, and `plab-init-project` 1.3.0 scaffolds
  agent infrastructure into a repository. Five skills becomes eight.
- All three ship with `disable-model-invocation: true`, so they never fire on their own. Type
  `/plab-spec`, `/plab-release-plan` or `/plab-init-project`. Their trigger phrases ("spec", "init",
  "set up project", "plan the release") are ordinary words in conversation about a repository, and
  all three write files into one.
- The catalog description for the entry now covers specification and release planning, which the
  previous four-area wording did not.

## 2026-08-18

### Fixed

- Plugin `source` entries and the README install command switched from the GitHub `owner/repo` shorthand to explicit HTTPS git URLs. The shorthand form clones over SSH by default, which fails with "Permission denied (publickey)" on any machine without an SSH key registered for GitHub, even though every repo listed here is public. HTTPS needs no key.

### Changed

- Repinned `prisant-utilities` from `v0.1.2` to `v0.2.0`. Session logs can now be archived by month:
  `/plab-wrap-session --organize` files logs from closed months into `YYYY-MM/` subfolders, keeping the
  current and previous month flat. Nothing moves without confirmation and nothing is ever deleted.
  Deep and final wraps also raise it on their own, so the command does not have to be remembered.
  `/plab-continue-session` reads the flat store and the month folders as one set ordered by filename,
  so resuming is unaffected before, during, or after archiving. Skills: `plab-wrap-session` 1.5.0 and
  `plab-continue-session` 1.3.0. Both ship together because the reader has to understand month folders
  before anything is filed into one. No format change: existing logs need no migration. Existing
  installs pick this up on `/plugin update`.
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
