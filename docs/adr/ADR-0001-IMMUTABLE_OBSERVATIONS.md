# ADR-0001: Immutable Observations

| Status | Accepted |
|----------|----------|
| Date | 2026-07-19 |
| Decision Makers | UOP Project |
| Supersedes | None |
| Superseded By | None |

---

# Context

The Urban Observation Platform (UOP) is designed to preserve observations of the physical environment over time.

An observation represents a historical record captured at a specific place and time. Once recorded, it becomes evidence of what was observed.

As processing algorithms improve or human interpretation changes, the understanding of an observation may evolve. However, the original observation should remain unchanged.

Allowing observations to be modified after storage would reduce traceability, complicate auditing and make analytical results difficult to reproduce.

---

# Decision

Observations are immutable once successfully stored.

The platform shall not permit modifications to the content of an existing observation.

If an error is discovered after storage, it shall be addressed by creating additional information rather than altering the original observation.

Derived information shall be represented as Knowledge objects linked to the original Observation.

---

# Consequences

## Positive

- Preserves historical accuracy.
- Enables complete traceability.
- Simplifies auditing.
- Supports reproducible processing.
- Allows multiple interpretations over time.
- Reduces the risk of accidental data corruption.

## Negative

- Incorrect observations cannot simply be edited.
- Additional mechanisms are required to handle corrections and annotations.
- Storage requirements may increase over time.

These trade-offs are considered acceptable because preserving historical integrity is a primary objective of UOP.

---

# Alternatives Considered

## Editable Observations

Allow users or administrators to update observations after creation.

**Rejected**

Reason:

Historical evidence should not change once recorded.

---

## Soft Updates

Store only the latest version of an observation while retaining an internal history.

**Rejected**

Reason:

This introduces unnecessary complexity and weakens the conceptual distinction between observations and knowledge.

---

# Rationale

The distinction between Observation and Knowledge is a foundational concept within UOP.

Observations represent facts as they were recorded.

Knowledge represents interpretations that may evolve over time.

Keeping these concepts separate results in a simpler, more traceable and more maintainable architecture.

---

# Impact

This decision affects:

- Domain Model
- Observation lifecycle
- Knowledge model
- Processing architecture
- API design
- Storage architecture

Future architectural decisions shall remain consistent with this principle.

---

# Related Documents

- ../architecture/domain/OBSERVATION.md
- ../architecture/domain/KNOWLEDGE.md
- ../architecture/solution/STORAGE.md
- ../philosophy/PROJECT_PHILOSOPHY.md
