# Backlog

> The backlog captures work that is planned, proposed or under consideration for the Urban Observation Platform (UOP).

Unlike the architecture documentation, the backlog is expected to change frequently as the project evolves.

The backlog helps separate current implementation from future work.

---

# Purpose

The purpose of the backlog is to:

- Organise future work
- Capture ideas
- Prioritise implementation
- Record architectural considerations
- Support transparent planning

The backlog is a planning tool, not an architectural specification.

---

# Backlog Documents

## Product-Backlog.md

Contains planned work items, features and technical tasks.

The Product Backlog represents work that has been accepted for future implementation.

---

## RTM.md

The Requirements Traceability Matrix (RTM) links requirements to architectural decisions, implementation and verification.

It helps ensure that important requirements remain visible throughout the project's lifecycle.

---

## ARCHITECTURE_IDEAS.md

Captures architectural ideas that have **not yet been accepted**.

Recording ideas here prevents them from being forgotten while avoiding unnecessary changes to the current architecture.

Ideas recorded here should not influence implementation until they have been reviewed and accepted.

---

# Backlog Principles

The backlog follows a few simple principles.

- Record ideas early.
- Prioritise continuously.
- Avoid unnecessary detail.
- Keep accepted architecture separate from proposed ideas.
- Remove completed work from the active backlog.

---

# Relationship to Architecture

The architecture describes what the platform is.

The backlog describes what the platform may become.

Work should normally follow this progression.

```
Idea
    │
    ▼
Architecture Ideas
    │
    ▼
Architecture Decision (ADR)
    │
    ▼
Product Backlog
    │
    ▼
Implementation
```

This process helps maintain architectural consistency while allowing the project to evolve.

---

# Future Evolution

As UOP grows, the backlog may be expanded to include:

- Milestones
- Releases
- Epics
- Feature groups
- Technical debt
- Maintenance activities

The structure should remain simple and easy to understand.

---

# Related Documentation

- `../architecture/README.md`
- `../adr/README.md`
- `../philosophy/GOVERNANCE.md`
- `../ROADMAP.md`