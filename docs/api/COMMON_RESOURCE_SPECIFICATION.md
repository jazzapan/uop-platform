# Common Resource Specification

> This document defines the common properties and behavioural requirements shared by all API resources within the Urban Observation Platform (UOP).

The purpose of this specification is to establish a consistent contract across all resources while avoiding duplication in individual resource specifications.

Unless explicitly stated otherwise, every API resource defined by the UOP Specification shall conform to the requirements described in this document.

---

# Purpose

The Common Resource Specification defines:

- Common identifiers
- Common metadata
- Timestamps
- Provenance
- Resource links
- Extensions
- Conformance requirements

Individual resource specifications extend this document rather than redefining common concepts.

---

# Common Principles

Every API resource shall:

- Represent a domain concept.
- Have a stable identity.
- Be independently addressable.
- Be serializable.
- Be technology independent.
- Preserve provenance where applicable.

Resources should expose business concepts rather than implementation details.

---

# Resource Identity

Every resource MUST have a unique identifier.

Identifiers:

- MUST be stable.
- MUST be unique within their resource type.
- MUST NOT expose implementation details.
- SHOULD be opaque to API consumers.

The format of identifiers is implementation-specific unless defined by a resource specification.

---

# Resource Metadata

Every resource MAY contain descriptive metadata.

Typical metadata includes:

- title
- description
- tags
- labels

Metadata improves discoverability but shall not alter the semantic meaning of a resource.

---

# Timestamps

Resources SHOULD expose timestamps where appropriate.

Common timestamps include:

- createdAt
- updatedAt
- capturedAt
- processedAt

All timestamps:

- MUST use ISO 8601.
- SHOULD use UTC.
- MUST include timezone information.

---

# Provenance

Resources SHOULD preserve provenance information.

Examples include:

- creator
- processor
- source system
- originating observation

Provenance enables traceability throughout the platform.

---

# Relationships

Resources may reference other resources.

Relationships:

- SHOULD be explicit.
- SHOULD use stable identifiers.
- SHOULD avoid duplication.

Relationship semantics are defined by the individual resource specifications.

---

# Extensions

Implementations MAY extend resource representations.

Extensions:

- MUST NOT change the meaning of existing properties.
- MUST remain backwards compatible.
- SHOULD use implementation-specific namespaces where appropriate.

Extensions shall not prevent interoperability between conforming implementations.

---

# Validation

Every resource specification shall define:

- Required properties
- Optional properties
- Validation rules
- Conformance requirements

Validation shall occur before a resource is accepted by the platform.

---

# Security Considerations

Resource specifications should identify:

- Sensitive properties
- Personally identifiable information
- Confidential metadata
- Access restrictions

Security requirements may vary between resource types.

---

# Conformance Requirements

A conforming implementation:

MUST

- provide stable identifiers;
- support ISO 8601 timestamps;
- preserve resource identity;
- validate required properties.

SHOULD

- preserve provenance;
- expose descriptive metadata;
- use explicit relationships.

MAY

- define implementation-specific extensions;
- introduce additional optional metadata.

---

# Relationship to Resource Specifications

The following resource specifications inherit the concepts defined in this document.

- Observation
- Place Object
- Knowledge
- Relation
- Analysis
- Processor

Individual specifications may introduce additional requirements but should not contradict this specification.

---

# Related Documents

- README.md
- API_DESIGN_GUIDELINES.md
- RESOURCES.md
- resources/OBSERVATIONS.md