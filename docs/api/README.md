# UOP API Specification

> This section defines the application programming interfaces (APIs) of the Urban Observation Platform (UOP).

The API specification provides a technology-independent contract for interacting with UOP implementations.

It defines the resources, operations and conventions that clients and services rely upon.

The API specification complements the architecture documentation by describing how the concepts defined in the Domain Architecture are exposed through stable interfaces.

---

# Purpose

The purpose of the API specification is to:

- Define stable platform contracts.
- Ensure interoperability between implementations.
- Promote consistency across APIs.
- Support long-term evolution without unnecessary breaking changes.
- Enable client libraries and third-party integrations.

---

# Relationship to the Architecture

The architecture describes:

- Why the platform exists.
- What the platform is.
- How the platform is structured.

The API specification describes:

- How software interacts with the platform.

The API does not define the domain model.

Instead, it exposes the domain model through well-defined interfaces.

---

# API Documents

## API_DESIGN_GUIDELINES.md

Defines the conventions that every API within UOP shall follow.

Topics include:

- Resource-oriented design
- Naming conventions
- HTTP methods
- JSON representation
- Versioning principles
- Statelessness

This document should be read first.

---

## VERSIONING.md

Defines the API versioning strategy and compatibility guarantees.

---

## AUTHENTICATION.md

Defines how clients authenticate and how authenticated identities are represented.

---

## ERROR_HANDLING.md

Defines the common error model used by all APIs.

---

## PAGINATION.md

Defines how collection resources are paginated.

---

## FILTERING.md

Defines common filtering conventions.

---

## SEARCH.md

Defines search capabilities and search-related endpoints.

---

## RESOURCES.md

Provides an overview of the platform's primary API resources and their relationships.

Individual resource specifications may later be split into separate documents as the API grows.

---

## openapi/

Contains the machine-readable OpenAPI specification for the current API version.

The OpenAPI description should remain aligned with the written documentation.

---

# Design Principles

The UOP API follows several key principles.

- Resource-oriented.
- Predictable.
- Stateless.
- Consistent.
- Versioned.
- Self-describing.
- Technology independent.

These principles are defined in greater detail within the API Design Guidelines.

---

# Reading Order

New contributors are encouraged to read the API documentation in the following order:

1. API_DESIGN_GUIDELINES.md
2. VERSIONING.md
3. AUTHENTICATION.md
4. ERROR_HANDLING.md
5. PAGINATION.md
6. FILTERING.md
7. SEARCH.md
8. RESOURCES.md
9. OpenAPI specification

---

# Conformance

An implementation claiming conformance with the UOP API Specification should implement the requirements defined in this documentation.

Future versions of the specification may introduce optional capabilities while maintaining backwards compatibility where practical.

---

# Related Documentation

- `../architecture/README.md`
- `../architecture/domain/README.md`
- `../architecture/solution/README.md`
- `../adr/README.md`
- `../philosophy/PROJECT_PHILOSOPHY.md`