# Search

> This document defines the search conventions for the Urban Observation Platform (UOP) API Specification.

Search enables clients to discover resources based on relevance, textual content, semantic meaning or other implementation-specific search capabilities.

This specification defines search behaviour independently of any transport protocol or search technology.

---

# Purpose

Search aims to:

- Enable efficient resource discovery.
- Support free-text and structured search.
- Improve usability for large datasets.
- Complement filtering and pagination.

Search does not replace filtering.

Filtering narrows known datasets, while search discovers relevant resources.

---

# Design Principles

Search shall be:

- Predictable
- Consistent
- Resource independent
- Technology independent

Search results should be reproducible where practical.

---

# Applicability

Search may be supported for any resource collection.

Examples include:

- Observations
- Place Objects
- Knowledge
- Relations
- Analyses
- Processors

Implementations should document which resources support search.

---

# Search Criteria

Implementations MAY support searching by:

- Free text
- Resource names
- Descriptions
- Tags
- Metadata
- Identifiers
- Geographic location
- Temporal information

Additional search criteria may be supported.

---

# Search Technologies

The UOP Specification does not prescribe a search implementation.

Examples include:

- Full-text indexing
- Keyword search
- Semantic search
- Vector search
- Knowledge graph traversal
- External search services

The chosen implementation shall not affect API interoperability.

---

# Relevance

Search results SHOULD be ordered by relevance unless another ordering is explicitly requested.

The relevance algorithm is implementation-specific.

Implementations should document significant relevance factors where practical.

---

# Combining Search and Filtering

Search may be combined with filtering.

When both are applied:

1. Search identifies candidate resources.
2. Filtering restricts the candidate set.
3. Ordering is applied.
4. Pagination is applied.

Implementations should apply these steps consistently.

---

# Result Metadata

Search responses SHOULD include metadata where appropriate.

Examples include:

- Total matches
- Relevance score
- Search execution time
- Applied search criteria

The representation of this metadata is transport-specific.

---

# Unsupported Searches

Implementations MAY reject unsupported search requests.

Examples include:

- Unsupported resource type
- Unsupported search field
- Invalid search expression
- Excessive query complexity

Errors shall follow the Error Handling specification.

---

# Performance

Implementations SHOULD optimise common search operations.

Implementations MAY impose limits on:

- Query complexity
- Result size
- Execution time

Such limits should be documented.

---

# Conformance Requirements

A conforming implementation:

MUST

- apply search consistently;
- return structured errors for invalid search requests.

SHOULD

- support free-text search where appropriate;
- document supported search capabilities;
- combine search predictably with filtering and pagination.

MAY

- support semantic search;
- support vector search;
- support implementation-specific search algorithms.

---

# Relationship to Filtering

Filtering and Search are complementary.

Filtering selects resources that satisfy explicit criteria.

Search discovers resources that are likely to satisfy the client's intent.

Implementations should expose both capabilities independently where practical.

---

# Relationship to Transport Protocols

This specification defines search behaviour only.

Transport-specific query syntax and response formats are defined separately by the corresponding transport specification.

---

# Related Documents

- FILTERING.md
- PAGINATION.md
- ERROR_HANDLING.md
- ../API_DESIGN_GUIDELINES.md
- ../COMMON_DATA_TYPES.md