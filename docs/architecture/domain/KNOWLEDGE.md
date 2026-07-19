# Knowledge

> Knowledge represents information derived from one or more observations.

---

# Purpose

Knowledge captures interpretations, classifications and conclusions that are generated from observations.

Unlike observations, knowledge is expected to evolve over time as new information becomes available or existing information is refined.

Knowledge enables the Urban Observation Platform (UOP) to transform raw observations into searchable, analysable and reusable information.

---

# Definition

Knowledge is information that has been created by interpreting one or more observations.

Knowledge may originate from:

- Automated processing
- Artificial intelligence
- Optical Character Recognition (OCR)
- Human review
- External data sources

Knowledge never replaces or modifies the original observation.

---

# Characteristics

Knowledge is:

- Derived
- Versioned
- Traceable
- Reproducible
- Extendable

Knowledge is not immutable.

New versions may replace earlier interpretations while preserving the complete history.

---

# Sources

Knowledge may reference one or more observations.

Examples include:

- A single observation containing one tag.
- Multiple observations documenting the same graffiti over time.
- Several observations that together identify a recurring pattern.

Every knowledge object shall maintain references to its source observations.

---

# Types of Knowledge

Typical knowledge objects include:

- Extracted text
- Detected symbols
- Language identification
- Classification
- Confidence score
- Human annotations
- Entity recognition
- Relationships

The platform shall allow additional knowledge types to be introduced without changing the core observation model.

---

# Lifecycle

Knowledge follows an evolutionary lifecycle.

```
Created
    │
    ▼
Validated
    │
    ▼
Published
    │
    ▼
Superseded
    │
    ▼
Archived
```

Earlier versions remain available for traceability.

---

# Versioning

Every knowledge object shall have a version identifier.

A new version shall be created whenever:

- Interpretation changes
- OCR results improve
- AI models are updated
- Human review modifies previous conclusions

No previous version shall be deleted.

---

# Traceability

Every knowledge object shall answer:

- Which observations were used?
- Which processor created it?
- Which processor version created it?
- When was it created?
- Has it been reviewed by a human?

This information enables reproducibility and auditing.

---

# Confidence

Knowledge may include confidence values.

Confidence values indicate the certainty of the interpretation.

Confidence values do not determine truth.

Human review may confirm or reject automated results regardless of confidence.

---

# Human Review

Knowledge may be reviewed by authorised users.

Human review may:

- Confirm
- Correct
- Reject
- Extend

Human review creates a new version of the knowledge object.

The original version remains available.

---

# Storage

Knowledge is stored independently from observations.

This separation allows knowledge to evolve without modifying historical observations.

---

# Relationships

Knowledge may reference:

- Observations
- Place Objects
- Other Knowledge
- Analyses

Relationships shall always be explicit.

---

# Domain Rules

The following rules apply:

- Knowledge shall reference at least one observation.
- Knowledge shall be versioned.
- Knowledge shall be traceable.
- Knowledge shall never modify observations.
- Knowledge may be replaced by newer versions.

---

# Related Documents

- DOMAIN_MODEL.md
- OBSERVATION.md
- PROCESSORS.md
- RELATIONS.md
- ANALYSIS.md
