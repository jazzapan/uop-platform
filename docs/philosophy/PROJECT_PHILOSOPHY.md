# UOP Project Philosophy

> Build only what solves real problems.

---

# Purpose

This document describes the guiding philosophy behind the Urban Observation Platform (UOP).

It explains the principles that guide architectural decisions, implementation choices and long-term evolution of the project.

Unlike technical documentation, this document focuses on *why* the platform is built the way it is.

---

# Mission

The mission of UOP is to provide an open, extensible and sustainable platform for collecting, preserving and analysing observations from the physical environment.

The platform shall support long-term documentation and analysis without being tied to a particular technology, organisation or deployment model.

---

# Vision

UOP aims to become a reusable platform rather than a single-purpose application.

The reference implementation focuses on graffiti, tags and stickers, but the architecture should support additional observation domains without fundamental redesign.

---

# Core Principles

The project is guided by the following principles.

- Observations are preserved.
- Knowledge evolves.
- Architecture is modular.
- Decisions are documented.
- Simplicity is preferred over unnecessary complexity.
- Open standards are preferred whenever practical.

---

# Observation Before Interpretation

Observations are historical records.

Knowledge is an interpretation of those records.

As analytical methods improve, interpretations may change.

The original observation shall remain unchanged.

This distinction forms one of the fundamental principles of UOP.

---

# Traceability

Every piece of derived information should be traceable.

It should always be possible to determine:

- Which observations were used.
- Which processor created the result.
- Which processor version was used.
- When processing occurred.
- Whether the result has been reviewed.

Traceability is essential for transparency and reproducibility.

---

# Simplicity

Every dependency introduces maintenance.

Every framework introduces complexity.

Every abstraction introduces cost.

The preferred solution is the simplest one that satisfies the requirements.

Complexity should only be introduced when it solves a demonstrated problem.

---

# Modularity

The platform should consist of well-defined modules with clear responsibilities.

Modules communicate through stable interfaces.

Internal implementation details should remain encapsulated.

New functionality should normally be introduced by extending the platform rather than modifying existing components.

---

# Open Technologies

Whenever practical, the project should favour:

- Open standards
- Open protocols
- Open data formats
- Open source software

This reduces long-term dependency on proprietary technologies.

---

# Long-Term Perspective

Programming languages will evolve.

Frameworks will change.

Infrastructure will be replaced.

The domain model and the observations are expected to outlive implementation technologies.

Architectural decisions should therefore prioritise long-term maintainability over short-term convenience.

---

# Documentation

Documentation is considered part of the product.

Features are not complete until their behaviour is documented.

Architecture documentation shall evolve together with the implementation.

---

# Community

UOP is intended to become a community-driven open source project.

Contributions should be encouraged through:

- Clear documentation
- Transparent decision making
- Respectful collaboration
- Stable architecture

The quality of the documentation is as important as the quality of the code.

---

# Decision Making

Architectural decisions should be guided by the following questions:

1. Does the solution solve a real problem?
2. Is it understandable?
3. Is it maintainable?
4. Can it be extended?
5. Can it be documented?
6. Does it remain consistent with the domain model?

If the answer to any of these questions is "no", the decision should be reconsidered.

---

# Final Principle

The Urban Observation Platform should remain understandable.

Software that can be understood can be improved.

Software that cannot be understood will eventually be replaced.
