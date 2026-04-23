# Codex Local Support Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Document how to run this MCP server locally with Codex on macOS without changing the server runtime.

**Architecture:** Keep the existing FastMCP server unchanged. Update repository documentation so the project is described as a generic MCP server, then add concrete Codex local configuration examples for both `uvx` and local checkout usage.

**Tech Stack:** Markdown, Codex MCP configuration, `uv`/`uvx`

---

### Task 1: Add a Codex local installation path to the README

**Files:**
- Modify: `README.md`

**Step 1: Update the project description**

Describe the server as working with MCP clients in general, instead of centering Claude only.

**Step 2: Add Codex local configuration examples**

Document:
- `codex mcp add` using `uvx things-mcp`
- `~/.codex/config.toml` using `command` + `args`
- local checkout usage with `uv run things-mcp`

**Step 3: Keep existing Claude instructions intact where still useful**

Do not remove Claude support. Reposition it as one supported client among others.

### Task 2: Verify the documentation changes

**Files:**
- Verify: `README.md`

**Step 1: Read the updated sections**

Check that the commands match Codex config syntax used locally in this environment.

**Step 2: Confirm scope stayed minimal**

Verify that no runtime code or unrelated docs were changed.
