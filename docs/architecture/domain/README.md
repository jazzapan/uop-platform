# Domain Architecture

> The Domain Architecture defines the concepts that make up the Urban Observation Platform (UOP).

The domain model represents the business concepts of UOP independently of implementation technologies such as programming languages, databases or deployment environments.

It provides a common vocabulary and establishes the rules that govern how information is represented within the platform.

---

# Purpose

The purpose of the Domain Architecture is to describe:

- The core domain objects
- Their responsibilities
- Their relationships
- Their lifecycle
- The rules that govern the domain

The domain model should remain stable even as implementation technologies evolve.

---

# Domain Overview

The Urban Observation Platform is centred around four primary domain objects.

```
Observation
      │
      ▼
Knowledge
      │
      ▼
Analysis

Observation
      │
      ▼
Place Object
```

Supporting these concepts are:

- Relations
- Processors

Together they describe how observations are collected, interpreted and analysed.

---

# Domain Documents

## DOMAIN_MODEL.md

Provides an overview of the complete domain model and explains how the domain objects relate to one another.

This document should be read first.

---

## OBSERVATION.md

Defines the Observation entity.

An Observation represents an immutable record of something observed in the physical environment.

---

## KNOWLEDGE.md

Defines the Knowledge entity.

Knowledge is derived from observations and represents interpretations that may evolve over time.

---

## PLACE_OBJECT.md

Defines physical objects that exist in the observed environment.

Multiple observations may refer to the same Place Object.

---

## RELATIONS.md

Defines explicit relationships between domain objects.

Relations improve traceability and analytical capabilities while keeping domain objects independent.

---

## ANALYSIS.md

Defines how observations and knowledge are transformed into higher-level insights.

Analysis produces derived information without modifying source data.

---

## PROCESSORS.md

Describes logical processors that generate Knowledge from Observations.

Processors are independent, replaceable and fully traceable.

---

# Core Principles

The Domain Architecture is built upon a small number of fundamental principles.

- Observations are immutable.
- Knowledge is versioned.
- Processing creates new knowledge.
- Relationships are explicit.
- Analysis is derived from domain data.
- Domain concepts are independent of implementation technologies.

These principles are reinforced throughout the architecture and documented in the project's Architecture Decision Records (ADRs).

---

# Relationship to the Solution Architecture

The Domain Architecture defines **what** the platform is.

The Solution Architecture defines **how** those concepts are implemented.

Changes to the implementation should not require changes to the domain model unless the underlying business concepts themselves change.

---

# Recommended Reading Order

1. DOMAIN_MODEL.md
2. OBSERVATION.md
3. KNOWLEDGE.md
4. PLACE_OBJECT.md
5. RELATIONS.md
6. ANALYSIS.md
7. PROCESSORS.md

---

# Related Documentation

- `../README.md`
- `../solution/README.md`
- `../../glossary/Domain-Glossary.md`
- `../../adr/`