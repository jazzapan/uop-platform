# Repository Structure

> This document describes the organisation of the Urban Observation Platform (UOP) repository.

The repository is organised to separate architecture, implementation and project governance while remaining easy to navigate.

---

# Design Principles

The repository structure follows a few simple principles.

- Documentation before implementation.
- Clear separation of concerns.
- Stable directory structure.
- Predictable locations.
- Incremental growth.

The structure should remain understandable as the project evolves.

---

# Top-Level Structure

```
/
├── docs/
├── src/                 (future)
├── tests/               (future)
├── tools/               (future)
├── README.md
├── CHANGELOG.md
├── CONTRIBUTING.md
├── ROADMAP.md
├── SECURITY.md
└── LICENSE
```

---

# Documentation Structure

```
docs/
├── adr/
├── architecture/
│   ├── domain/
│   └── solution/
├── backlog/
├── glossary/
├── philosophy/
├── api/             (future)
├── development/     (future)
└── operations/      (future)
```

---

# Repository Evolution

The repository is expected to evolve in stages.

## Current

Architecture-first documentation.

## Next

Implementation specifications.

Examples include:

- API documentation
- Data model
- OpenAPI
- Development guides

## Later

Reference implementation.

Examples include:

- Source code
- Tests
- Build scripts
- Deployment automation

---

# Directory Responsibilities

## docs/

Architecture and project documentation.

---

## src/

Application source code.

Not yet introduced.

---

## tests/

Automated tests.

Not yet introduced.

---

## tools/

Development utilities and scripts.

Not yet introduced.

---

# Repository Principles

The repository should remain:

- Well organised
- Easy to navigate
- Easy to contribute to
- Independent of specific technologies
- Consistent with the documented architecture

---

# Related Documentation

- README.md
- docs/README.md
- docs/architecture/README.md
- docs/philosophy/README.md