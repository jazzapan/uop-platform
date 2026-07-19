# Filtering

> This document defines the filtering conventions for the Urban Observation Platform (UOP) API Specification.

Filtering allows clients to restrict resource collections based on specified criteria.

This specification defines filtering semantics independently of any transport protocol or query language.

---

# Purpose

Filtering aims to:

- Reduce the amount of returned data.
- Improve query efficiency.
- Support selective retrieval.
- Enable precise resource discovery.

Filtering applies only to collection operations.

---

# Design Principles

Filtering shall be:

- Predictable
- Consistent
- Resource independent
- Transport independent

Filtering should never alter the underlying resources.

It only affects which resources are returned.

---

# Applicability

Filtering may be applied to any collection of resources.

Examples include:

- Observations
- Place Objects
- Knowledge
- Relations
- Analyses
- Processors

Individual resource specifications may define additional filterable properties.

---

# Filter Criteria

Implementations SHOULD support filtering using resource properties.

Examples include:

- Identifier
- Resource type
- Status
- Timestamp
- Tags
- Confidence
- Processor
- Version

Additional criteria may be supported.

---

# Multiple Criteria

Clients may combine multiple filter criteria.

Unless documented otherwise, multiple criteria should be interpreted using logical AND.

Implementations may additionally support logical OR and grouping.

---

# Comparison Operations

Implementations SHOULD support common comparison operations.

Examples include:

- Equals
- Not equals
- Greater than
- Less than
- Greater than or equal
- Less than or equal
- Contains
- Starts with
- Ends with

The supported comparison operations shall be documented by the implementation.

---

# Temporal Filtering

Implementations SHOULD support filtering based on timestamps where applicable.

Examples include:

- Created after
- Created before
- Captured during
- Published after

Timestamp values shall follow the Common Data Types specification.

---

# Spatial Filtering

Resources with spatial information may support spatial filtering.

Examples include:

- Within area
- Intersects geometry
- Near location
- Bounding box

Spatial operations should align with recognised geospatial standards where practical.

---

# Result Ordering

Filtering may be combined with ordering and pagination.

Filtering shall be applied before pagination.

Ordering behaviour is defined separately by the implementation.

---

# Invalid Filters

Invalid filter expressions shall result in structured error information.

Examples include:

- Unknown property
- Unsupported comparison
- Invalid value type
- Invalid geometry

Errors shall follow the Error Handling specification.

---

# Performance

Implementations SHOULD optimise commonly used filters.

Implementations MAY restrict expensive filter operations where necessary.

Any restrictions should be documented.

---

# Conformance Requirements

A conforming implementation:

MUST

- apply filtering consistently;
- validate filter criteria;
- return structured errors for invalid filters.

SHOULD

- support multiple filter criteria;
- support temporal filtering where applicable;
- document supported comparison operations.

MAY

- support spatial filtering;
- support implementation-specific filter capabilities.

---

# Relationship to Transport Protocols

This specification defines filtering semantics only.

Transport-specific filter syntax is defined separately by the corresponding transport specification.

---

# Related Documents

- SEARCH.md
- PAGINATION.md
- ERROR_HANDLING.md
- ../COMMON_DATA_TYPES.md
- ../API_DESIGN_GUIDELINES.md