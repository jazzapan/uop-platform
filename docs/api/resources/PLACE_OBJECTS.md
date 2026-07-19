# Place Object Resource

> This document defines the Place Object resource within the Urban Observation Platform (UOP).

A Place Object represents a persistent physical entity in the observed environment.

Unlike an Observation, which records a specific event at a point in time, a Place Object represents something that exists independently of any individual observation.

This document is normative. Implementations claiming conformance with the UOP Specification shall satisfy the requirements defined herein.

---

# Purpose

The Place Object resource provides a stable identity for physical entities that may be observed repeatedly over time.

Its primary purpose is to connect multiple observations referring to the same real-world object.

Examples include:

- Buildings
- Roads
- Bridges
- Utility poles
- Traffic signs
- Benches
- Trees
- Public artwork
- Utility cabinets

The Place Object resource does not describe observations of these entities. It represents the entities themselves.

---

# Scope

A Place Object represents:

- A physical entity.
- Its persistent identity.
- Descriptive attributes.
- Optional spatial representation.
- Relationships to observations and other resources.

A Place Object does not represent:

- An observation.
- A conclusion.
- A temporary event.
- A processing result.

---

# Resource Definition

A Place Object is a persistent domain resource.

Multiple observations may reference the same Place Object.

A Place Object may exist before, during or after any individual observation.

---

# Resource Representation

A Place Object consists of:

- Identifier
- Object type
- Spatial representation
- Descriptive metadata
- Optional classification
- Relationships

The exact representation is transport-independent.

---

# Required Properties

Every Place Object MUST contain:

- Place Object identifier
- Object type
- Creation timestamp

---

# Optional Properties

A Place Object MAY include:

- Name
- Description
- Tags
- Geometry
- Address
- External identifiers
- Classification
- Status
- Additional metadata

Optional properties shall not change the identity of the object.

---

# Spatial Representation

A Place Object MAY contain one or more spatial representations.

Examples include:

- Point
- Line
- Polygon
- MultiPolygon

Spatial representations should follow recognised geospatial standards where practical.

---

# Identity

A Place Object represents the same physical entity throughout its lifetime.

Changes to descriptive properties do not create a new Place Object.

If an object ceases to exist, the resource should remain available for historical reference.

---

# Relationships

A Place Object may be referenced by:

- Observations
- Knowledge
- Analysis
- Relations

A Place Object may reference:

- Parent Place Objects
- Child Place Objects
- Related Place Objects

Relationship semantics shall be explicit.

---

# Lifecycle

The typical lifecycle is:

```
Created

↓

Referenced

↓

Updated

↓

Archived (optional)
```

Unlike Observations, Place Objects may evolve over time.

---

# Validation Rules

Implementations shall validate:

- Identifier uniqueness
- Object type
- Spatial representation
- Relationship integrity

Validation failures shall prevent creation or modification.

---

# Versioning

Implementations MAY support version history.

Version history should preserve previous representations where practical.

The current specification does not mandate a versioning mechanism.

---

# Security Considerations

Implementations should protect:

- Sensitive infrastructure
- Restricted locations
- Protected facilities
- Confidential metadata

Access control policies are implementation-specific.

---

# Conformance Requirements

A conforming implementation:

MUST

- provide stable identifiers;
- support persistent identity;
- allow multiple observations to reference the same Place Object.

SHOULD

- support spatial representations;
- preserve historical references;
- support explicit relationships.

MAY

- support hierarchical structures;
- support multiple geometries;
- support implementation-specific classifications.

---

# Example Representation

```json
{
  "placeObjectId": "po-10452",
  "objectType": "traffic-sign",
  "createdAt": "2026-07-19T10:22:15Z",
  "name": "Speed Limit Sign",
  "geometry": {
    "type": "Point",
    "coordinates": [
      18.0686,
      59.3293
    ]
  }
}
```

The example is informative rather than normative.

---

# Future Evolution

Future versions may introduce:

- Rich geospatial models
- Semantic classifications
- External authority references
- Digital twin integration
- Spatial indexing metadata

Future revisions should preserve backwards compatibility whenever practical.

---

# Related Documents

- ../COMMON_RESOURCE_SPECIFICATION.md
- ../API_DESIGN_GUIDELINES.md
- ../RESOURCES.md
- ../../architecture/domain/PLACE_OBJECT.md
- ../../architecture/domain/RELATIONS.md