# Resource Lifecycle Specification

> This document defines the lifecycle models used by resources within the Urban Observation Platform (UOP).

Resources within UOP do not all behave the same throughout their lifetime. Some resources represent immutable historical facts, while others evolve as understanding improves or as the physical world changes.

This specification defines the lifecycle categories available within the platform.

---

# Purpose

The purpose of this specification is to:

- Define common lifecycle behaviours.
- Ensure consistency across resource specifications.
- Clarify how resources evolve over time.
- Preserve historical integrity.
- Support interoperability between implementations.

Individual resource specifications shall reference one of the lifecycle models defined in this document.

---

# Lifecycle Categories

The UOP Specification defines three lifecycle categories.

| Lifecycle | Description |
|------------|-------------|
| Immutable | Never changes after creation |
| Persistent | May evolve while preserving identity |
| Versioned | Evolves by creating new versions |

Each API resource shall belong to exactly one lifecycle category.

---

# Immutable Resources

Immutable resources represent historical facts.

Once created they shall never change.

Corrections are represented by creating new resources rather than modifying existing ones.

Characteristics:

- Stable identity
- No updates
- No version history
- Permanent historical record

Example:

- Observation

---

# Persistent Resources

Persistent resources represent entities that continue to exist over time.

Their descriptive properties may change while their identity remains stable.

Characteristics:

- Stable identity
- Mutable properties
- No mandatory version history
- Represents a continuing entity

Examples:

- Place Object
- Relation

---

# Versioned Resources

Versioned resources represent evolving understanding.

Rather than modifying existing information, new versions are created.

Previous versions remain available.

Characteristics:

- Stable logical identity
- Multiple versions
- Historical traceability
- Explicit supersession

Examples:

- Knowledge
- Analysis
- Processor

---

# Lifecycle Transitions

Immutable resources

```
Create

↓

Store

↓

Reference
```

No further lifecycle transitions occur.

---

Persistent resources

```
Create

↓

Reference

↓

Update

↓

Archive (optional)
```

Updates preserve the identity of the resource.

---

Versioned resources

```
Create

↓

Publish

↓

Supersede

↓

Publish New Version

↓

Archive (optional)
```

Previous versions remain part of the historical record.

---

# Historical Integrity

The platform shall preserve historical integrity.

Implementations MUST NOT:

- modify immutable resources;
- delete historical versions without explicit policy;
- lose provenance information.

Historical traceability is a core design principle of UOP.

---

# Resource Identity

Lifecycle behaviour shall not affect resource identity.

Each resource maintains a stable identifier throughout its lifecycle.

Versioned resources additionally expose version identifiers.

---

# Conformance Requirements

Every conforming implementation:

MUST

- assign each resource to exactly one lifecycle category;
- preserve historical integrity;
- implement lifecycle behaviour consistently.

SHOULD

- expose lifecycle status where appropriate;
- preserve archived resources.

MAY

- implement additional operational states;
- define implementation-specific lifecycle workflows.

---

# Lifecycle Assignment

The core UOP resources currently use the following lifecycle models.

| Resource | Lifecycle |
|----------|-----------|
| Observation | Immutable |
| Place Object | Persistent |
| Relation | Persistent |
| Knowledge | Versioned |
| Analysis | Versioned |
| Processor | Versioned |

Future resource specifications shall explicitly declare which lifecycle model they implement.

---

# Relationship to Resource Specifications

This document defines lifecycle behaviour only.

Individual resource specifications define:

- Validation
- Properties
- Relationships
- Security
- Examples

Those specifications inherit lifecycle semantics from this document.

---

# Related Documents

- API_DESIGN_GUIDELINES.md
- COMMON_RESOURCE_SPECIFICATION.md
- RESOURCES.md
- resources/OBSERVATIONS.md
- resources/PLACE_OBJECTS.md
- resources/KNOWLEDGE.md
- resources/RELATIONS.md
- resources/ANALYSIS.md
- resources/PROCESSORS.md