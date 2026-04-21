# Changelog

All notable changes to this project will be documented in this file.

## [Unreleased]

### Fixed
- (Issue #13) Correct credential name on `Day 2 - lb pool check` and `Day 2 - Linux Patching` templates (`Network F5` → `Daily Demo F5 Network`) — pending test environment validation
- (Issue #14) ✅ Consolidate 6 individual workflow files into single `controller_workflow_job_templates.yml` to prevent `include_vars: dir:` key overwrite — validated in dev: all 6 workflows confirmed created on setup
- (Issue #18) Add `job_tags: create` to `Daily Demo F5 Create/Remove` node in `Run workflow for the f5 Daily Demo` — prevents both create and remove tags running simultaneously, which caused subnet lookup failure during VM provisioning
- (Issue #21) Add `my_remote_vault`, `my_remote_ssh_pub_key`, and `ansible_python_interpreter` extra vars to `Daily Demo F5 website` template — role `remote_vault` requires `my_remote_vault` to fetch vaulted variables
- (Issue #23) Add `{{ my_vault }}` to `Daily Demo F5 website` credentials — vault credential required to decrypt the remote vault file (`my_aap_credential` is a controller credential, not a vault credential)

### Added
- (Issue #15) Post-setup validation play in `setup_demo.yml` — queries AAP API to assert all expected job templates and workflows exist before exiting
