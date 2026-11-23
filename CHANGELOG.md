# Changelog

All notable changes to **Sculpting Framework** are documented in this file. This project adheres to [Semantic Versioning](https://semver.org/).

## [1.0.1] - 2026-11-22

Refinements discovered during the first live end-to-end build using the installed `SKILL.md` plugin.

### Changed
- **`sculpting` & `sculpting-block`:** Clarified `manual`-mode SSoT storage (`docs/sculpt-<slug>.md` or in-thread) and git hygiene policy for `sculpting.context.md` in public/open-source repos.
- **`sculpting-rough-cut`:** Marked the Pre-Detail Spike (Template 5) gate explicitly as conditional *(if external/3rd-party or major technical unknowns exist; N/A for pure static/UI work)*.
- **`sculpting-detail`:** Added a solo-owner fast handoff rule — when there is a single technical owner (no parallel conflicts) and the sole decision maker already approved implementation in Rough Cut, post slices as an FYI and proceed straight to `sculpting-polish` without an extra blocking round.
- **`sculpting-polish`:** Marked live telemetry in the Done Gate as conditional *(if applicable — never violate privacy or no-tracker Red Lines)*.

## [1.0.0] - 2026-11-22

### Added
- Initial marketplace-ready release (`plugin.json`, `.claude-plugin/plugin.json`, `.claude-plugin/marketplace.json`).
- 5 portable `SKILL.md` skills: `sculpting`, `sculpting-block`, `sculpting-rough-cut`, `sculpting-detail`, `sculpting-polish`.
- Core framework specification (`docs/framework-v1.0.md`) and 7-simulation empirical validation log (`docs/simulations.md`).
- Brand icon and international English `README.md`.
