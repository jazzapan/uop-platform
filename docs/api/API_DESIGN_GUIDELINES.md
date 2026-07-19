# API Design Guidelines

> This document defines the design principles and conventions for all APIs within the Urban Observation Platform (UOP).

The purpose of these guidelines is to ensure that all APIs are consistent, predictable and easy to understand, regardless of which component or service implements them.

These guidelines form the foundation for all future API specifications.

---

# Scope

These guidelines apply to:

- Public APIs
- Internal service APIs
- Administrative APIs
- Future extension APIs

Unless explicitly stated otherwise, every API specification within UOP shall follow these guidelines.

---

# Design Goals

The UOP API shall be:

- Consistent
- Predictable
- Resource-oriented
- Stateless
- Versionable
- Self-descriptive
- Easy to evolve
- Independent of implementation technology

---

# General Principles

The API:

- MUST expose domain concepts rather than database structures.
- MUST remain independent of programming language and framework.
- MUST preserve the separation between Observations and Knowledge.
- SHOULD minimise unnecessary complexity.
- SHOULD favour explicitness over implicit behaviour.

---

# Resource-Oriented Design

APIs expose resources.

Examples include:

- Observations
- Knowledge
- Place Objects
- Relations
- Analysis
- Processors

Operations are performed on resources rather than actions.

Example:

```
GET /observations
```

instead of

```
GET /getObservations
```

---

# Uniform Resource Naming

Resource names:

- MUST use nouns.
- MUST use plural form.
- MUST use lowercase letters.
- MUST use hyphen-separated words where necessary.

Examples:

```
/observations
/place-objects
/knowledge
/processors
```

Avoid:

```
/GetObservation
/createKnowledge
```

---

# HTTP Methods

Standard HTTP methods shall be used consistently.

| Method | Purpose |
|----------|----------|
| GET | Read resources |
| POST | Create resources |
| PUT | Replace a resource |
| PATCH | Partially update a resource |
| DELETE | Remove a resource where permitted |

Method semantics shall follow the HTTP specification.

---

# Resource Identifiers

Each resource:

- MUST have a stable identifier.
- MUST remain uniquely identifiable.
- SHOULD avoid exposing implementation details.

Identifiers shall be opaque to API consumers.

---

# JSON Representation

JSON shall be the default exchange format.

Property names:

- MUST use camelCase.
- MUST be descriptive.
- SHOULD remain stable over time.

Example:

```json
{
  "observationId": "...",
  "capturedAt": "...",
  "location": { }
}
```

---

# Dates and Times

All timestamps:

- MUST use ISO 8601.
- MUST include timezone information.
- SHOULD use UTC unless another timezone is explicitly required.

Example:

```
2026-07-19T14:35:27Z
```

---

# Versioning

APIs shall support explicit versioning.

Example:

```
/api/v1/observations
```

Breaking changes require a new API version.

Non-breaking additions should not require a new version.

Versioning strategy is described separately.

---

# Error Handling

Errors shall be returned using a consistent structure.

Every error response should include:

- Error code
- Human-readable message
- Optional details
- Correlation identifier (where applicable)

Detailed error handling is specified separately.

---

# Pagination

Collection resources should support pagination.

Pagination should be predictable and stable.

The pagination strategy is specified separately.

---

# Filtering

Collection resources should support filtering where appropriate.

Filtering should remain:

- Explicit
- Predictable
- Composable

Filtering rules are documented separately.

---

# Sorting

Collection resources should support explicit sorting.

Sorting should never depend on implementation details.

---

# Searching

Search capabilities should be separated from ordinary resource retrieval where appropriate.

Search behaviour is documented separately.

---

# Idempotency

GET operations MUST be idempotent.

PUT operations MUST be idempotent.

DELETE operations SHOULD be idempotent.

POST operations are normally not idempotent unless explicitly documented.

---

# Statelessness

Requests shall be self-contained.

Servers shall not depend upon client session state between requests.

Authentication state is handled independently of application state.

---

# Extensibility

The API should evolve through additive changes whenever possible.

Examples include:

- New optional fields
- New resources
- Additional endpoints

Existing behaviour should remain stable.

---

# Documentation

Every API resource shall be documented.

Documentation should include:

- Purpose
- Resource representation
- Operations
- Parameters
- Responses
- Error conditions
- Examples

OpenAPI descriptions should be generated from or aligned with the written specifications.

---

# Relationship to the Architecture

The API is an implementation interface for the Domain Model.

The API shall expose domain concepts without exposing implementation details.

Changes to the API should remain consistent with:

- Project Philosophy
- Domain Architecture
- Solution Architecture
- Architecture Decision Records

---

# Related Documents

- README.md
- VERSIONING.md
- ERROR_HANDLING.md
- PAGINATION.md
- FILTERING.md
- AUTHENTICATION.md
- ../architecture/domain/DOMAIN_MODEL.md
- ../adr/ADR-0001-IMMUTABLE_OBSERVATIONS.md
- ../adr/ADR-0002-VERSIONED_KNOWLEDGE.md