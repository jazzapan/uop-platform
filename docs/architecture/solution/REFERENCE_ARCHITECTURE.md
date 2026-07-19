# UOP Reference Architecture

> The Reference Architecture defines the high-level structure of the Urban Observation Platform (UOP).

---

# Purpose

The purpose of the Reference Architecture is to describe the major architectural building blocks of the Urban Observation Platform and the relationships between them.

It provides a common understanding of the platform before individual components and services are described in detail.

This document intentionally focuses on architecture rather than implementation.

---

# Architectural Goals

The reference architecture is designed to:

- Support long-term maintainability
- Preserve immutable observations
- Enable independent processing
- Scale individual components independently
- Minimise operational cost
- Support both small and large deployments

---

# Architectural Overview

The platform consists of six major layers.

```
+------------------------------------------------------+
|                  Client Applications                 |
|------------------------------------------------------|
| Mobile Application                                   |
| Web Application                                      |
| External Clients                                     |
+------------------------------------------------------+
                      │
                      ▼
+------------------------------------------------------+
|                     API Layer                        |
|------------------------------------------------------|
| REST API                                             |
| Authentication                                       |
| Authorisation                                        |
| Search                                               |
+------------------------------------------------------+
                      │
                      ▼
+------------------------------------------------------+
|                  Domain Services                     |
|------------------------------------------------------|
| Observation Service                                  |
| Knowledge Service                                    |
| Place Object Service                                 |
| Analysis Service                                     |
+------------------------------------------------------+
                      │
                      ▼
+------------------------------------------------------+
|                 Processing Layer                     |
|------------------------------------------------------|
| OCR                                                  |
| Image Classification                                 |
| Human Review                                         |
| Future Processors                                    |
+------------------------------------------------------+
                      │
                      ▼
+------------------------------------------------------+
|                  Persistence Layer                   |
|------------------------------------------------------|
| PostgreSQL                                           |
| PostGIS                                              |
| Object Storage                                       |
+------------------------------------------------------+
                      │
                      ▼
+------------------------------------------------------+
|                Infrastructure Layer                  |
|------------------------------------------------------|
| Containers                                            |
| Monitoring                                            |
| Logging                                               |
| Backup                                                |
+------------------------------------------------------+
```

---

# Architectural Principles

The platform follows several architectural principles.

- Separation of concerns
- Loose coupling
- High cohesion
- Immutable observations
- Versioned knowledge
- Explicit relationships
- API-first design
- Modular processing

---

# Major Components

The reference architecture contains the following major components.

## Client Applications

Responsible for collecting observations and presenting information to users.

Examples:

- Mobile application
- Web application
- Administrative interface
- External integrations

---

## API Layer

Provides the public interface to the platform.

Responsibilities include:

- Authentication
- Authorisation
- Validation
- Search
- Data access

Clients never communicate directly with the database.

---

## Domain Services

Domain services implement the business capabilities of the platform.

Responsibilities include:

- Observation management
- Knowledge management
- Place Object management
- Analysis management

The domain services enforce the domain rules described in the Domain Architecture.

---

## Processing Layer

Responsible for generating knowledge from observations.

Processors operate independently from client applications.

Processing may occur asynchronously.

Processors never modify observations.

---

## Persistence Layer

Responsible for long-term storage.

The persistence layer stores:

- Observations
- Knowledge
- Relations
- Place Objects
- Analysis results
- Images

The persistence layer is independent of processing.

---

## Infrastructure Layer

Provides the technical foundation for the platform.

Examples include:

- Container runtime
- Logging
- Monitoring
- Backup
- Reverse proxy
- Object storage

Infrastructure should remain replaceable.

---

# Communication

Communication between architectural layers occurs through clearly defined interfaces.

The preferred communication pattern is:

```
Client

↓

API

↓

Domain Services

↓

Persistence
```

Processing components communicate through the same public interfaces where appropriate.

---

# Scalability

The architecture supports independent scaling of:

- API
- Processing
- Storage
- Search

Small deployments may execute all components on a single host.

Larger deployments may distribute components across multiple servers.

---

# Deployment

The reference architecture supports multiple deployment models.

Examples include:

- Local development
- Single server
- Virtual machine
- Docker Compose
- Kubernetes (future)

The deployment model does not affect the domain architecture.

---

# Security

Security is enforced primarily at the API boundary.

Examples include:

- Authentication
- Authorisation
- Input validation
- Audit logging

Security responsibilities are described in detail in `SECURITY.md`.

---

# Extensibility

The platform is designed to support future extensions.

Examples include:

- New processors
- Alternative storage providers
- Additional client applications
- External integrations
- Plugin modules

New functionality should be introduced without requiring changes to the core domain model.

---

# Related Documents

- COMPONENTS.md
- DATAFLOW.md
- STORAGE.md
- SECURITY.md
- DEPLOYMENT.md
- ../domain/DOMAIN_MODEL.md
