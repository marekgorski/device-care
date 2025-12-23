# DECISIONS.md - Architecture Decision Records

This file tracks architectural decisions for Device Care.

---

## Active Decisions

### ADR-001: Use folder hierarchy as navigation (Yahoo-style directory)

**Status:** Accepted
**Date:** 2024-12-23

**Context:**
Need a way to organize and find device guides without building a search system or web app.

**Decision:**
Use nested folders as the primary navigation mechanism. Browse down through categories to find specific guides.

**Alternatives Considered:**
- Flat folder with tags in frontmatter — requires tooling to search/filter
- Single README with table of contents — doesn't scale, hard to maintain
- Static site generator — adds build complexity for minimal benefit

**Consequences:**
- No build step or tooling required
- Works directly in GitHub's web UI
- Folder structure must be intuitive; reorganization means moving files
- Deep nesting could get unwieldy (mitigate by keeping hierarchy shallow)

---

### ADR-002: Markdown files for all content

**Status:** Accepted
**Date:** 2024-12-23

**Context:**
Need a format for device guides that's readable, editable, and portable.

**Decision:**
All guides are plain markdown (.md) files. GitHub renders them nicely, and they're easy to edit anywhere.

**Consequences:**
- Portable — can move to any platform
- Version controlled with git
- No lock-in
- Limited formatting (no interactive elements)

---

### ADR-003: Folder structure by device type, then brand, then model

**Status:** Accepted
**Date:** 2024-12-23

**Context:**
Need a consistent hierarchy for organizing devices.

**Decision:**
Structure: `devices/{category}/{subcategory}/{brand-model}/guide.md`

Example: `devices/audio/headphones/sony-wi-c310/pairing-iphone.md`

**Alternatives Considered:**
- By brand first — makes sense if you think in brands, but categories are more intuitive when troubleshooting
- By location (living room, kitchen) — devices move, categories don't

**Consequences:**
- Consistent mental model
- Easy to add new devices
- Some devices may not fit neatly (handle case-by-case)

---

## Template: New ADR

Copy this when adding decisions:

```markdown
### ADR-XXX: [DECISION_TITLE]

**Status:** Proposed | Accepted | Deprecated | Superseded
**Date:** [DATE]

**Context:**
[What situation prompted this decision?]

**Decision:**
[What did we decide?]

**Alternatives Considered:**
- [Option] — [why not chosen]

**Consequences:**
- [Positive or tradeoff]
```

---

*Last updated: 2024-12-23*
