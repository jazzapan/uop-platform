# Relations

> Relations describe explicit connections between domain objects within the Urban Observation Platform (UOP).

---

# Purpose

Relations provide a structured way to describe how domain objects are connected.

Rather than embedding references directly into multiple entities, relationships are represented explicitly to improve traceability, flexibility and future extensibility.

Relations enable the platform to document both direct and derived connections while preserving the integrity of the underlying data.

---

# Definition

A Relation is an explicit association between two or more domain objects.

Relations describe how objects are connected but do not change the objects themselves.

Every relation has:

- A source
- A target
- A relation type
- A creation timestamp
- Provenance information

---

# Why Relations Exist

The platform records information that evolves over time.

As knowledge grows, new relationships emerge between observations, place objects and derived knowledge.

Representing these connections as explicit relations provides:

- Traceability
- Flexibility
- Reproducibility
- Better analytical capabilities

---

# Relation Types

The following relation types are expected to exist within UOP.

## Observation → Place Object

Indicates that an observation documents a particular physical object.

Example:

```
Observation O-123
    documents
Place Object P-456
```

---

## Knowledge → Observation

Indicates that a knowledge object was derived from an observation.

Example:

```
Knowledge K-789
    derived_from
Observation O-123
```

---

## Knowledge → Place Object

Indicates that knowledge describes characteristics of a physical object.

Example:

```
Knowledge K-102
    describes
Place Object P-456
```

---

## Analysis → Observation

Indicates that an analysis includes one or more observations.

Example:

```
Analysis A-501
    includes
Observation O-123
```

---

## Analysis → Knowledge

Indicates that analytical results are based on one or more knowledge objects.

---

## Observation → Observation

Represents relationships between observations.

Examples include:

- Same event
- Same location
- Duplicate observation
- Follow-up observation
- Time sequence

---

## Knowledge → Knowledge

Knowledge objects may reference previous knowledge.

Examples include:

- Supersedes
- Refines
- Confirms
- Contradicts

---

# Relation Properties

Every relation should include:

- Identifier
- Relation type
- Source object
- Target object
- Creation timestamp
- Created by
- Confidence (optional)
- Notes (optional)

---

# Direction

Relations are directional.

Example:

```
Knowledge

derived_from

Observation
```

is different from

```
Observation

references

Knowledge
```

The direction shall always be explicitly defined.

---

# Cardinality

Relations may represent:

- One-to-one
- One-to-many
- Many-to-many

The domain model does not restrict cardinality.

Application rules may impose additional constraints where appropriate.

---

# Traceability

Relations are fully traceable.

For every relation it shall be possible to determine:

- When it was created
- Why it exists
- Which process created it
- Whether it has been reviewed
- Whether it is still considered valid

---

# Lifecycle

Relations follow a simple lifecycle.

```
Created
    │
    ▼
Validated
    │
    ▼
Active
    │
    ▼
Deprecated
    │
    ▼
Archived
```

Historical relations remain available even when no longer considered active.

---

# Validation

The platform shall ensure that:

- Source objects exist.
- Target objects exist.
- Relation types are valid.
- Circular references are avoided where inappropriate.

---

# Extensibility

New relation types may be introduced without modifying existing domain objects.

This supports future processors, analytical methods and extensions while maintaining a stable domain model.

---

# Domain Rules

The following rules apply.

- Relations are explicit.
- Relations never modify domain objects.
- Every relation has a defined type.
- Every relation has provenance.
- Every relation is traceable.

---

# Examples

## Example 1

An Observation documents an electrical cabinet.

A relation links the Observation to the corresponding Place Object.

---

## Example 2

OCR processing extracts text from an Observation.

A Knowledge object is created.

A relation records that the Knowledge was derived from the Observation.

---

## Example 3

A trend analysis identifies recurring observations.

The resulting Analysis object references all included Observations through explicit relations.

---

# Related Documents

- DOMAIN_MODEL.md
- OBSERVATION.md
- KNOWLEDGE.md
- PLACE_OBJECT.md
- ANALYSIS.md
- PROCESSORS.md
