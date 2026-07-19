# ADR-0002: Versioned Knowledge

| Status | Accepted |
|----------|----------|
| Date | 2026-07-19 |
| Decision Makers | UOP Project |
| Supersedes | None |
| Superseded By | None |

---

# Context

Knowledge within the Urban Observation Platform (UOP) is derived from observations through automated processors, human interpretation or analytical methods.

Unlike observations, knowledge is expected to evolve over time.

Examples include:

- Improved OCR results
- Better image classification
- Corrected human interpretation
- New processing algorithms
- Additional contextual information

Replacing previous knowledge would remove historical context and reduce the reproducibility of analytical results.

---

# Decision

Knowledge shall be versioned.

New or improved interpretations shall create new versions rather than modifying or replacing existing knowledge.

Each Knowledge object shall include sufficient metadata to identify:

- Its version
- Its origin
- The processor or reviewer that created it
- The time of creation
- The observations from which it was derived

Previous versions may be retained for historical reference, auditing and reproducibility.

---

# Consequences

## Positive

- Preserves historical interpretations.
- Enables reproducible analysis.
- Supports continuous improvement of processors.
- Allows human review without losing previous results.
- Simplifies auditing and debugging.

## Negative

- Storage requirements increase over time.
- Consumers may need to determine which version is considered current.
- Version management introduces additional implementation complexity.

These trade-offs are acceptable because knowledge is inherently evolutionary.

---

# Alternatives Considered

## Replace Existing Knowledge

Overwrite previous knowledge whenever improved results become available.

**Rejected**

Reason:

Replacing previous knowledge removes historical context and makes it impossible to reproduce earlier analytical results.

---

## Mutable Knowledge Objects

Allow direct editing of existing Knowledge objects.

**Rejected**

Reason:

This weakens traceability and makes it difficult to understand how knowledge has evolved over time.

---

# Rationale

Observations represent historical facts.

Knowledge represents interpretation.

Interpretation changes as:

- Algorithms improve
- Additional observations become available
- Human understanding evolves

Versioning acknowledges that multiple valid interpretations may exist over time while preserving a complete history.

---

# Impact

This decision affects:

- Knowledge lifecycle
- Processing Services
- Analysis
- Storage Architecture
- Search
- API design

Future processing components shall create new knowledge versions rather than modifying existing ones.

---

# Related Documents

- ../architecture/domain/KNOWLEDGE.md
- ../architecture/domain/PROCESSORS.md
- ../architecture/domain/ANALYSIS.md
- ../architecture/solution/STORAGE.md
- ADR-0001-IMMUTABLE_OBSERVATIONS.md
