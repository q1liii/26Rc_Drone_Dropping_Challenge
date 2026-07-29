# Fast-Drone-250 / ws_livox Remote Repository Audit Plan

> **For Codex:** Execute this plan as a read-only audit of `ubuntu@192.168.0.183`; do not modify the remote host.

**Goal:** Build a complete, evidence-backed description of the two ROS workspaces, with special attention to `realflight_modules/px4ctrl`, mission scripts, localization/planning/control interfaces, and point-flight operation.

**Method:** Collect host and Git metadata over SSH, copy only source/configuration/document text files into a local temporary snapshot, derive a complete manifest, then trace ROS packages, launch files, topics, messages, parameters, executables, and mission data flow from source. Generated build products and large binary data are counted and classified but not copied.

**Deliverables:** A Chinese Markdown project guide under `docs/` plus a machine-readable file manifest under `docs/audit/`.

---

### Task 1: Establish the audit baseline

**Files:**
- Create: `tmp/remote_audit/ssh_collect.py`
- Create: `tmp/remote_audit/raw/host-baseline.txt`

**Steps:**
1. Verify SSH connectivity without exposing or persisting the password.
2. Record OS, ROS distribution, compiler/build tools, disk status, repository roots, Git branches, remotes, commits, submodules, and dirty state.
3. Confirm every remote command is read-only.

### Task 2: Build the complete repository inventory

**Files:**
- Create: `tmp/remote_audit/snapshot/Fast-Drone-250/`
- Create: `tmp/remote_audit/snapshot/ws_livox/`
- Create: `docs/audit/2026-07-29-remote-repo-file-manifest.tsv`

**Steps:**
1. Enumerate all paths, sizes, modes, and symlink targets under both workspace roots.
2. Classify generated directories, binaries, bags/logs, datasets, and source/configuration files.
3. Copy all relevant text/source/configuration files to the local snapshot and hash them.
4. Verify local manifest counts against the remote enumeration.

### Task 3: Trace ROS packages and runtime interfaces

**Files:**
- Inspect: `tmp/remote_audit/snapshot/Fast-Drone-250/src/realflight_modules/px4ctrl/**`
- Inspect: `tmp/remote_audit/snapshot/Fast-Drone-250/src/**`
- Inspect: `tmp/remote_audit/snapshot/ws_livox/src/**`

**Steps:**
1. Parse all `package.xml`, `CMakeLists.txt`, launch, YAML, message, service, Python, shell, and C/C++ files.
2. Extract nodes, executables, publishers, subscribers, services, actions, parameters, remaps, frames, and message types.
3. Reconstruct FAST-LIO2 → mapping/localization → EGO-Planner → `px4ctrl` → MAVROS/PX4 data flow.
4. Trace exact interfaces for position commands, hover/waypoint operation, takeoff/landing, and mission scripts.

### Task 4: Classify project ownership and competition capability

**Files:**
- Inspect: Git metadata, READMEs, licenses, commit logs, script comments, launch files, and configuration paths.

**Steps:**
1. Separate upstream/open-source modules, original competition/application scripts, integration glue, experiment/demo tools, calibration utilities, and generated artifacts.
2. Mark each conclusion as verified from code, derived from Git history, or inferred from integration context.
3. Map existing components to the 2026 mission needs and identify real gaps without claiming unimplemented behavior.

### Task 5: Write and verify the project guide

**Files:**
- Create: `docs/2026-07-29-Fast-Drone-250-ws_livox-现有项目完整说明.md`

**Steps:**
1. Document repository topology, package responsibilities, runtime startup order, interfaces, coordinate frames, point-flight procedures, mission scripts, tools, and competition reuse.
2. Include copy-pasteable commands only when confirmed by repository files or installed remote tools.
3. Cross-check every path/topic/message/parameter against the snapshot.
4. Scan for unresolved placeholders and verify all required sections and manifest statistics.
