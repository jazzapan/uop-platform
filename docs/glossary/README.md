# Glossary

> The glossary defines the common terminology used throughout the Urban Observation Platform (UOP).

A shared vocabulary is essential for maintaining a consistent understanding of the platform across documentation, implementation and discussions.

Whenever a term has a specific meaning within UOP, that meaning should be defined here.

---

# Purpose

The glossary exists to:

- Establish consistent terminology
- Reduce ambiguity
- Support contributors
- Improve readability
- Provide a common language for architecture and implementation

Definitions in the glossary should be considered authoritative unless explicitly superseded by an Architecture Decision Record (ADR).

---

# Glossary Documents

## Domain-Glossary.md

Defines the core concepts and terminology used throughout the Domain and Solution Architecture.

Examples include:

- Observation
- Knowledge
- Place Object
- Relation
- Analysis
- Processor

This document should be updated whenever new domain concepts are introduced.

---

# Principles

Glossary entries should:

- Be concise
- Be unambiguous
- Avoid implementation details
- Use terminology consistently throughout the documentation
- Reference related concepts where appropriate

The glossary describes concepts rather than implementation.

---

# Relationship to Other Documentation

The glossary supports every part of the documentation.

- Philosophy uses the glossary to describe guiding principles.
- Domain Architecture defines the concepts.
- Solution Architecture implements those concepts.
- ADRs explain architectural decisions affecting those concepts.

All documentation should use glossary terms consistently.

---

# Maintaining the Glossary

When introducing a new domain concept:

1. Determine whether an existing term already describes the concept.
2. If not, add a new glossary entry.
3. Update related documentation as needed.
4. Ensure terminology remains consistent throughout the repository.

The glossary should evolve together with the architecture.

---

# Related Documentation

- `../architecture/domain/README.md`
- `../architecture/solution/README.md`
- `../adr/README.md`