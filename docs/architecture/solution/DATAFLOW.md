# Data Flow

> This document describes how data moves through the Urban Observation Platform (UOP).

---

# Purpose

The purpose of this document is to describe the logical flow of information through the platform, from the moment an observation is created until it becomes searchable and available for analysis.

The data flow is independent of implementation technology and focuses on the responsibilities of each architectural component.

---

# Overview

The platform processes information through a sequence of stages.

```
Observation Capture
        │
        ▼
Observation Upload
        │
        ▼
Observation Validation
        │
        ▼
Observation Storage
        │
        ▼
Knowledge Processing
        │
        ▼
Knowledge Storage
        │
        ▼
Search Indexing
        │
        ▼
Analysis
        │
        ▼
Presentation
```

Each stage has a clearly defined responsibility.

---

# Stage 1 – Observation Capture

The process begins when a user creates an observation using the mobile application.

Typical information collected includes:

- One or more photographs
- Geographic position
- Timestamp
- Device metadata
- User-provided metadata (optional)

The observation is created locally before being transmitted.

---

# Stage 2 – Observation Upload

The client uploads the observation to the platform.

The upload includes:

- Observation metadata
- Image files
- Geographic information

The upload process should support interrupted network connections and retry mechanisms.

---

# Stage 3 – Observation Validation

Before an observation is accepted, the platform validates:

- Required fields
- File integrity
- Metadata format
- Geographic coordinates
- Authentication and authorisation

Validation failures are reported to the client.

Invalid observations are not persisted.

---

# Stage 4 – Observation Storage

Once validated, the observation is stored.

Storage includes:

- Observation record
- Image references
- Metadata
- Geographic information

After storage, the observation becomes immutable.

---

# Stage 5 – Knowledge Processing

Stored observations become available for processing.

Processors may perform tasks such as:

- OCR
- Image classification
- Metadata extraction
- Language detection
- Human review preparation

Processors create Knowledge objects without modifying observations.

Processing may occur asynchronously.

---

# Stage 6 – Knowledge Storage

Knowledge produced by processors is stored independently from observations.

Each Knowledge object includes:

- Source references
- Processing metadata
- Version information
- Confidence values

Knowledge remains fully traceable to its originating observations.

---

# Stage 7 – Search Indexing

Searchable information is indexed.

Typical indexed content includes:

- Extracted text
- Geographic location
- Observation metadata
- Place Objects
- Knowledge
- Analysis metadata

Indexing improves retrieval performance without replacing the primary data store.

---

# Stage 8 – Analysis

Analysis processes collections of observations and knowledge.

Examples include:

- Geographic clustering
- Temporal analysis
- Trend detection
- Statistical summaries

Analytical results do not modify source data.

---

# Stage 9 – Presentation

Users access information through client applications.

Presentation may include:

- Maps
- Search results
- Observation details
- Image galleries
- Dashboards
- Reports

Presentation components consume platform services without direct access to underlying storage.

---

# Reprocessing

Previously stored observations may be processed again.

Typical reasons include:

- New processors
- Improved OCR
- Updated classification models
- Human review
- Algorithm improvements

Reprocessing generates new Knowledge objects while preserving previous results.

---

# Error Handling

Errors may occur at any stage.

The platform should:

- Record failures
- Preserve successful observations
- Support retry mechanisms
- Avoid partial updates
- Provide diagnostic information

Errors in processing shall not affect stored observations.

---

# Traceability

Every stage shall record sufficient information to answer:

- What happened?
- When did it happen?
- Which component performed the operation?
- Which data was used?
- What was produced?

This supports auditing, debugging and reproducibility.

---

# Design Principles

The data flow follows these principles:

- Observations are immutable.
- Knowledge is derived.
- Processing is independent.
- Failures are isolated.
- Operations are traceable.
- Components communicate through defined interfaces.

---

# Related Documents

- REFERENCE_ARCHITECTURE.md
- COMPONENTS.md
- STORAGE.md
- SECURITY.md
- ../domain/OBSERVATION.md
- ../domain/KNOWLEDGE.md
- ../domain/PROCESSORS.md
