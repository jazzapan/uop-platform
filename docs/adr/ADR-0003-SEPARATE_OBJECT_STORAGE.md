# ADR-0003: Separate Object Storage

| Status | Accepted |
|----------|----------|
| Date | 2026-07-19 |
| Decision Makers | UOP Project |
| Supersedes | None |
| Superseded By | None |

---

# Context

The Urban Observation Platform (UOP) stores two fundamentally different categories of information.

Structured domain data includes:

- Observations
- Knowledge
- Place Objects
- Relations
- Analysis metadata

Binary data includes:

- Images
- Future video
- Future audio
- Attachments

These categories have different storage, performance and lifecycle characteristics.

Storing large binary objects directly within the primary relational database increases storage requirements, backup size and database maintenance complexity.

---

# Decision

Binary objects shall be stored separately from structured domain data.

The relational database stores metadata and references to binary objects.

Binary content is stored in a dedicated object storage solution.

The choice of object storage implementation is an infrastructure concern and shall not affect the domain model.

---

# Consequences

## Positive

- Improves database performance.
- Simplifies backup strategies.
- Enables efficient storage of large media collections.
- Supports independent scaling of database and media storage.
- Reduces database growth caused by binary data.
- Allows storage technologies to evolve independently.

## Negative

- Requires coordination between the database and object storage.
- Introduces an additional infrastructure component.
- Orphaned objects must be managed through operational procedures.

These trade-offs are considered acceptable because they provide a cleaner separation of responsibilities and improve long-term maintainability.

---

# Alternatives Considered

## Store Binary Objects in the Database

Store images and other media directly as binary large objects (BLOBs) in the relational database.

**Rejected**

Reason:

This couples structured and binary storage, increases operational complexity and reduces flexibility.

---

## Store Files on the Local File System

Store media files directly on the application server.

**Rejected**

Reason:

This approach complicates scaling, backup, migration and multi-instance deployments.

---

# Rationale

Structured data and binary media have different operational characteristics.

The domain model should describe observations and their relationships without depending on how media files are physically stored.

Separating these concerns results in a cleaner architecture and allows storage technologies to evolve independently of the domain model.

---

# Impact

This decision affects:

- Storage Architecture
- Deployment Architecture
- Backup Strategy
- Processing Services
- API Design

Future storage implementations shall preserve this separation regardless of the underlying storage technology.

---

# Related Documents

- ../architecture/solution/STORAGE.md
- ../architecture/solution/DEPLOYMENT.md
- ../architecture/solution/REFERENCE_ARCHITECTURE.md
- ../architecture/domain/OBSERVATION.md
- ADR-0001-IMMUTABLE_OBSERVATIONS.md
- ADR-0002-VERSIONED_KNOWLEDGE.md
