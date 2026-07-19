# Place Object

> A Place Object represents a persistent physical object that can be observed over time.

---

# Purpose

A Place Object represents a physical object or structure in the environment that may be associated with one or more observations.

Unlike an Observation, which captures a moment in time, a Place Object exists independently of any single observation and may be observed repeatedly over an extended period.

The purpose of the Place Object is to provide continuity between observations that refer to the same physical object.

---

# Definition

A Place Object is a uniquely identifiable physical object that exists in the real world.

Examples include:

- Electrical cabinet
- Utility box
- Building facade
- Tunnel entrance
- Bridge
- Fence
- Retaining wall
- Traffic sign
- Bus shelter
- Railway infrastructure

The list is not exhaustive.

The platform shall support additional object types without requiring architectural changes.

---

# Characteristics

A Place Object is:

- Persistent
- Identifiable
- Observable
- Independent of observations
- Referenced by observations

A Place Object is not created because an observation exists.

It exists regardless of whether it has ever been documented.

---

# Identification

Every Place Object shall have a globally unique identifier.

The identifier remains stable throughout the lifetime of the object.

---

# Classification

A Place Object may be classified according to its physical characteristics.

Examples include:

- Utility infrastructure
- Transport infrastructure
- Building
- Public furniture
- Natural object
- Other

The classification model shall remain extensible.

---

# Attributes

A Place Object may contain:

- Identifier
- Type
- Name (optional)
- Description (optional)
- Geographic position
- Geometry (optional)
- Creation date (optional)
- Status

The platform shall allow additional attributes to be introduced without affecting existing observations.

---

# Geographic Representation

A Place Object may be represented by:

- A point
- A line
- A polygon

The chosen representation should reflect the physical nature of the object.

Examples:

- Electrical cabinet → Point
- Fence → Line
- Building → Polygon

---

# Relationships

A Place Object may be associated with:

- One or more Observations
- Knowledge
- Analyses

Relationships shall be explicit.

No information shall be inferred without documentation.

---

# Lifecycle

A Place Object typically follows this lifecycle.

```
Identified
    │
    ▼
Referenced
    │
    ▼
Observed
    │
    ▼
Updated
    │
    ▼
Retired
```

Retirement does not remove historical observations.

Historical observations remain valid even if the physical object no longer exists.

---

# Status

A Place Object may have a lifecycle status.

Typical statuses include:

- Active
- Removed
- Replaced
- Unknown

The status reflects the current understanding of the physical object.

---

# Relationship with Observations

Observations reference Place Objects.

Multiple observations may reference the same Place Object.

This enables the platform to document changes over time while preserving individual observations.

---

# Relationship with Knowledge

Knowledge may describe a Place Object.

Examples include:

- Frequently tagged
- Cleaned
- Repainted
- Damaged
- Repaired

Knowledge evolves independently of the Place Object.

---

# Domain Rules

The following rules apply.

- Every Place Object shall have a unique identifier.
- A Place Object may exist without observations.
- Multiple observations may reference the same Place Object.
- Removing a Place Object shall never remove observations.
- Place Objects represent physical reality rather than interpretations.

---

# Examples

Example 1

An electrical cabinet has been documented twelve times during two years.

The cabinet is represented as one Place Object.

Each visit creates a new Observation.

---

Example 2

A railway bridge has graffiti documented every month.

The bridge remains one Place Object.

Each documented occurrence becomes a separate Observation.

---

Example 3

A utility box is removed by the municipality.

The Place Object status changes to "Removed".

Historical observations remain available.

---

# Related Documents

- DOMAIN_MODEL.md
- OBSERVATION.md
- KNOWLEDGE.md
- RELATIONS.md
- ANALYSIS.md
