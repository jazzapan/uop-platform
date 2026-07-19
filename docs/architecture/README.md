# Architecture

> This section describes the architecture of the Urban Observation Platform (UOP).

The architecture is intentionally divided into two complementary perspectives:

- **Domain Architecture** — what the platform is.
- **Solution Architecture** — how the platform is realised.

Keeping these perspectives separate allows the domain model to remain stable even as implementation technologies evolve.

---

# Architecture Overview

```
Architecture
│
├── Domain Architecture
│       │
│       ├── Observation
│       ├── Knowledge
│       ├── Place Object
│       ├── Relations
│       ├── Analysis
│       └── Processors
│
└── Solution Architecture
        │
        ├── Components
        ├── Data Flow
        ├── Storage
        ├── Security
        └── Deployment
```

The Domain Architecture defines the concepts that make up UOP.

The Solution Architecture defines the software structure that implements those concepts.

---

# Domain Architecture

The Domain Architecture is independent of programming language, database technology and deployment model.

Its purpose is to define:

- Core domain objects
- Relationships
- Responsibilities
- Domain rules
- Processing concepts

These concepts should remain stable over time.

See:

```
domain/
```

---

# Solution Architecture

The Solution Architecture describes the logical software architecture of the platform.

Topics include:

- Reference Architecture
- Components
- Data Flow
- Storage
- Security
- Deployment

Implementation technologies may evolve while preserving the overall architectural structure.

See:

```
solution/
```

---

# Architectural Principles

The architecture is guided by several fundamental principles.

- Observations are immutable.
- Knowledge is versioned.
- Relationships are explicit.
- Processing is independent.
- Architecture is modular.
- Components have clear responsibilities.
- Significant decisions are documented through ADRs.

These principles are explained in the Project Philosophy and Architecture Decision Records.

---

# Related Documentation

For architectural rationale:

```
../adr/
```

For project principles:

```
../philosophy/
```

For terminology:

```
../glossary/
```

---

# Reading Order

New contributors are encouraged to read the architecture documentation in the following order:

1. DOMAIN_MODEL.md
2. Domain Architecture documents
3. REFERENCE_ARCHITECTURE.md
4. Solution Architecture documents
5. Architecture Decision Records (ADR)

Following this sequence provides a gradual understanding of both the conceptual and technical design of UOP.