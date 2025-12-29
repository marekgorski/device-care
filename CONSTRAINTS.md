# Constraints

Principles and conventions for Device Care.

---

## Core Principles

### Personal Wiki, Not Knowledge Base
> A personal collection of troubleshooting guides, not a public reference.

Guides are written for family members, not strangers. Assume context.

### GitHub as CMS
> Markdown files, folder structure, version control.

No database, no backend. Just browsable files on GitHub.

### Guides Over Manuals
> Focus on specific problems, not comprehensive documentation.

A guide answers "How do I pair my headphones?" not "Everything about headphones."

---

## Folder Hierarchy

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
5. **References** — Links to official docs if helpful

---

## Naming Conventions

| Element | Convention |
|---------|------------|
| Folders | lowercase, hyphens (`sony-wi-c310`) |
| Files | lowercase, hyphens (`pairing-iphone.md`) |
| Categories | plural nouns (`headphones`, `air-filters`) |

---

## Explicitly Rejected

| Approach | Why Rejected | Date |
|----------|--------------|------|
| Database | Overkill for personal wiki | Dec 2024 |
| GitHub Wiki | Less browsable than files | Dec 2024 |
| Static site generator | Adds build complexity | Dec 2024 |
| Public hosting | Family use only | Dec 2024 |

---

*Referenced by CLAUDE.md*
*Last updated: December 28, 2025*
