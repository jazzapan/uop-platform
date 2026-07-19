# Processor Resource

> This document defines the Processor resource within the Urban Observation Platform (UOP).

A Processor represents an actor capable of producing, validating or transforming information within the platform.

Processors provide provenance by identifying how derived resources such as Knowledge and Analysis were produced.

This document is normative. Implementations claiming conformance with the UOP Specification shall satisfy the requirements defined herein.

---

# Purpose

The Processor resource identifies the origin of derived information.

Processors improve:

- Traceability
- Reproducibility
- Auditability
- Transparency

Processors are not limited to software.

They may represent:

- Human reviewers
- AI models
- Machine learning systems
- OCR engines
- Computer vision services
- External systems
- Automated workflows

---

# Scope

A Processor represents:

- A processing capability
- Processing metadata
- Version information
- Provenance information

A Processor does not represent:

- Individual processing executions
- Jobs
- Tasks
- Queues

Execution details belong to operational systems rather than the platform specification.

---

# Resource Definition

A Processor is a persistent domain resource.

Processors identify the capability responsible for producing derived information.

A Processor may produce multiple Knowledge and Analysis resources over its lifetime.

---

# Resource Representation

A Processor consists of:

- Processor identifier
- Name
- Type
- Version
- Status
- Metadata

The representation shall remain transport-independent.

---

# Required Properties

Every Processor MUST contain:

- Processor identifier
- Name
- Processor type
- Version
- Created timestamp

---

# Optional Properties

A Processor MAY include:

- Description
- Vendor
- Model identifier
- Configuration reference
- Documentation URI
- Tags
- Additional metadata

---

# Processor Types

Implementations SHOULD distinguish between processor categories.

Examples include:

- Human
- OCR
- Computer Vision
- Machine Learning
- Rule Engine
- External System
- Data Import
- Manual Review

Additional processor types MAY be introduced.

---

# Versioning

Processors SHALL support version identification.

Different versions of the same Processor represent different processing capabilities.

Historical Processor versions should remain available to preserve provenance.

---

# Relationships

A Processor may be referenced by:

- Knowledge
- Analysis

A Processor may also reference:

- Previous Processor versions
- External documentation
- Supporting configuration

Relationships shall be explicit.

---

# Lifecycle

The typical lifecycle is:

```
Registered

↓

Available

↓

Deprecated

↓

Retired
```

Retired Processors should remain available for historical provenance.

---

# Validation Rules

Implementations shall validate:

- Identifier uniqueness
- Version identifier
- Processor type
- Required properties

Validation failures shall prevent registration.

---

# Security Considerations

Implementations should protect:

- Sensitive configuration
- Proprietary model information
- Credentials
- Internal processing metadata

Confidential implementation details should not be exposed through the public API.

---

# Conformance Requirements

A conforming implementation:

MUST

- provide stable identifiers;
- identify processor versions;
- preserve historical provenance.

SHOULD

- categorise processors;
- document processor capabilities;
- support processor retirement.

MAY

- expose implementation-specific metadata;
- reference external documentation;
- support custom processor categories.

---

# Example Representation

```json
{
  "processorId": "proc-vision-v2",
  "name": "Traffic Sign Detector",
  "type": "ComputerVision",
  "version": "2.3.1",
  "createdAt": "2026-07-19T18:20:00Z",
  "status": "Available"
}
```

The example is informative rather than normative.

---

# Future Evolution

Future versions may introduce:

- Capability descriptions
- Performance characteristics
- Certification metadata
- Benchmark results
- Model lineage

Future revisions should preserve backwards compatibility whenever practical.

---

# Related Documents

- ../COMMON_RESOURCE_SPECIFICATION.md
- ../API_DESIGN_GUIDELINES.md
- ../RESOURCES.md
- ../../architecture/domain/PROCESSORS.md
- resources/KNOWLEDGE.md
- resources/ANALYSIS.md