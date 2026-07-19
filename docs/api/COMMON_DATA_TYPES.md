# Common Data Types

> This document defines the common data types used throughout the Urban Observation Platform (UOP) API Specification.

The purpose of this specification is to establish a consistent vocabulary for all API resources and conventions.

Unless explicitly stated otherwise, every API specification within UOP shall use the data types defined in this document.

---

# Purpose

The Common Data Types specification defines:

- Primitive value types
- Common structured types
- Formatting rules
- Validation requirements
- Conformance requirements

Individual resource specifications reference these types rather than redefining them.

---

# Design Principles

Common data types shall be:

- Technology independent
- Human readable where practical
- Machine processable
- Stable over time
- Consistent across the platform

---

# Identifier

An Identifier uniquely identifies a resource.

Requirements:

- MUST be unique within its resource type.
- MUST remain stable.
- MUST NOT expose implementation details.
- SHOULD be opaque.

Example:

```text
obs-6a3b9d42
```

---

# Version

A Version identifies a specific revision of a versioned resource.

Requirements:

- MUST identify exactly one version.
- SHOULD be monotonically increasing or otherwise ordered.
- MUST remain immutable.

Examples:

```text
1
2
3
```

or

```text
v2.1
```

The version format is implementation-specific.

---

# Timestamp

A Timestamp represents a specific point in time.

Requirements:

- MUST use ISO 8601.
- MUST include timezone information.
- SHOULD use UTC.

Example:

```text
2026-07-19T14:35:27Z
```

---

# URI

A URI identifies an external or internal resource.

Requirements:

- SHOULD follow RFC 3986.
- MUST be absolute unless otherwise specified.

Example:

```text
https://example.org/media/image-42
```

---

# Coordinate

A Coordinate represents a geographic position.

Requirements:

- Latitude
- Longitude

Optional:

- Altitude

Example:

```json
{
  "latitude": 59.3293,
  "longitude": 18.0686
}
```

---

# Geometry

A Geometry represents the spatial extent of a Place Object.

Supported representations may include:

- Point
- LineString
- Polygon
- MultiPoint
- MultiLineString
- MultiPolygon

Implementations should align with established geospatial standards where practical.

---

# Confidence

Confidence expresses the estimated reliability of derived information.

Requirements:

- MUST represent confidence in the interpretation.
- MUST NOT represent observation quality.

Recommended representation:

```text
0.0 – 1.0
```

Example:

```text
0.96
```

---

# Reference

A Reference identifies another resource.

A Reference consists of:

- Resource type
- Resource identifier

Example:

```json
{
  "resourceType": "Observation",
  "resourceId": "obs-6a3b9d42"
}
```

References should remain stable.

---

# Metadata

Metadata consists of optional descriptive information.

Examples include:

- Title
- Description
- Tags
- Labels

Metadata improves discoverability but does not alter resource semantics.

---

# Tag

A Tag is a short descriptive keyword.

Requirements:

- SHOULD be human readable.
- SHOULD be concise.
- MAY be implementation-specific.

Example:

```text
traffic-sign
```

---

# Language Tag

Language tags identify the language of textual content.

Implementations should use BCP 47 language tags.

Example:

```text
en
sv-SE
```

---

# Status

Status indicates the current state of a resource where applicable.

The permitted values are defined by the individual resource specification.

Examples include:

- Created
- Published
- Archived
- Deprecated

---

# Extension

Extensions provide implementation-specific information.

Extensions:

- MUST NOT change the meaning of standard properties.
- MUST remain backwards compatible.

Implementations should namespace extensions where appropriate.

---

# Conformance Requirements

A conforming implementation:

MUST

- use stable identifiers;
- use ISO 8601 timestamps;
- preserve reference integrity.

SHOULD

- use standard language tags;
- use recognised geospatial formats.

MAY

- define additional implementation-specific data types;
- extend structured types while maintaining backwards compatibility.

---

# Relationship to Resource Specifications

All API resource specifications inherit the common data types defined in this document.

Individual specifications may introduce additional specialised types but should not redefine the common types.

---

# Related Documents

- API_DESIGN_GUIDELINES.md
- COMMON_RESOURCE_SPECIFICATION.md
- RESOURCE_LIFECYCLE_SPECIFICATION.md
- RESOURCES.md