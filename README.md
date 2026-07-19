# Urban Observation Platform (UOP)

> An open source platform for collecting, preserving and analysing georeferenced observations.

> **Status:** Early Architecture (v0.3)

---

## Vision

Urban Observation Platform (UOP) is an open source platform for documenting, managing and analysing observations collected in the physical environment.

The initial reference implementation focuses on graffiti, tags, stickers and other visual markings found in public spaces.

The platform is intentionally designed around a generic observation model, allowing future use cases without changing the core architecture.

---

## Core Principles

UOP is built around a few fundamental principles.

* Observations are immutable.
* Knowledge evolves over time.
* Everything is traceable.
* Open standards are preferred.
* Simplicity is favoured over unnecessary complexity.

---

## What is an Observation?

An observation is an immutable record describing something that existed at a specific location and point in time.

An observation typically contains:

* Photograph(s)
* Geographic position
* Timestamp
* Device metadata
* Optional notes

Observations never change.

New interpretations are stored separately as Knowledge.

---

## High-Level Architecture

```
        Mobile Client
              │
              ▼
        REST / GraphQL API
              │
    ┌─────────┴─────────┐
    │                   │
Observation Store   Processing Queue
    │                   │
    │          OCR / AI / Analysis
    │                   │
    └─────────┬─────────┘
              ▼
      Knowledge Database
              │
              ▼
 Search • Maps • Analytics
```

---

## Project Goals

* Collect high quality observations.
* Preserve historical data.
* Generate traceable knowledge.
* Support geographical analysis.
* Remain inexpensive to operate.
* Be easy to extend.

---

## Planned Components

| Component | Status |
|-----------|--------|
| Mobile Client | Planned |
| Web Client | Planned |
| REST API | Planned |
| Observation Store | Planned |
| Knowledge Engine | Planned |
| OCR Processor | Planned |
| Analysis Engine | Planned |
| Plugin SDK | Planned |

---

## Documentation

The documentation is organised into several sections.

```
docs/

architecture/
reference/
adr/
api/
development/
operations/
backlog/
glossary/
```

---

## Roadmap

Current milestone:

**v0.4 — Foundation**

Next milestones:

* Bootstrap repository
* Complete documentation
* API specification
* Domain model
* Reference implementation

---

## Technology (current proposal)

Backend

* Python
* FastAPI

Database

* PostgreSQL
* PostGIS

Object Storage

* MinIO

Mobile

* Flutter

Frontend

* React

Deployment

* Docker Compose

---

## Project Status

The project is currently in the architecture phase.

No production-ready implementation exists yet.

---

## Contributing

The project is currently under active design.

External contributions will be welcomed after the initial architecture has stabilised.

---

## License

License selection is pending.

Apache 2.0 is currently the preferred candidate.

---

## Repository Structure

```
backend/
mobile/
web/
processors/
api/
docs/
tests/
.github/
```

---

## Philosophy

Build only what solves a real problem.

Document every important decision.

Prefer clarity over cleverness.

Everything should be understandable.
