# Error Handling

> This document defines the error handling conventions for the Urban Observation Platform (UOP) API Specification.

The purpose of this specification is to provide a consistent mechanism for communicating errors to API consumers while remaining independent of any transport protocol.

---

# Purpose

The error handling conventions aim to:

- Provide consistent error reporting.
- Support automated error processing.
- Improve troubleshooting.
- Preserve implementation independence.

Every failed operation should return a structured error representation.

---

# Error Principles

Errors shall:

- Be predictable.
- Be machine readable.
- Be human understandable.
- Avoid exposing implementation details.
- Support traceability.

Error messages should help clients understand what went wrong and, where appropriate, how to correct the request.

---

# Error Representation

Every error representation SHOULD contain:

- Error code
- Error message
- Timestamp

It MAY also contain:

- Correlation identifier
- Resource identifier
- Validation details
- Additional metadata

---

# Error Code

Every error SHALL expose a stable error code.

Error codes:

- MUST remain stable across minor releases.
- SHOULD be concise.
- SHOULD be implementation independent.

Example:

```text
OBSERVATION_NOT_FOUND
```

---

# Error Message

Every error SHALL include a human-readable message.

Messages should:

- Explain the problem.
- Avoid implementation details.
- Be suitable for display in logs.

Example:

```text
Observation 'obs-6a3b9d42' does not exist.
```

---

# Correlation Identifier

Implementations SHOULD provide a correlation identifier.

The identifier allows requests to be traced through logs and distributed systems.

Example:

```text
req-84a2fc91
```

---

# Validation Errors

Validation errors SHOULD identify the affected property.

Example:

```json
{
  "property": "capturedAt",
  "message": "Timestamp must use ISO 8601 format."
}
```

Multiple validation errors may be returned for a single request.

---

# Error Categories

Implementations SHOULD classify errors consistently.

Typical categories include:

- Validation
- Authentication
- Authorization
- Resource
- Conflict
- Processing
- Internal
- Configuration

Additional categories MAY be introduced.

---

# Retry Behaviour

Errors SHOULD indicate whether retrying the operation is appropriate.

Examples include:

- Retry recommended
- Retry not recommended
- Retry after correction

The mechanism is implementation-specific.

---

# Sensitive Information

Error responses MUST NOT expose:

- Credentials
- Internal configuration
- Stack traces
- Database details
- Security-sensitive information

Detailed diagnostics should remain in server logs.

---

# Example Representation

```json
{
  "errorCode": "OBSERVATION_NOT_FOUND",
  "message": "Observation 'obs-6a3b9d42' does not exist.",
  "timestamp": "2026-07-19T18:42:11Z",
  "correlationId": "req-84a2fc91"
}
```

This example is informative rather than normative.

---

# Conformance Requirements

A conforming implementation:

MUST

- return structured error information;
- provide stable error codes;
- avoid exposing sensitive implementation details.

SHOULD

- include correlation identifiers;
- provide validation details where applicable;
- categorise errors consistently.

MAY

- include implementation-specific diagnostic metadata.

---

# Relationship to Transport Protocols

This specification defines the structure of error information.

Transport-specific mappings (such as HTTP status codes) are defined separately by the corresponding transport specification.

---

# Related Documents

- VERSIONING.md
- ../COMMON_DATA_TYPES.md
- ../COMMON_RESOURCE_SPECIFICATION.md
- ../API_DESIGN_GUIDELINES.md