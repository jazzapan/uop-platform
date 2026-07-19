# Pagination

> This document defines the pagination conventions for the Urban Observation Platform (UOP) API Specification.

Pagination allows clients to retrieve large collections of resources efficiently while maintaining predictable and consistent behaviour.

This specification defines pagination semantics independently of any transport protocol.

---

# Purpose

Pagination aims to:

- Limit response size.
- Improve performance.
- Support scalable collections.
- Enable predictable navigation through large datasets.

---

# Applicability

Pagination applies only to operations that return collections of resources.

Operations returning a single resource are not paginated.

Examples of paginated collections include:

- Observations
- Place Objects
- Knowledge
- Relations
- Analyses
- Processors

---

# Design Principles

Pagination shall be:

- Predictable
- Stable
- Efficient
- Independent of resource type

Clients should be able to navigate collections without needing knowledge of implementation details.

---

# Pagination Models

The UOP Specification does not mandate a specific pagination mechanism.

Implementations MAY support:

- Offset-based pagination
- Cursor-based pagination
- Token-based pagination

The chosen mechanism shall be documented by the implementation.

---

# Ordering

Pagination requires a deterministic ordering.

Implementations SHALL define a default ordering for every paginated collection.

Clients MAY request alternative orderings where supported.

Ordering shall remain stable throughout a paginated result set.

---

# Page Size

Implementations SHOULD define:

- A default page size.
- A maximum page size.

Clients may request smaller page sizes.

Implementations may reject requests exceeding the maximum supported page size.

---

# Collection Metadata

Paginated responses SHOULD provide metadata describing the returned collection.

Typical metadata includes:

- Number of returned resources
- Total number of available resources (where practical)
- Information required to retrieve the next page
- Information required to retrieve the previous page

The exact representation is transport-specific.

---

# Consistency

Implementations SHOULD provide consistent pagination behaviour while clients navigate a collection.

If underlying resources change during navigation, implementations should document how consistency is maintained.

---

# Performance

Implementations SHOULD optimise pagination for large collections.

Implementations are not required to calculate total result counts if doing so would significantly impact performance.

---

# Error Handling

Pagination-related errors shall follow the Error Handling specification.

Examples include:

- Invalid page size
- Invalid cursor
- Invalid continuation token

---

# Conformance Requirements

A conforming implementation:

MUST

- support deterministic ordering;
- document its pagination mechanism;
- apply pagination consistently across resource collections.

SHOULD

- provide collection metadata;
- define default and maximum page sizes;
- support efficient navigation through large datasets.

MAY

- support multiple pagination mechanisms;
- omit total result counts where impractical.

---

# Relationship to Transport Protocols

This specification defines pagination behaviour only.

Transport-specific representations (such as query parameters or response headers) are defined separately by the corresponding transport specification.

---

# Related Documents

- FILTERING.md
- SEARCH.md
- ERROR_HANDLING.md
- VERSIONING.md
- ../API_DESIGN_GUIDELINES.md