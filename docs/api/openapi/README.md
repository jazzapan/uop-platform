# UOP REST API (OpenAPI)

> This section defines the REST API binding of the Urban Observation Platform (UOP) API Specification.

The UOP Platform Specification defines the domain model, resource model and API semantics independently of any transport protocol.

This directory defines how those concepts are exposed through a RESTful HTTP API using the OpenAPI Specification.

The OpenAPI documents are normative for the REST transport only.

---

# Purpose

The purpose of this section is to:

- Define the REST interface.
- Describe HTTP resource mappings.
- Specify request and response formats.
- Define HTTP status codes.
- Enable automatic client generation.
- Support interoperability between REST implementations.

---

# Relationship to the Platform Specification

The Platform Specification defines:

- Resources
- Lifecycles
- Data types
- Naming conventions
- API semantics

The REST API defines:

- HTTP methods
- URI structure
- Request bodies
- Response bodies
- Status codes
- Headers
- Media types

The REST API shall not redefine the platform concepts.

Instead, it maps those concepts to HTTP.

---

# Design Principles

The REST API shall:

- Follow the Platform Specification.
- Be resource-oriented.
- Use predictable URIs.
- Use standard HTTP semantics.
- Preserve resource identity.
- Preserve lifecycle semantics.

The REST API should avoid introducing concepts that are not defined by the Platform Specification.

---

# Resource Mapping

Each platform resource is mapped to one or more REST endpoints.

Examples include:

| Platform Resource | REST Collection |
|-------------------|-----------------|
| Observation | `/observations` |
| Place Object | `/place-objects` |
| Knowledge | `/knowledge` |
| Relation | `/relations` |
| Analysis | `/analyses` |
| Processor | `/processors` |

Additional transport-specific endpoints may be defined where necessary.

---

# Lifecycle Mapping

Resource lifecycle behaviour is preserved by the REST API.

Examples include:

- Immutable resources do not support modification.
- Persistent resources support updates.
- Versioned resources expose version history.

The HTTP operations used to implement these behaviours are defined by the REST specification.

---

# Error Mapping

The platform defines a common error model.

The REST API maps that model to HTTP status codes.

Examples include:

- Validation errors
- Authentication failures
- Authorization failures
- Missing resources
- Conflicts
- Internal server errors

The structure of error responses remains consistent with the Error Handling specification.

---

# Versioning

The REST API follows the API Versioning specification.

REST implementations should clearly expose the supported API version.

The mechanism is implementation-specific.

Examples include:

- URI versioning
- Header versioning
- Media type versioning

The UOP Specification does not mandate a single approach.

---

# OpenAPI Documents

This directory contains the machine-readable OpenAPI descriptions.

Typical contents include:

```text
openapi/
│
├── README.md
├── openapi.yaml
├── components/
│   ├── schemas/
│   ├── parameters/
│   ├── responses/
│   └── security/
│
├── paths/
│   ├── observations.yaml
│   ├── place-objects.yaml
│   ├── knowledge.yaml
│   ├── relations.yaml
│   ├── analyses.yaml
│   └── processors.yaml
│
└── examples/
```

The exact organisation may evolve as the specification grows.

---

# Conformance

A conforming REST implementation:

MUST

- conform to the Platform Specification;
- implement the REST mappings defined by the OpenAPI documents;
- preserve the semantics of the platform resources.

SHOULD

- expose complete OpenAPI documentation;
- support automated client generation;
- document implementation-specific extensions.

MAY

- provide additional REST endpoints;
- support implementation-specific capabilities that do not conflict with the Platform Specification.

---

# Future Transport Bindings

The Platform Specification is transport-independent.

Future transport bindings may include:

- GraphQL
- gRPC
- Event-driven APIs
- OGC API
- Message-based interfaces

Each transport binding should preserve the semantics defined by the Platform Specification.

---

# Related Documents

- ../README.md
- ../API_DESIGN_GUIDELINES.md
- ../COMMON_RESOURCE_SPECIFICATION.md
- ../RESOURCE_LIFECYCLE_SPECIFICATION.md
- ../conventions/VERSIONING.md
- ../conventions/ERROR_HANDLING.md