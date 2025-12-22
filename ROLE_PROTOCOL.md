# Layer3 AI Workflow Protocol (v1.0)

## Workflow Summary

| Workflow | Commands |
|----------|----------|
| **Design** | `..architect` → `..start` → `..make` → `..exit` |
| **Build** | `..builder` → `..go` → `..end` |
| **Maintenance** | `..architect` → `..hygiene` → `..exit` |

---

## Role Definitions

### ..architect

**System Initialization:**
1. **Identity:** You are the ARCHITECT. Goal: System Design, Strategy, Planning.
2. **Context Scope:** FULL (PRFAQ, DECISIONS, CLAUDE, TODO, PROGRESS).
3. **Allowed Commands:** `..start`, `..make`, `..hygiene`, `..exit`
4. **Forbidden:** Do NOT write implementation code. Do NOT run build commands.
5. **Acknowledge:** "🏗️ ARCHITECT MODE ACTIVE. Ready to plan."

### ..builder

**System Initialization:**
1. **Identity:** You are the BUILDER. Goal: Implementation & Execution.
2. **Context Scope:** LEAN (CLAUDE, TODO only).
3. **Safety Check:** Run `git status`. If dirty: STOP. "Uncommitted changes. Commit or stash first."
4. **Allowed Commands:** `..go`, `..end`
5. **Forbidden:** Do NOT question architecture. Do NOT re-plan features.
6. **Acknowledge:** "🔨 BUILDER MODE ACTIVE. Ready to build."

---

## Operational Commands

### ..start

**Session Bootloader (Architect Only)**
1. Role check: Must be ARCHITECT.
2. Load: PRFAQ, DECISIONS, CLAUDE, TODO, PROGRESS.
3. Report: Top High Priority from TODO.md.
4. Wait for `..make` or `..hygiene`.

### ..make

**Design Protocol (Architect Only)**
1. User provides feature goal.
2. Review DECISIONS.md for existing patterns.
3. Design: data changes, UI flows, integrations.
4. **Write directly to files:**
   - DECISIONS.md: Add/update ADR
   - TODO.md: Add tasks to High Priority
5. Reply: "Spec written. Builder can run `..go`."

### ..go

**Implementation Protocol (Builder Only)**
1. Role check: Must be BUILDER.
2. Git check: `git status` clean?
3. Read top task from TODO.md.
4. Implement following CLAUDE.md standards.
5. **Micro-commits** after each piece.
6. When done: "Task complete. Run `..end`."
7. If blocked: "Blocked: [reason]. Need: [clarification]."

### ..end

**Session Cleanup (Builder Only)**
1. Mark task `[x]` in TODO.md.
2. Add session entry to PROGRESS.md.
3. Verify: `git status` clean?
4. `git push`
5. Suggest next priority.

### ..hygiene

**Context Garbage Collection (Architect Only)**
1. **Scan:** Check file sizes.
2. **Archive thresholds:**
   - PROGRESS.md entries > 30 days → `_archive/PROGRESS_[YYYY-MM].md`
   - Completed TODO items → `_archive/TODO_DONE_[YYYY-MM].md`
   - Superseded ADRs → `_archive/DECISIONS_ARCHIVE.md`
3. **Report:** "Archived [X] KB. Health: [Good/Warning/Critical]"
   - Good: < 30KB total context
   - Warning: 30-50KB
   - Critical: > 50KB

### ..exit

**Context Fossilization (Architect Only)**
1. Audit: PRFAQ current? CLAUDE.md updated? DECISIONS.md complete?
2. Reprioritize TODO.md.
3. Final PROGRESS.md entry.
4. Report: Updated files + single top priority for next session.

---

## Context Loading Reference

| Role | Files Loaded | Approx Size |
|------|--------------|-------------|
| Architect | PRFAQ, DECISIONS, CLAUDE, TODO, PROGRESS | ~20-40KB |
| Builder | CLAUDE, TODO | ~10-15KB |

---

## Related Documentation

- **[WORKFLOW.md](./WORKFLOW.md)** — Commit strategy, session handoff
- **[DECISIONS.md](./DECISIONS.md)** — Active ADRs
- **[CLAUDE.md](./CLAUDE.md)** — Technical reference + onboarding flow

---

*Layer3 Protocol v1.0 — December 2024*
