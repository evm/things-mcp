# Things User Story Projects Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Replace workflow-phase headings in the user's live Things projects with one primary user-story heading per project.

**Architecture:** Use a replacement migration per project. Read the current Things state with `things-py`, create replacement projects through Things JSON import so each new project gets a user-story heading immediately, move existing tasks under that heading, then cancel the old projects.

**Tech Stack:** Python 3.12, `things-py`, local `things-mcp` helpers, Things JSON URL import, macOS `open`

---

### Task 1: Capture pre-migration state

**Files:**
- Modify: `/tmp/things_snapshot_before_user_story_migration.json`

**Step 1: Save current Things state**

Run:

```bash
uv run python - <<'PY'
import json
import things
from pathlib import Path

snapshot = {
    "projects": things.projects() or [],
    "todos": things.todos(include_items=True) or [],
    "headings": things.tasks(type="heading") or [],
}
Path("/tmp/things_snapshot_before_user_story_migration.json").write_text(
    json.dumps(snapshot, ensure_ascii=False, indent=2)
)
print("snapshot ready")
PY
```

Expected: `snapshot ready`

### Task 2: Define user-story mapping

**Files:**
- Modify: live migration script only

**Step 1: Write one primary user story per visible project**

Rules:

- one heading per project
- conservative wording
- derive from project title, notes, and tasks

**Step 2: Exclude temporary or superseded projects**

Do not migrate canceled or hidden predecessors; only the currently visible projects should survive the migration.

### Task 3: Migrate projects by replacement

**Files:**
- Modify: live Things data

**Step 1: For each project, create a replacement with one user-story heading**

Use Things JSON import so the heading exists at creation time.

**Step 2: Move all open tasks into the replacement project under the user-story heading**

Use `update_todo` with `list_id` and `heading_id`.

**Step 3: Cancel the old project and rename the replacement to the original title**

This preserves a clean project list.

### Task 4: Verify final structure

**Files:**
- Modify: `/tmp/things_snapshot_after_user_story_migration.json`

**Step 1: Save post-migration state**

Run a fresh snapshot.

**Step 2: Verify each visible project has exactly one heading**

Run a readback over all current projects and assert:

- one heading only
- heading text starts with `Als Ernst wil ik`

**Step 3: Verify no temporary project names remain**

Check that no names end with migration suffixes.
