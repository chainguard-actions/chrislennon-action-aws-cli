<!-- markdownlint-disable -->

# Hardening Report: chrislennon--action-aws-cli/v1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **chrislennon--action-aws-cli/v1** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The workflow uses `actions/checkout@v1`, which is pinned to a mutable version tag rather than an immutable 40-character commit SHA. This means the action could be silently updated or replaced with a malicious version without any change to the workflow file, creating a supply-chain risk.

Locations:

- `.github/workflows/checkin.yml:13`

### missing-permissions (severity: medium)

The workflow file has no top-level `permissions:` key, and the single `build` job also has no job-level `permissions:` key. Without explicit permissions, the workflow inherits the default repository permissions (which may include write access to contents, packages, etc.), violating the principle of least privilege.

Locations:

- `.github/workflows/checkin.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed checkin.yml: (1) Pinned `actions/checkout@v1` to immutable SHA `50fbc622fc4ef5163becd7fab6573eac35f8462e` with `# v1` comment for readability. (2) Added top-level `permissions: contents: read` block to enforce least-privilege — the workflow only needs to read repository contents for checkout and build steps.

