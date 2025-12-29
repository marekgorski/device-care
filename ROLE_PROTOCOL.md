# Layer3 AI Workflow Protocol (v1.2)

## Changelog
- **v1.2** (Dec 28, 2025): Added task ownership markers, human/AI handoff system, acceptance criteria, verification steps, recovery levels
- **v1.0** (Dec 2024): Initial protocol

## Workflow Summary

| Workflow | Commands |
|----------|----------|
| **Design** | `..architect` → `..start` → `..make` → `..exit` |
| **Build** | `..builder` → `..go` → `..end` |
| **Maintenance** | `..architect` → `..hygiene` → `..exit` |
| **Recovery** | `..recover` (Any role) |

---

## Task Ownership Markers

Tasks in TODO.md use markers to indicate who can complete them:

| Marker | Meaning | Example |
|--------|---------|---------|
| `[C]` | Claude can complete | `[C] Create guide template` |
| `[M]` | Marek must complete | `[M] Test guide on device` |
| `[C→M]` | Claude prepares, Marek executes | `[C→M] Draft troubleshooting steps` |
| `[M→C]` | Marek decides, Claude implements | `[M→C] Provide filter part numbers` |

**No marker = `[C]`** — Tasks without markers are assumed Claude-completable.

### TODO.md Format with Markers

```markdown
## High Priority

- [ ] [C] Create guide template
  - AC: Template file exists
  - AC: Includes all standard sections

- [ ] [M] Gather HVAC filter info
  - AC: Filter sizes documented
  - Blocks: Filter guide creation
```

---

## MAREK.md Structure

Human-only tasks live in MAREK.md, organized by status:

```markdown
## ⏸️ Blocked (needs Marek action)
- [ ] [M] Gather HVAC filter info → blocks filter guide

## ✅ Ready for Marek (Claude prepared)
- [ ] [C→M] Draft guide ready → /devices/audio/...

## ❓ Waiting on Marek Decision
- [ ] [M→C] Which devices to document next?

## ✅ Completed
- [x] [M] Sony WI-C310 info — Dec 23, 2024
```

---

## Handoff Protocol

### Claude completing [C→M] task
1. Create deliverable (guide, template)
2. Move task to MAREK.md "Ready for Marek"
3. Note in PROGRESS.md

### Marek completing [M] task
1. Mark complete in MAREK.md with output (device info, test results)
2. Claude picks up on next `..go` and unblocks dependent work

### Marek making [M→C] decision
1. Add decision/info to MAREK.md "Completed"
2. Claude picks up and creates guide

---

## Role Definitions

### ..architect

**System Initialization:**
1. **Identity:** You are the ARCHITECT. Goal: System Design, Strategy, Planning.
2. **Context Scope:** FULL (PRFAQ, CONSTRAINTS, DECISIONS, CLAUDE, TODO, PROGRESS, MAREK).
3. **Allowed Commands:** `..start`, `..make`, `..hygiene`, `..exit`
4. **Forbidden:** Do NOT write implementation code.
5. **Acknowledge:** "🏗️ ARCHITECT MODE ACTIVE. Ready to plan. (~15% token budget loaded)"

### ..builder

**System Initialization:**
1. **Identity:** You are the BUILDER. Goal: Implementation & Execution.
2. **Context Scope:** LEAN (CLAUDE, TODO, MAREK only).
3. **Safety Check:** Run `git status`. If dirty: STOP.
4. **Allowed Commands:** `..go`, `..end`, `..recover`
5. **Forbidden:** Do NOT question architecture.
6. **Acknowledge:** "🔨 BUILDER MODE ACTIVE. Ready to build. (~5% token budget loaded)"

---

## Operational Commands

### ..start

**Session Bootloader (Architect Only)**

1. Read: PRFAQ, CONSTRAINTS, DECISIONS, CLAUDE, TODO, PROGRESS, MAREK.
2. Check MAREK.md for completed `[M]` tasks that unblock work.
3. Flag stale `[M]` tasks (>7 days).
4. Report top `[C]` task with acceptance criteria.

---

### ..make

**Design Protocol (Architect Only)**

1. User provides feature goal.
2. Review CONSTRAINTS.md and DECISIONS.md.
3. **Assign task ownership markers** to each task.
4. Write to files:
   - TODO.md: `[C]` tasks with AC
   - MAREK.md: `[M]` and info-gathering tasks
   - DECISIONS.md: ADR if needed

---

### ..go

**Implementation Protocol (Builder Only)**

1. Check MAREK.md for completed human tasks → unblock dependent work.
2. Run `git status` + `git pull` (context drift check).
3. Filter TODO.md to `[C]` tasks only.
4. Select top priority, display AC.
5. Implement with micro-commits.
6. If blocked on device info → add to MAREK.md, move to next `[C]` task.

---

### ..end

**Session Cleanup (Builder Only)**

1. **Verify AC met** for each task worked on.
2. Move `[C→M]` deliverables to MAREK.md "Ready for Marek".
3. Update TODO.md and PROGRESS.md.
4. `git push`
5. Suggest next `[C]` priority.

---

### ..hygiene

**Context Garbage Collection (Architect Only)**

1. Archive PROGRESS.md entries > 30 days.
2. Archive completed TODO items.
3. Archive completed MAREK.md items.
4. Report health status.

---

### ..recover

**Emergency Recovery Protocol (Any Role)**

**Level 1:** `git reset --hard [last-good-commit]`
**Level 2:** Delete local, `git pull origin main`

---

### ..exit

**Context Fossilization (Architect Only)**

1. Verify recent Builder work.
2. Review MAREK.md for stale tasks.
3. Audit documentation.
4. Output top `[C]` priority + top `[M]` priority.

---

## Context Loading Reference

| Role | Files Loaded | Token Budget |
|------|--------------|--------------|
| Architect | PRFAQ, CONSTRAINTS, DECISIONS, CLAUDE, TODO, PROGRESS, MAREK | ~15% |
| Builder | CLAUDE, TODO, MAREK | ~5% |

---

## Anti-Patterns Learned

| Anti-Pattern | Consequence | Prevention |
|--------------|-------------|------------|
| TODO without AC | "Done" but broken | `..make` requires AC |
| No task markers | Claude attempts `[M]` tasks | Use ownership markers |
| `[M]` without blocker note | Unclear what's waiting | Note "Blocks: X" |
| Skipping `..end` | Docs out of sync | Builder must run `..end` |

---

## Related Documentation

- **[MAREK.md](./MAREK.md)** — Human-only tasks
- **[WORKFLOW.md](./WORKFLOW.md)** — Commit strategy
- **[CONSTRAINTS.md](./CONSTRAINTS.md)** — Principles, rejected approaches
- **[DECISIONS.md](./DECISIONS.md)** — Active ADRs
- **[CLAUDE.md](./CLAUDE.md)** — Technical reference

---

*Layer3 Protocol v1.2 — December 28, 2025*
