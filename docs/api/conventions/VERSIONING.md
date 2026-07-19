# API Versioning

> This document defines the versioning strategy for the Urban Observation Platform (UOP) API.

The purpose of versioning is to enable the API to evolve while maintaining compatibility for existing clients.

This document defines versioning of the API specification. It does not define versioning of individual resources, which is specified separately.

---

# Purpose

The versioning strategy aims to:

- Support backwards compatibility.
- Enable controlled evolution.
- Minimise breaking changes.
- Provide predictable upgrade paths.

---

# Versioning Principles

The UOP API follows semantic versioning.

```
MAJOR.MINOR.PATCH
```

Example:

```
1.0.0
```

---

# Major Versions

A major version introduces incompatible changes.

Examples include:

- Removing API capabilities.
- Renaming resources.
- Breaking representation changes.
- Removing required properties.

Major version changes may require client updates.

Example:

```
1.x.x → 2.0.0
```

---

# Minor Versions

Minor versions introduce new functionality without breaking existing clients.

Examples include:

- New optional properties.
- New resources.
- Additional query capabilities.
- New relation types.

Example:

```
1.2.0 → 1.3.0
```

---

# Patch Versions

Patch versions introduce:

- Documentation improvements.
- Clarifications.
- Bug fixes.
- Editorial corrections.

Patch versions shall not change API behaviour.

Example:

```
1.3.2 → 1.3.3
```

---

# Backwards Compatibility

Minor and patch versions shall remain backwards compatible.

Implementations should avoid:

- Removing existing properties.
- Changing property semantics.
- Changing identifier behaviour.

---

# Deprecation

Deprecated features:

- SHOULD remain available for at least one major version.
- SHOULD be clearly documented.
- SHOULD include migration guidance.

Deprecation does not imply immediate removal.

---

# Resource Evolution

Resource-specific evolution follows the individual resource specifications.

Examples:

- Observation resources are immutable.
- Knowledge resources are versioned.
- Place Objects evolve while preserving identity.

These lifecycle models are independent of API versioning.

---

# Conformance Requirements

A conforming implementation:

MUST

- identify the supported API version;
- follow semantic versioning;
- preserve backwards compatibility within a major version.

SHOULD

- document deprecated features;
- provide migration guidance.

MAY

- support multiple API versions simultaneously.

---

# Related Documents

- ../API_DESIGN_GUIDELINES.md
- ../RESOURCE_LIFECYCLE_SPECIFICATION.md
- ../COMMON_RESOURCE_SPECIFICATION.md