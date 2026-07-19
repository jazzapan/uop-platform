# Components

> This document describes the major architectural components of the Urban Observation Platform (UOP), their responsibilities and interactions.

---

# Purpose

The purpose of this document is to define the logical components that together form the UOP platform.

Each component has a clearly defined responsibility and communicates with other components through well-defined interfaces.

A component should have one primary responsibility.

---

# Component Overview

The platform consists of the following major components.

```
+---------------------------+
| Mobile Application        |
+---------------------------+
            │
            ▼
+---------------------------+
| Web Application           |
+---------------------------+
            │
            ▼
+---------------------------+
| API                       |
+---------------------------+
            │
            ▼
+---------------------------+
| Domain Services           |
+---------------------------+
            │
            ▼
+---------------------------+
| Processing Services       |
+---------------------------+
            │
            ▼
+---------------------------+
| Data Storage              |
+---------------------------+
```

---

# Mobile Application

## Purpose

The Mobile Application enables users to collect observations in the field.

## Responsibilities

- Capture photographs
- Record geographic position
- Collect metadata
- Create observations
- Upload observations
- Support offline operation
- Synchronise pending observations

## Does Not

- Perform OCR
- Execute analysis
- Store permanent data
- Generate knowledge

---

# Web Application

## Purpose

The Web Application provides access to observations, knowledge and analysis through a browser.

## Responsibilities

- Search observations
- Browse maps
- Display images
- Review knowledge
- Perform administrative tasks
- Visualise analytical results

## Does Not

- Store observations directly
- Execute processing
- Access the database directly

---

# API

## Purpose

The API provides the public interface to the platform.

## Responsibilities

- Authentication
- Authorisation
- Validation
- CRUD operations
- Search
- File upload
- API versioning

## Does Not

- Execute long-running processing
- Perform analysis
- Store files directly

---

# Domain Services

## Purpose

Domain Services implement the business capabilities of the platform.

The initial services are:

- Observation Service
- Knowledge Service
- Place Object Service
- Analysis Service

## Responsibilities

- Enforce domain rules
- Coordinate persistence
- Validate business operations
- Maintain relationships between domain objects

## Does Not

- Handle user interface concerns
- Execute infrastructure tasks

---

# Processing Services

## Purpose

Processing Services generate knowledge from observations.

## Responsibilities

- OCR
- Classification
- Metadata extraction
- Human review workflows
- Future processors

Processing Services may operate asynchronously.

## Does Not

- Modify observations
- Provide user interfaces

---

# Database

## Purpose

The database stores structured platform data.

## Stores

- Observations
- Knowledge
- Relations
- Place Objects
- Analysis metadata
- Users
- Configuration

## Does Not

- Store original image files
- Execute business logic

---

# Object Storage

## Purpose

Object Storage stores binary objects.

Examples include:

- Images
- Attachments
- Future media

Metadata remains in the database.

---

# Search

## Purpose

Provides efficient querying of platform data.

Search may support:

- Full text
- Geographic queries
- Temporal queries
- Object lookup
- Tag lookup

The implementation technology is independent of the domain model.

---

# Authentication

## Purpose

Authenticate users and systems.

Responsibilities include:

- Login
- Session management
- API tokens
- Identity verification

---

# Authorisation

## Purpose

Determine what authenticated users may access.

Responsibilities include:

- Role evaluation
- Permission checks
- Access policies

Authorisation decisions should be enforced consistently throughout the platform.

---

# Logging

## Purpose

Provide operational visibility.

Examples include:

- API requests
- Errors
- Processing events
- Security events
- Audit events

---

# Monitoring

## Purpose

Provide operational health information.

Typical metrics include:

- Response times
- Queue length
- Processing throughput
- Storage utilisation
- Error rates

---

# Component Relationships

```
Mobile App
        │
        ▼
API
        │
        ▼
Domain Services
        │
        ├─────────────► Database
        │
        ├─────────────► Object Storage
        │
        ▼
Processing Services
        │
        ▼
Knowledge
        │
        ▼
Analysis
```

---

# Component Independence

Each component should:

- Have a clearly defined responsibility
- Be independently testable
- Be replaceable where practical
- Expose stable interfaces
- Minimise dependencies

---

# Future Components

The architecture allows future introduction of additional components such as:

- Notification Service
- Machine Learning Service
- Reporting Service
- Plugin Framework
- External Data Connectors

These additions should not require changes to the core domain model.

---

# Related Documents

- REFERENCE_ARCHITECTURE.md
- DATAFLOW.md
- STORAGE.md
- SECURITY.md
- DEPLOYMENT.md
- ../domain/DOMAIN_MODEL.md
