# Storage

> This document describes the storage architecture of the Urban Observation Platform (UOP).

---

# Purpose

The purpose of the storage architecture is to define how information is stored, organised and managed within the platform.

The storage architecture separates structured data from binary data and allows each type of information to be managed according to its characteristics.

---

# Objectives

The storage architecture shall:

- Preserve observations permanently
- Support immutable observations
- Enable versioned knowledge
- Store large image collections efficiently
- Support geographic queries
- Support future scalability
- Minimise operational cost
- Avoid vendor lock-in

---

# Storage Overview

The platform stores several categories of information.

```
+--------------------------------------+
|           Structured Data            |
|--------------------------------------|
| Observations                         |
| Knowledge                            |
| Relations                            |
| Place Objects                        |
| Analysis Metadata                    |
| Users                                |
| Configuration                        |
+--------------------------------------+

                │

                ▼

+--------------------------------------+
|            Binary Storage            |
|--------------------------------------|
| Images                               |
| Attachments                          |
| Future Media                         |
+--------------------------------------+
```

---

# Structured Data

Structured data consists of information that is queried, filtered and related.

Examples include:

- Observations
- Knowledge
- Relations
- Place Objects
- Analysis definitions
- User accounts
- System configuration

Structured data shall support:

- Transactions
- Referential integrity
- Geographic queries
- Versioning
- Auditing

---

# Binary Data

Binary storage contains large objects that should not be embedded in the primary database.

Examples include:

- Photographs
- Image thumbnails
- Future video files
- Future audio files

Binary objects are referenced by structured records.

---

# Observation Storage

Each Observation stores:

- Identifier
- Timestamp
- Geographic position
- Metadata
- References to associated images

Observations are immutable once stored.

---

# Knowledge Storage

Knowledge is stored independently from observations.

Each Knowledge object contains:

- Identifier
- Version
- Source references
- Processor information
- Confidence values
- Derived information

Historical versions may be retained.

---

# Place Object Storage

Place Objects are stored independently from observations.

Typical information includes:

- Identifier
- Type
- Geographic representation
- Status
- Optional descriptive attributes

Observations reference Place Objects without duplicating their information.

---

# Relation Storage

Relations are stored explicitly.

Each relation includes:

- Identifier
- Source object
- Target object
- Relation type
- Timestamp
- Provenance information

Explicit storage improves traceability and analytical capabilities.

---

# Analysis Storage

Analysis storage contains:

- Analysis definitions
- Parameters
- Processing metadata
- References to source data
- Generated summaries

Large generated datasets may be stored separately if required.

---

# Geographic Data

The platform supports geographic information as a first-class capability.

Geographic information may include:

- Coordinates
- Bounding boxes
- Areas
- Lines
- Polygons

The storage solution should support efficient spatial indexing and geographic queries.

---

# Search

Search capabilities should support queries based on:

- Free text
- Geographic area
- Time period
- Observation identifier
- Place Object
- Knowledge
- Relation

Search indexes supplement, but do not replace, the primary data store.

---

# Backup

The storage architecture shall support regular backup of:

- Structured data
- Binary objects
- Configuration
- System metadata

Backup procedures should be documented and regularly verified.

---

# Retention

Observations represent historical records.

Unless required by legal or administrative policies, observations should not be deleted.

Knowledge may evolve through versioning rather than replacement.

---

# Scalability

The storage architecture should support gradual growth.

Small deployments may operate on a single server.

Larger deployments may separate:

- Database
- Object storage
- Search index
- Backup storage

This separation should not affect the domain model.

---

# Security

Stored information shall be protected through appropriate security measures.

Examples include:

- Authentication
- Authorisation
- Encryption in transit
- Access logging
- Backup protection

Security policies are described in SECURITY.md.

---

# Design Principles

The storage architecture follows these principles:

- Observations are immutable.
- Knowledge is versioned.
- Binary data is stored separately from structured data.
- Geographic information is a core capability.
- Storage technology should remain replaceable where practical.

---

# Related Documents

- REFERENCE_ARCHITECTURE.md
- COMPONENTS.md
- DATAFLOW.md
- SECURITY.md
- DEPLOYMENT.md
- ../domain/OBSERVATION.md
- ../domain/KNOWLEDGE.md
- ../domain/PLACE_OBJECT.md
