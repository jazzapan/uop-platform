# Knowledge Resource

> This document defines the Knowledge resource within the Urban Observation Platform (UOP).

Knowledge represents information derived from one or more observations through interpretation, analysis or processing.

Unlike Observations, Knowledge is expected to evolve over time as new observations become available, analytical methods improve or human understanding changes.

This document is normative. Implementations claiming conformance with the UOP Specification shall satisfy the requirements defined herein.

---

# Purpose

The purpose of the Knowledge resource is to separate facts from interpretation.

Observations record what was observed.

Knowledge records what is currently understood.

This distinction preserves historical evidence while allowing understanding to improve over time.

---

# Scope

A Knowledge resource represents:

- An interpretation
- A classification
- A detected condition
- A measured property
- A derived conclusion
- An inferred relationship

A Knowledge resource does not represent:

- Raw observations
- Media objects
- Processing jobs
- Physical entities

---

# Resource Definition

Knowledge is a versioned domain resource.

Each version represents the current understanding at a particular point in time.

Older versions remain part of the historical record.

Knowledge shall always reference the observations from which it was derived.

---

# Resource Representation

A Knowledge resource consists of:

- Knowledge identifier
- Version identifier
- Knowledge type
- Current status
- Provenance
- Supporting observations
- Confidence
- Creation metadata

The representation shall remain independent of implementation technology.

---

# Required Properties

Every Knowledge resource MUST contain:

- Knowledge identifier
- Version identifier
- Knowledge type
- Created timestamp
- Provenance
- At least one supporting Observation

---

# Optional Properties

A Knowledge resource MAY include:

- Title
- Description
- Confidence score
- Classification
- Validity period
- Supporting evidence
- Tags
- External references
- Custom metadata

---

# Provenance

Every Knowledge resource SHALL record how it was produced.

Examples include:

- Human assessment
- OCR
- Computer vision
- Machine learning
- Sensor fusion
- External import

The provenance information should allow future users to understand how the knowledge was created.

---

# Versioning

Knowledge evolves through versioning.

A new version SHALL be created whenever:

- Interpretation changes.
- Confidence changes significantly.
- Additional observations affect the conclusion.
- New analytical methods produce a better result.

Older versions SHALL remain available for historical traceability.

Knowledge versions MUST NOT overwrite previous versions.

---

# Confidence

Knowledge MAY express confidence.

Confidence indicates the estimated reliability of the interpretation rather than the quality of the underlying observations.

The confidence model is implementation-specific.

---

# Relationships

Knowledge may reference:

- Observations
- Place Objects
- Relations
- Analysis
- Processors
- Earlier Knowledge versions

Knowledge shall maintain explicit references to all supporting resources.

---

# Lifecycle

The typical lifecycle is:

```
Created

↓

Validated

↓

Published

↓

Superseded

↓

Archived (optional)
```

Superseded versions remain available.

Knowledge is never destroyed solely because a newer version exists.

---

# Validation Rules

Implementations shall validate:

- Supporting observations
- Provenance
- Version consistency
- Knowledge type
- Required properties

Validation failures shall prevent publication.

---

# Security Considerations

Implementations should protect:

- Sensitive interpretations
- Restricted assessments
- Internal classifications
- Protected metadata

Security policies are implementation-specific.

---

# Conformance Requirements

A conforming implementation:

MUST

- provide stable identifiers;
- support versioning;
- preserve historical versions;
- maintain provenance;
- reference supporting observations.

SHOULD

- expose confidence information;
- support multiple provenance sources;
- preserve publication history.

MAY

- support review workflows;
- support implementation-specific knowledge types;
- support additional metadata.

---

# Example Representation

```json
{
  "knowledgeId": "know-8421",
  "version": 3,
  "knowledgeType": "traffic-sign-condition",
  "createdAt": "2026-07-19T15:42:18Z",
  "confidence": 0.96,
  "derivedFrom": [
    "obs-6a3b9d42",
    "obs-6a3b9d81"
  ],
  "processor": "vision-model-v2"
}
```

The example is informative rather than normative.

---

# Future Evolution

Future versions may introduce:

- Rich semantic models
- Confidence histories
- Collaborative review workflows
- Formal ontology mappings
- Knowledge graphs

Future revisions should preserve backwards compatibility whenever practical.

---

# Related Documents

- ../COMMON_RESOURCE_SPECIFICATION.md
- ../API_DESIGN_GUIDELINES.md
- ../RESOURCES.md
- ../../architecture/domain/KNOWLEDGE.md
- ../../adr/ADR-0002-VERSIONED_KNOWLEDGE.md