# Observation Resource

> This document defines the Observation resource within the Urban Observation Platform (UOP).

An Observation represents an immutable record of something observed in the physical environment.

Observations are the foundation of the UOP domain model. Every piece of derived information originates from one or more observations.

This document is normative. Implementations claiming conformance with the UOP specification shall satisfy the requirements defined herein.

---

# Purpose

The purpose of the Observation resource is to capture facts about the physical world without interpretation.

Observations preserve what was observed, when it was observed and how it was observed.

Interpretation is intentionally separated into the Knowledge resource.

---

# Scope

The Observation resource is responsible for representing:

- A single observation event.
- The metadata describing that event.
- References to collected evidence.
- Provenance information.

The Observation resource does **not** represent:

- Interpretations
- Classifications
- Analysis results
- Derived conclusions

These belong to other resources.

---

# Resource Definition

An Observation is an immutable domain resource.

Once created, the contents of an Observation shall never change.

Corrections shall be represented by creating a new Observation rather than modifying an existing one.

This behaviour is defined by ADR-0001.

---

# Resource Representation

An Observation consists of:

- Identifier
- Capture metadata
- Spatial information
- Temporal information
- Evidence references
- Optional descriptive metadata

The representation shall remain independent of storage technology.

---

# Required Properties

Every Observation MUST contain:

- Observation identifier
- Capture timestamp
- Observation location
- Observation source
- Creation timestamp

Implementations MAY include additional required fields provided they remain backwards compatible.

---

# Optional Properties

An Observation MAY include:

- Title
- Description
- Tags
- External references
- Device metadata
- Environmental metadata
- Custom attributes

Optional properties shall not alter the semantic meaning of the observation.

---

# Evidence

An Observation MAY reference one or more evidence objects.

Examples include:

- Photographs
- Video
- Audio
- Documents
- Sensor data

Evidence shall be referenced rather than embedded whenever practical.

Evidence objects are immutable.

---

# Relationships

An Observation may reference:

- Place Objects
- Knowledge
- Relations
- Analysis
- Other Observations

Relationships shall be explicit.

Resources shall not rely on implicit relationships.

---

# Lifecycle

The Observation lifecycle consists of four stages.

```
Created

↓

Validated

↓

Stored

↓

Referenced
```

After storage the Observation becomes immutable.

Observations are never versioned.

---

# Validation Rules

Implementations shall validate:

- Required properties.
- Identifier uniqueness.
- Timestamp format.
- Spatial information.
- Evidence references.

Validation failures shall prevent creation of the Observation.

---

# Immutability

An Observation:

- MUST NOT be modified.
- MUST NOT be versioned.
- MUST remain historically accurate.
- MUST preserve provenance.

If additional information becomes available:

- create Knowledge;
- create Relations; or
- create a new Observation.

---

# Security Considerations

Implementations should protect:

- Personal information
- Sensitive locations
- Protected infrastructure
- Confidential metadata

Security policies are implementation-specific but shall preserve Observation integrity.

---

# Conformance Requirements

A conforming implementation:

MUST

- generate stable identifiers;
- preserve Observation immutability;
- record capture time;
- preserve provenance;
- support evidence references.

SHOULD

- support geospatial coordinates;
- support multiple evidence objects;
- support audit logging.

MAY

- support additional metadata;
- support implementation-specific extensions;
- support custom validation rules.

---

# Example Representation

The following example illustrates one possible JSON representation.

```json
{
  "observationId": "obs-6a3b9d42",
  "capturedAt": "2026-07-19T14:35:27Z",
  "createdAt": "2026-07-19T14:36:10Z",
  "location": {
    "latitude": 59.3293,
    "longitude": 18.0686
  },
  "source": "mobile-app",
  "evidence": [
    {
      "type": "image",
      "objectId": "media-2f5c"
    }
  ]
}
```

The example is informative rather than normative.

Equivalent representations may exist for different transport protocols.

---

# Future Evolution

Future versions of the Observation resource may introduce:

- Additional metadata
- New evidence types
- Extended provenance information
- Additional relationship types

Future revisions should preserve backwards compatibility whenever practical.

---

# Related Documents

- ../API_DESIGN_GUIDELINES.md
- ../RESOURCES.md
- ../../architecture/domain/OBSERVATION.md
- ../../adr/ADR-0001-IMMUTABLE_OBSERVATIONS.md