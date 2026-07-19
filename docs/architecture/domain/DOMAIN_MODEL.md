# UOP Domain Model

> The domain model defines the core concepts of the Urban Observation Platform (UOP).

---

# Purpose

The purpose of the domain model is to describe the problem domain independently of implementation technology.

The domain model is considered the most stable part of the architecture.

Programming languages, databases and frameworks may change over time.

The domain model should remain consistent.

---

# Core Principle

The central concept of UOP is the **Observation**.

Everything else either:

- describes an observation,
- derives knowledge from an observation,
- relates observations to each other,
- or analyses collections of observations.

The architecture therefore grows outward from the Observation.

---

# Domain Overview

```text
                    Observation
                         │
         ┌───────────────┼───────────────┐
         │               │               │
      Position         Image          Metadata
         │
         │
         ▼
     Place Object
         │
         ▼
      Knowledge
         │
         ▼
      Relations
         │
         ▼
      Analysis
```

---

# Primary Domain Objects

The domain consists of seven primary entities.

## Observation

Represents an immutable record of something observed at a specific place and time.

The Observation is the foundation of the entire platform.

---

## Image

A photograph associated with an Observation.

Multiple images may belong to the same Observation.

Images are immutable.

---

## Position

Represents the geographical location of an Observation.

A Position may originate from:

- GPS
- EXIF metadata
- User-selected map location
- Administrative correction

The source of the position should always be recorded.

---

## Knowledge

Knowledge is information derived from one or more observations.

Knowledge may originate from:

- OCR
- AI classification
- Human review
- External systems

Knowledge is versioned.

Knowledge may change.

---

## Place Object

Represents a persistent physical object.

Examples include:

- electrical cabinet
- bridge
- tunnel entrance
- station wall
- traffic sign
- building facade

Observations may reference the same Place Object over time.

---

## Relation

Represents a documented relationship between domain objects.

Examples include:

- Observation references Place Object
- Knowledge derived from Observation
- Similar observations
- Temporal sequence

Relations should always be explicit.

---

## Analysis

Represents aggregated information generated from multiple observations.

Examples include:

- heat maps
- trend analysis
- temporal changes
- geographic clusters

Analysis never modifies observations.

---

# Domain Rules

The following rules always apply.

## Rule 1

Observations are immutable.

---

## Rule 2

Knowledge may evolve.

---

## Rule 3

Analysis never changes source data.

---

## Rule 4

Relations are explicit.

---

## Rule 5

Every derived result should be traceable to its source.

---

# Aggregate Root

Observation is the Aggregate Root of the domain.

Other entities exist either because they belong to an Observation or because they reference one or more Observations.

This simplifies reasoning about ownership and lifecycle.

---

# Domain Evolution

New concepts should only be introduced when they represent a genuine domain concept.

Technical implementation details do not belong in the domain model.

---

# Related Documents

- OBSERVATION.md
- KNOWLEDGE.md
- PLACE_OBJECT.md
- RELATIONS.md
- ANALYSIS.md
- PROCESSORS.md
- DOMAIN_GLOSSARY.md
