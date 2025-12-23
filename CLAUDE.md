# CLAUDE.md

## System Protocol

This project uses the **Layer3 workflow protocol** for AI-assisted development.

### Commands

| Command | Mode | Purpose |
|---------|------|---------|
| `..architect` | Planning | Design, strategy, architecture |
| `..builder` | Implementation | Write code, execute tasks |
| `..start` | Architect | Load context, show priorities |
| `..make` | Architect | Design a feature, write specs |
| `..go` | Builder | Execute top task from TODO |
| `..end` | Builder | Close session, update docs |
| `..hygiene` | Architect | Archive old content, prune files |
| `..exit` | Architect | Fossilize context for handoff |

See `ROLE_PROTOCOL.md` for full command specifications.

### Quick Rules

1. **Architect designs, Builder implements** — Don't mix roles
2. **Docs are source of truth** — Update TODO, PROGRESS, DECISIONS after changes
3. **Micro-commits** — Small, frequent commits with clear messages
4. **Context files stay lean** — Run `..hygiene` when files grow large

---

## Project Overview

**Project:** Device Care

**One-liner:** A personal wiki of device troubleshooting guides, organized as browsable markdown files on GitHub.

**Status:** Initialized

---

## Structure

```
device-care/
├── CLAUDE.md           # Technical reference (this file)
├── PRFAQ.md            # Product vision and FAQs
├── TODO.md             # Prioritized task list
├── PROGRESS.md         # Session-by-session log
├── DECISIONS.md        # Architecture Decision Records
├── WORKFLOW.md         # Development process
├── ROLE_PROTOCOL.md    # AI workflow commands
├── README.md           # User-facing documentation
└── devices/            # Device guides (the actual content)
    ├── audio/
    │   └── headphones/
    │       └── sony-wi-c310/
    │           └── pairing-iphone.md
    ├── hvac/
    └── ...
```

---

## Folder Hierarchy

The folder structure follows a Yahoo-directory style:

```
devices/{category}/{subcategory}/{brand-model}/{guide}.md
```

**Examples:**
- `devices/audio/headphones/sony-wi-c310/pairing-iphone.md`
- `devices/hvac/air-filters/ordering-replacements.md`
- `devices/lighting/smart-bulbs/philips-hue/setup.md`

---

## Guide Format

Each guide should include:

1. **Title** — What problem this solves
2. **Device info** — Model, brief description
3. **Steps** — Numbered, actionable steps
4. **Troubleshooting table** — Common issues and solutions (optional)
5. **References** — Links to official docs/videos if helpful

---

## Related Documentation

| File | Purpose |
|------|---------|
| `PRFAQ.md` | Product vision, press release, FAQs |
| `DECISIONS.md` | Architecture Decision Records |
| `TODO.md` | Prioritized task list |
| `PROGRESS.md` | Session-by-session development log |
| `WORKFLOW.md` | Development process and commit strategy |
| `ROLE_PROTOCOL.md` | AI workflow commands |
| `README.md` | User/setup documentation |

---

*Last updated: 2024-12-23*
*Status: Initialized*
