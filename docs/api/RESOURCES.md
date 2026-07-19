# API Resources

> This document provides an overview of the primary resources exposed by the Urban Observation Platform (UOP) API.

The API is resource-oriented. Each resource represents a domain concept rather than an implementation detail.

Individual resource specifications build upon the concepts described in this document.

---

# Purpose

The purpose of this document is to:

- Define the primary API resources.
- Describe how resources relate to one another.
- Establish common resource lifecycle concepts.
- Provide a consistent foundation for future resource specifications.

---

# Resource Principles

Every API resource shall:

- Represent a domain concept.
- Have a stable identifier.
- Be independently addressable.
- Expose a well-defined representation.
- Support predictable operations.
- Remain independent of internal storage mechanisms.

Resources should not expose implementation details.

---

# Resource Overview

The UOP API is centred around six primary resources.

```
Observation
      │
      ▼
Knowledge
      │
      ▼
Analysis

Observation
      │
      ▼
Place Object

Observation
      │
      ▼
Relation

Observation
      │
      ▼
Processor
```

These relationships are conceptual and do not imply ownership.

---

# Observation

An Observation represents something that was recorded in the physical environment.

Observations are immutable.

Typical contents include:

- Metadata
- Time of observation
- Location
- Media references
- Collector information

Observations form the foundation of the platform.

---

# Knowledge

Knowledge represents information derived from one or more observations.

Knowledge is versioned and may evolve as:

- Processing algorithms improve.
- Human interpretation changes.
- Additional observations become available.

Knowledge never replaces the original observations.

---

# Place Object

A Place Object represents a physical entity in the observed environment.

Examples include:

- Buildings
- Walls
- Bridges
- Signs
- Utility cabinets

Multiple observations may reference the same Place Object.

---

# Relation

Relations describe explicit connections between resources.

Examples include:

- Observation references Place Object.
- Knowledge derived from Observation.
- Observation linked to another Observation.
- Analysis derived from Knowledge.

Relations improve traceability while keeping resources independent.

---

# Analysis

Analysis represents higher-level insights produced from observations and knowledge.

Examples include:

- Trends
- Statistics
- Spatial analysis
- Temporal analysis

Analysis does not modify source resources.

---

# Processor

A Processor represents the origin of derived information.

Processors may include:

- OCR
- Image classification
- Object detection
- Human review
- Future AI-based analysis

Processor metadata supports traceability and reproducibility.

---

# Resource Relationships

Resources are connected through explicit references.

```
Observation
     │
     ├────────► Place Object
     │
     ├────────► Knowledge
     │               │
     │               ▼
     │          Analysis
     │
     └────────► Relations
```

This separation keeps the API modular and extensible.

---

# Resource Lifecycle

Although each resource has its own lifecycle, the general pattern is:

```
Create

↓

Retrieve

↓

Reference

↓

Archive (optional)
```

Some resources may support additional lifecycle operations.

Observations remain immutable after creation.

Knowledge evolves through versioning.

---

# Resource Specifications

Each primary resource will have its own specification describing:

- Purpose
- Representation
- Operations
- Relationships
- Validation rules
- Permissions
- Examples

These specifications define the normative API contract for each resource.

---

# Related Documents

- API_DESIGN_GUIDELINES.md
- VERSIONING.md
- ../architecture/domain/DOMAIN_MODEL.md
- ../architecture/domain/OBSERVATION.md
- ../architecture/domain/KNOWLEDGE.md
- ../architecture/domain/PLACE_OBJECT.md
- ../architecture/domain/RELATIONS.md
- ../architecture/domain/ANALYSIS.md
- ../architecture/domain/PROCESSORS.md