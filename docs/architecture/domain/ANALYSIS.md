# Analysis

> Analysis represents derived insights generated from collections of observations and knowledge.

---

# Purpose

The purpose of Analysis is to transform observations and knowledge into information that helps users understand patterns, trends and relationships.

Unlike individual observations, which describe specific events, an Analysis describes characteristics of a collection of observations.

Analysis never modifies source data.

---

# Definition

An Analysis is a derived result produced from one or more observations, knowledge objects or relations.

Analyses provide higher-level information that supports exploration, decision making and research.

Examples include:

- Geographic clustering
- Temporal trends
- Density maps
- Pattern detection
- Statistical summaries
- Relationship analysis

---

# Characteristics

An Analysis is:

- Derived
- Reproducible
- Traceable
- Versioned
- Non-destructive

Analyses may be regenerated whenever new observations become available or analytical methods improve.

---

# Inputs

An Analysis may use one or more of the following inputs:

- Observations
- Knowledge
- Relations
- Place Objects

The complete set of input data shall always be traceable.

---

# Outputs

An Analysis may produce:

- Maps
- Charts
- Reports
- Statistics
- Heat maps
- Timelines
- Graph structures
- Aggregated datasets

The presentation format is independent of the analytical result itself.

---

# Types of Analysis

The platform supports multiple categories of analysis.

## Geographic Analysis

Examines spatial distribution of observations.

Examples:

- Observation density
- Geographic clusters
- Hotspot identification
- Distribution maps

---

## Temporal Analysis

Examines how observations change over time.

Examples:

- Daily trends
- Seasonal variation
- Activity over time
- Persistence of markings

---

## Object Analysis

Examines Place Objects and their observation history.

Examples:

- Frequently observed objects
- Objects with recurring graffiti
- Objects with changing characteristics

---

## Knowledge Analysis

Examines derived knowledge.

Examples:

- Frequently occurring tags
- OCR accuracy
- Classification trends
- Human validation statistics

---

## Relationship Analysis

Examines explicit relations within the domain.

Examples:

- Connected observations
- Shared characteristics
- Similar markings
- Network analysis

---

# Lifecycle

An Analysis follows a lifecycle.

```
Created
    │
    ▼
Published
    │
    ▼
Updated
    │
    ▼
Archived
```

New analyses do not replace previous analytical results unless explicitly intended.

---

# Versioning

Every Analysis shall have a version identifier.

A new version may be created when:

- Input data changes
- Algorithms change
- Parameters change
- Processing methods improve

Historical versions may be retained for reproducibility.

---

# Traceability

Every Analysis shall document:

- Input observations
- Input knowledge
- Applied processing
- Parameters
- Software version
- Creation timestamp

This ensures analytical results can be reproduced.

---

# Scope

An Analysis may operate on:

- A single geographic area
- Multiple regions
- A municipality
- A country
- The complete dataset

The domain model places no restrictions on analytical scope.

---

# Performance

Analyses are computational processes.

They should normally execute independently of observation collection.

Long-running analyses should be performed asynchronously.

---

# Domain Rules

The following rules apply.

- Analyses never modify observations.
- Analyses never modify knowledge.
- Every analysis is reproducible.
- Every analysis is traceable.
- Every analysis has defined inputs.

---

# Examples

## Example 1

Generate a heat map showing observation density for a municipality.

---

## Example 2

Compare graffiti activity between two calendar years.

---

## Example 3

Identify Place Objects that have accumulated the highest number of observations.

---

## Example 4

Identify recurring tags within a defined geographic area.

---

# Related Documents

- DOMAIN_MODEL.md
- OBSERVATION.md
- KNOWLEDGE.md
- PLACE_OBJECT.md
- RELATIONS.md
- PROCESSORS.md
