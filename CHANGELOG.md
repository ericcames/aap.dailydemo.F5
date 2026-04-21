# Changelog

All notable changes to this project will be documented in this file.

## [Unreleased]

### Fixed
- (Issue #13) Correct credential name on `Day 2 - lb pool check` and `Day 2 - Linux Patching` templates (`Network F5` → `Daily Demo F5 Network`) — pending test environment validation
- (Issue #14) ✅ Consolidate 6 individual workflow files into single `controller_workflow_job_templates.yml` to prevent `include_vars: dir:` key overwrite — validated in dev: all 6 workflows confirmed created on setup

### Added
- (Issue #15) Post-setup validation play in `setup_demo.yml` — queries AAP API to assert all expected job templates and workflows exist before exiting
