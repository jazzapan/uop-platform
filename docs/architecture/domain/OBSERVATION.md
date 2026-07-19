# Observation

> The Observation is the fundamental domain object of the Urban Observation Platform.

---

# Purpose

An Observation represents an immutable record of something observed at a specific place and time.

The Observation is the foundation of the entire platform.

Every other domain object either:

- belongs to an Observation,
- references an Observation,
- or derives information from one or more Observations.

---

# Definition

An Observation records **what was observed**, **where**, **when**, and **by whom or what**.

It intentionally avoids storing interpretations.

Interpretations belong to the Knowledge domain.

---

# Design Principles

An Observation shall be:

- Immutable
- Traceable
- Self-contained
- Globally identifiable
- Independent of processing

---

# Observation Lifecycle

```
Observed
    │
    ▼
Recorded
    │
    ▼
Stored
    │
    ▼
Available
    │
    ▼
Processed
    │
    ▼
Archived
```

Only the lifecycle state changes.

The recorded information never changes.

---

# Attributes

## Identity

Every Observation has a globally unique identifier.

Example

```
ObservationId
```

The identifier never changes.

---

## Timestamp

The Observation records when it was created.

Possible timestamps include:

- Observation Time
- Upload Time
- Processing Time

Only Observation Time belongs to the Observation itself.

---

## Position

Every Observation should contain a geographical position.

Possible sources include:

- GPS
- EXIF metadata
- User-selected map position

The source shall always be recorded.

---

## Images

One Observation may contain one or more images.

Images are immutable.

Images belong to the Observation.

---

## Metadata

Metadata may include:

- Device information
- Camera orientation
- EXIF data
- Application version
- Observer identifier
- Accuracy estimates

Metadata is preserved exactly as collected.

---

# What an Observation Does NOT Contain

An Observation never stores:

- OCR results
- AI classifications
- Similarity scores
- Tags
- Categories
- Relationships
- Analytical results

These belong elsewhere in the domain.

---

# Immutability

After an Observation has been stored:

- Images cannot be replaced.
- Position cannot be edited.
- Metadata cannot be modified.
- Timestamp cannot change.

If new information becomes available, it is stored as Knowledge.

---

# Versioning

Observations are never versioned.

There is only one version.

Knowledge may evolve.

Observations do not.

---

# Relationships

An Observation may reference:

- Position
- Images
- Place Objects

Other domain objects reference the Observation.

Examples:

Knowledge → Observation

Analysis → Observation

Relation → Observation

---

# Validation Rules

A valid Observation shall contain:

- Identifier
- Timestamp
- Position
- At least one image

Optional information may be absent.

---

# Quality

An Observation may receive quality indicators.

Examples:

- GPS accuracy
- Image resolution
- Blur estimation
- Completeness score

These indicators never modify the Observation itself.

---

# Traceability

Every Observation should answer:

- Who created it?
- When was it created?
- Where was it created?
- Which device created it?
- Which images belong to it?

These answers should remain available throughout the lifetime of the platform.

---

# Security

Observations may contain sensitive information.

Access control should therefore be applied at the API level.

The Observation itself remains immutable regardless of permissions.

---

# Domain Constraints

The following constraints always apply.

- One identifier.
- One observation time.
- At least one image.
- One recorded location.
- Immutable after storage.

---

# Architectural Significance

Observation is the Aggregate Root of the UOP domain.

All processing originates from Observations.

No processor may modify an Observation.

Processors only generate additional knowledge.

---

# Related Documents

- DOMAIN_MODEL.md
- KNOWLEDGE.md
- PLACE_OBJECT.md
- PROCESSORS.md
- ADR-0001-Immutable-Observations.md
