# Relation Resource

> This document defines the Relation resource within the Urban Observation Platform (UOP).

A Relation represents an explicit connection between two or more resources within the platform.

Relations are first-class resources. They provide semantic meaning to connections while preserving the independence of the resources they link.

This document is normative. Implementations claiming conformance with the UOP Specification shall satisfy the requirements defined herein.

---

# Purpose

The purpose of the Relation resource is to describe how resources are connected.

Rather than embedding references directly into resources, Relations provide a flexible and extensible mechanism for modelling associations.

Examples include:

- An Observation depicts a Place Object.
- Knowledge is derived from an Observation.
- An Analysis is based on multiple Knowledge resources.
- A Place Object is part of another Place Object.

---

# Scope

A Relation represents:

- An explicit association.
- The type of relationship.
- The participating resources.
- Optional metadata describing the relationship.

A Relation does not duplicate the data contained within the connected resources.

---

# Resource Definition

A Relation is an independent domain resource.

Relations connect two or more resources while remaining independent of their internal representations.

Deleting a resource should not silently remove historical Relations.

---

# Resource Representation

A Relation consists of:

- Relation identifier
- Relation type
- Source resource
- Target resource
- Provenance
- Creation metadata

The representation shall remain transport-independent.

---

# Required Properties

Every Relation MUST contain:

- Relation identifier
- Relation type
- Source resource identifier
- Target resource identifier
- Created timestamp

---

# Optional Properties

A Relation MAY include:

- Description
- Confidence
- Validity period
- Provenance
- Tags
- External references
- Additional metadata

---

# Relation Types

Implementations SHOULD support well-defined relation types.

Examples include:

- depicts
- derived-from
- belongs-to
- contains
- adjacent-to
- references
- supersedes
- related-to

Implementations MAY define additional relation types.

---

# Direction

Relations may be:

- Directed
- Undirected

The semantics of the relation type determine whether direction is significant.

---

# Relationships

Relations may connect any combination of supported resources.

Examples include:

- Observation → Place Object
- Observation → Observation
- Knowledge → Observation
- Knowledge → Place Object
- Analysis → Knowledge
- Place Object → Place Object

Future resource types may also participate in Relations.

---

# Lifecycle

The typical lifecycle is:

```
Created

↓

Validated

↓

Referenced

↓

Archived (optional)
```

Relations should remain stable once published.

If the meaning of a relation changes significantly, a new Relation should normally be created.

---

# Validation Rules

Implementations shall validate:

- Existence of referenced resources.
- Relation type.
- Direction (where applicable).
- Required properties.

Validation failures shall prevent publication.

---

# Security Considerations

Implementations should protect:

- Sensitive associations.
- Restricted infrastructure relationships.
- Confidential metadata.

Access control is implementation-specific.

---

# Conformance Requirements

A conforming implementation:

MUST

- provide stable identifiers;
- reference existing resources;
- define the relation type;
- preserve relationship integrity.

SHOULD

- support provenance;
- support confidence information;
- preserve historical relations.

MAY

- support custom relation types;
- support multi-resource relations;
- support temporal validity.

---

# Example Representation

```json
{
  "relationId": "rel-3159",
  "relationType": "depicts",
  "source": {
    "resourceType": "Observation",
    "resourceId": "obs-6a3b9d42"
  },
  "target": {
    "resourceType": "PlaceObject",
    "resourceId": "po-10452"
  },
  "createdAt": "2026-07-19T16:05:11Z"
}
```

The example is informative rather than normative.

---

# Future Evolution

Future versions may introduce:

- Temporal relationships
- Weighted relationships
- Semantic ontologies
- Graph query support
- Relationship constraints

Future revisions should preserve backwards compatibility whenever practical.

---

# Related Documents

- ../COMMON_RESOURCE_SPECIFICATION.md
- ../API_DESIGN_GUIDELINES.md
- ../RESOURCES.md
- ../../architecture/domain/RELATIONS.md
- resources/OBSERVATIONS.md
- resources/PLACE_OBJECTS.md
- resources/KNOWLEDGE.md