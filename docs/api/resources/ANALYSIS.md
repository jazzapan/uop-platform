# Analysis Resource

> This document defines the Analysis resource within the Urban Observation Platform (UOP).

An Analysis represents derived insights produced from one or more platform resources. It aggregates, evaluates or interprets information to answer broader questions than those addressed by individual Knowledge resources.

Analysis is intended for higher-level reasoning, reporting and decision support.

This document is normative. Implementations claiming conformance with the UOP Specification shall satisfy the requirements defined herein.

---

# Purpose

The Analysis resource captures insights derived from collections of resources.

Unlike Knowledge, which describes an interpretation of specific observations, Analysis answers broader questions using multiple sources.

Examples include:

- Asset condition summaries
- Infrastructure risk assessments
- Temporal change detection
- Geographic trend analysis
- Statistical reports
- Network connectivity analysis

---

# Scope

An Analysis represents:

- A derived result
- Its methodology
- Supporting resources
- Output metrics
- Provenance

An Analysis does not replace or modify the resources from which it is derived.

---

# Resource Definition

An Analysis is a versioned domain resource.

It represents the result of applying one or more analytical methods to platform resources.

Multiple analyses may exist for the same subject using different methodologies.

---

# Resource Representation

An Analysis consists of:

- Analysis identifier
- Analysis type
- Version identifier
- Status
- Methodology
- Supporting resources
- Results
- Provenance

The representation shall remain transport-independent.

---

# Required Properties

Every Analysis MUST contain:

- Analysis identifier
- Analysis type
- Version identifier
- Created timestamp
- At least one supporting resource
- Provenance

---

# Optional Properties

An Analysis MAY include:

- Title
- Description
- Confidence
- Summary
- Metrics
- Attachments
- Tags
- External references
- Additional metadata

---

# Inputs

An Analysis may use any combination of supported resources.

Examples include:

- Observations
- Knowledge
- Place Objects
- Relations
- Previous Analyses

All inputs should be explicitly referenced.

---

# Outputs

An Analysis may produce:

- Scores
- Metrics
- Classifications
- Recommendations
- Reports
- Visualisations
- Derived datasets

The structure of outputs is implementation-specific.

---

# Provenance

Every Analysis SHALL record:

- The analytical method
- The producing Processor or user
- Input resources
- Execution time
- Creation timestamp

This enables reproducibility and auditing.

---

# Versioning

Analysis evolves through versioning.

A new version SHALL be created whenever:

- Input resources change.
- Analytical methods change.
- Results are corrected.
- New supporting evidence is incorporated.

Historical versions SHALL remain available.

---

# Relationships

An Analysis may reference:

- Observations
- Knowledge
- Place Objects
- Relations
- Processors
- Other Analyses

Relationships shall be explicit.

---

# Lifecycle

The typical lifecycle is:

```
Created

↓

Processing

↓

Validated

↓

Published

↓

Superseded

↓

Archived (optional)
```

Published analyses remain available for historical reference.

---

# Validation Rules

Implementations shall validate:

- Input resources
- Methodology
- Required properties
- Provenance
- Version consistency

Validation failures shall prevent publication.

---

# Security Considerations

Implementations should protect:

- Sensitive analytical results
- Restricted infrastructure assessments
- Confidential methodologies
- Internal metrics

Access control policies are implementation-specific.

---

# Conformance Requirements

A conforming implementation:

MUST

- provide stable identifiers;
- preserve version history;
- record provenance;
- reference supporting resources.

SHOULD

- document analytical methods;
- support confidence information;
- preserve reproducibility.

MAY

- support custom output formats;
- support implementation-specific metrics;
- support collaborative review workflows.

---

# Example Representation

```json
{
  "analysisId": "analysis-1048",
  "version": 2,
  "analysisType": "asset-condition-summary",
  "createdAt": "2026-07-19T17:15:00Z",
  "derivedFrom": [
    "know-8421",
    "know-8422",
    "know-8423"
  ],
  "processor": "condition-analysis-v1",
  "summary": {
    "overallCondition": "Fair",
    "confidence": 0.91
  }
}
```

The example is informative rather than normative.

---

# Future Evolution

Future versions may introduce:

- Distributed analyses
- Real-time analytical pipelines
- Predictive models
- Geospatial aggregation
- Simulation outputs

Future revisions should preserve backwards compatibility whenever practical.

---

# Related Documents

- ../COMMON_RESOURCE_SPECIFICATION.md
- ../API_DESIGN_GUIDELINES.md
- ../RESOURCES.md
- ../../architecture/domain/ANALYSIS.md
- ../../architecture/domain/KNOWLEDGE.md
- ../../adr/ADR-0002-VERSIONED_KNOWLEDGE.md