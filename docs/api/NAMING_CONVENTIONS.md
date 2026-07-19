# API Naming Conventions

> This document defines the naming conventions used throughout the Urban Observation Platform (UOP) API Specification.

Consistent naming improves readability, interoperability and long-term maintainability.

Unless explicitly stated otherwise, all API specifications shall follow the conventions defined in this document.

---

# Purpose

This specification defines conventions for:

- Resource names
- Property names
- Data types
- Enumerations
- Identifiers
- File names
- JSON representations

It intentionally does not define implementation-specific naming conventions.

---

# General Principles

Names shall be:

- Clear
- Consistent
- Predictable
- Technology independent
- Domain-oriented

Names should describe business concepts rather than implementation details.

---

# Resource Names

Resource names represent domain concepts.

Requirements:

- SHALL use singular nouns.
- SHALL use Title Case in documentation.
- SHALL avoid abbreviations unless universally recognised.

Examples:

- Observation
- Place Object
- Knowledge
- Relation
- Analysis
- Processor

---

# Property Names

JSON property names SHALL use lower camelCase.

Examples:

```json
{
  "observationId": "...",
  "capturedAt": "...",
  "createdAt": "...",
  "placeObjectId": "...",
  "confidence": 0.96
}
```

Property names should:

- describe a single concept;
- avoid unnecessary prefixes;
- remain stable over time.

---

# Identifier Properties

Identifier properties SHALL end with `Id`.

Examples:

```text
observationId
knowledgeId
placeObjectId
relationId
analysisId
processorId
```

Identifiers should be opaque to API consumers.

---

# Timestamp Properties

Timestamp properties SHALL end with `At`.

Examples:

```text
createdAt
updatedAt
capturedAt
processedAt
publishedAt
```

All timestamps shall follow the Common Data Types specification.

---

# Boolean Properties

Boolean property names SHOULD express a true/false state.

Examples:

```text
isArchived
isVerified
isPublic
```

Avoid negative forms such as:

```text
isNotVisible
```

---

# Collection Properties

Properties containing multiple values SHOULD use plural nouns.

Examples:

```text
observations
knowledge
relations
tags
processors
```

---

# Enumeration Values

Enumeration values SHOULD use PascalCase.

Examples:

```text
Created
Published
Archived
Retired
```

Enumeration values should remain stable.

---

# Resource Type Names

Resource type names SHALL match the names defined by the specification.

Examples:

```text
Observation
Knowledge
PlaceObject
Relation
Analysis
Processor
```

Transport-specific representations may differ where required.

---

# File Names

Documentation files SHALL use uppercase words separated by underscores.

Examples:

```text
COMMON_DATA_TYPES.md
API_DESIGN_GUIDELINES.md
RESOURCE_LIFECYCLE_SPECIFICATION.md
```

Resource specifications SHALL use plural file names.

Examples:

```text
OBSERVATIONS.md
PLACE_OBJECTS.md
PROCESSORS.md
```

---

# JSON Representation

JSON representations SHOULD:

- use camelCase property names;
- avoid unnecessary nesting;
- remain concise;
- omit null values where practical.

Property ordering is informative only.

---

# Reserved Property Names

The following property names are reserved across the specification:

- id
- type
- version
- createdAt
- updatedAt
- status
- metadata
- links

Resource-specific specifications may extend this list.

---

# Abbreviations

Avoid abbreviations unless they are widely recognised.

Acceptable examples:

- URI
- UUID
- GPS
- OCR
- AI

Avoid implementation-specific abbreviations.

---

# Conformance Requirements

A conforming implementation:

MUST

- use consistent resource names;
- use camelCase JSON properties;
- use stable identifier names.

SHOULD

- avoid unnecessary abbreviations;
- follow the naming patterns defined in this specification.

MAY

- introduce implementation-specific names internally;
- map external systems to these conventions.

---

# Relationship to Other Specifications

This document complements:

- Common Data Types
- Common Resource Specification
- API Design Guidelines

It does not replace resource-specific naming defined by individual specifications.

---

# Related Documents

- API_DESIGN_GUIDELINES.md
- COMMON_DATA_TYPES.md
- COMMON_RESOURCE_SPECIFICATION.md
- RESOURCE_LIFECYCLE_SPECIFICATION.md