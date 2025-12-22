# Layer3 Protocol

A project template for AI-assisted development with Claude.

## What is this?

Layer3 Protocol is a documentation scaffold that helps Claude understand your project and work with you effectively. It provides:

- **Onboarding flow** — Claude asks discovery questions before jumping in
- **Role separation** — Architect (planning) vs Builder (implementation)
- **Session commands** — `..architect`, `..builder`, `..go`, `..make`, etc.
- **Living documentation** — PRFAQ, TODO, PROGRESS, DECISIONS files that stay in sync

## Quick Start

### 1. Clone/Fork this repo

```bash
git clone https://github.com/[username]/layer3-protocol.git my-project
cd my-project
```

### 2. Open in Claude Code

When you open the project, Claude will see the `[PLACEHOLDER]` markers and run the onboarding flow automatically.

### 3. Answer discovery questions

Claude will ask:
1. What are we building?
2. Who is it for?
3. What problem does it solve?
4. What does MVP success look like?
5. Any constraints?

### 4. Review and confirm

Claude reflects back understanding. Confirm or correct.

### 5. Start building

Use the workflow commands:
- `..architect` — Enter planning mode
- `..builder` — Enter implementation mode
- `..go` — Execute top task
- `..end` — Close session

## File Structure

```
my-project/
├── CLAUDE.md           # Technical reference + onboarding flow
├── PRFAQ.md            # Product vision (Press Release / FAQ)
├── TODO.md             # Prioritized task list
├── PROGRESS.md         # Session-by-session development log
├── DECISIONS.md        # Architecture Decision Records
├── WORKFLOW.md         # Development process
├── ROLE_PROTOCOL.md    # AI workflow commands
└── README.md           # This file (replace with your own)
```

## Commands Reference

| Command | Mode | Purpose |
|---------|------|---------|
| `..architect` | — | Enter planning mode |
| `..builder` | — | Enter implementation mode |
| `..start` | Architect | Load context, show priorities |
| `..make` | Architect | Design a feature |
| `..go` | Builder | Execute top task |
| `..end` | Builder | Close session, update docs |
| `..hygiene` | Architect | Archive old content |
| `..exit` | Architect | Fossilize context |

## Philosophy

### Why separate Architect and Builder?

- **Architect** has full context (PRFAQ, DECISIONS, etc.) for big-picture thinking
- **Builder** has lean context (CLAUDE, TODO only) for focused execution
- Prevents scope creep during implementation
- Mirrors how humans work: plan first, then execute

### Why so many markdown files?

- Claude reads these automatically
- Version-controlled documentation
- Easy to review what changed and when
- Survives across sessions (Claude has no memory otherwise)

### Why the onboarding flow?

- Ensures Claude understands the project before acting
- Prevents "helpful" assumptions that miss the mark
- Creates documentation as a byproduct

## License

MIT — Use freely, modify as needed.

---

*Layer3 Protocol v1.0*
