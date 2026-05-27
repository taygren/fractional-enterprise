[claude-code.md](https://github.com/user-attachments/files/28306296/claude-code.md)
# Platform Profile: Claude Code

**Provider:** Anthropic  
**Interface:** Terminal / CLI (claude command), IDE integrations  
**Distinct from:** Claude.ai chat — different interface, context format, and capability set

---

## Strengths
- Terminal-native agentic coding — reads, writes, and executes files directly
- Repo-level understanding — can traverse entire codebases autonomously
- Multi-file changes in a single session without copy-paste
- Git-aware — understands diffs, branches, commit history
- Runs shell commands, installs packages, executes tests
- No copy-paste loop — changes happen in the actual codebase
- Strong for refactoring, debugging, and test generation at scale
- Ideal for CI/CD pipeline work and DevOps tasks

## Weaknesses
- Terminal-only interface — no GUI, no visual canvas
- Requires local setup and API key configuration
- Less suited for exploratory conversation and analysis
- Not ideal for document production or non-code deliverables
- Context is file/repo-scoped — external research requires separate tools

## Context Window
- Inherits Claude's 200K token context
- Loads files from the repo into context automatically as needed
- Context is repo-anchored, not conversation-anchored

## Memory & Persistence
- **CLAUDE.md:** Project-level instructions file read automatically at session start
- **No cross-session memory** by default — CLAUDE.md is the persistence layer
- **Handoff note:** Always include a CLAUDE.md update as part of any handoff to Claude Code — this is how context persists

## System Prompt Support
- ✅ Via CLAUDE.md in the project root (read automatically)
- ✅ Via `--system-prompt` flag at CLI invocation
- CLAUDE.md is the primary configuration surface for ongoing projects

## Tool Availability
- Full filesystem read/write access (within project scope)
- Shell command execution
- Git operations
- Package manager access (npm, pip, etc.)
- Web search (when enabled via MCP)
- MCP server integrations

## Prompt Format Conventions
- Task prompts should be specific and file-referenced where possible
- Reference specific files, functions, or line numbers rather than describing them
- Include acceptance criteria — what does "done" look like?
- CLAUDE.md should contain: project overview, stack, conventions, what not to touch
- Avoid narrative context — Claude Code needs specs, not stories

## Ideal Task Types
- Multi-file refactoring
- Codebase-aware debugging (where the bug might be anywhere)
- Test suite generation
- Automated documentation generation
- CI/CD pipeline configuration
- Infrastructure as Code (Terraform, Kubernetes, Dockerfiles)
- Dependency updates across a large repo
- Any task that requires reading from and writing to actual files

---

## Handoff Receiving Template

```
=== CLAUDE CODE HANDOFF PACKAGE ===
Project: [name]
Handed off from: [platform] ([phase])
Receiving: Claude Code ([phase])

# CLAUDE.md UPDATE
[Paste this content into CLAUDE.md in your project root before starting]

## Project
[2-sentence description of what this codebase is]

## Stack
[Language, framework, key dependencies]

## Current Task
[What Claude Code is being asked to do in this session]

## Conventions
[Naming conventions, file structure rules, patterns to follow]

## Do Not Touch
[Files, directories, or patterns that must not be modified]

## Acceptance Criteria
[What "done" looks like for this task]

# TASK PROMPT
[Paste this into the Claude Code terminal after updating CLAUDE.md]

You are continuing work on [project]. The following has been completed:
[Bullet list of what exists]

Your task:
1. [First specific action — reference file paths]
2. [Second action]
3. [Third action]

Constraints:
- [Hard constraint 1]
- [Hard constraint 2]

When complete, output a summary of:
- Files changed
- Decisions made
- Any blockers or unresolved questions
This summary will be used to hand back to [origin platform].

=== END ===
```

## Configuration Checklist
- [ ] CLAUDE.md exists in project root and is updated with current task context
- [ ] Claude Code is initialized in the correct project directory (`claude` from project root)
- [ ] API key is configured (`ANTHROPIC_API_KEY` set)
- [ ] Git status is clean or stashed before starting (makes diffs readable)
- [ ] Acceptance criteria are defined before starting — Claude Code works best with clear done-states
