# Processors

> Processors transform observations into knowledge without modifying the original data.

---

# Purpose

Processors are responsible for generating knowledge from observations.

They perform automated or semi-automated processing and produce new knowledge that can be searched, analysed and reviewed.

Processors never modify observations.

Their only responsibility is to create new knowledge.

---

# Definition

A Processor is a logical component that consumes one or more observations and produces one or more knowledge objects.

Processors may operate automatically, on demand or as part of scheduled workflows.

The platform is designed to support multiple independent processors.

---

# Characteristics

Processors are:

- Independent
- Stateless whenever practical
- Replaceable
- Traceable
- Extensible

Each processor has a clearly defined responsibility.

---

# Processing Model

The general processing model consists of four steps.

```
Observation

↓

Processor

↓

Knowledge

↓

Analysis (optional)
```

A processor may consume existing knowledge in addition to observations, provided that all inputs remain traceable.

---

# Responsibilities

Processors may perform tasks such as:

- Optical Character Recognition (OCR)
- Image classification
- Object detection
- Language identification
- Metadata extraction
- Similarity detection
- Human-assisted interpretation
- Validation

The platform is intentionally extensible and does not restrict future processor types.

---

# Inputs

Processors may consume:

- Observations
- Images
- Metadata
- Existing Knowledge
- Relations

Every input shall be recorded for traceability.

---

# Outputs

Processors produce one or more Knowledge objects.

Typical outputs include:

- Extracted text
- Detected symbols
- Suggested classifications
- Confidence values
- Human review requests
- Validation results

Processors do not produce analytical results directly.

Analyses are performed separately.

---

# Traceability

Every processor execution shall record:

- Processor identifier
- Processor version
- Execution timestamp
- Input references
- Output references
- Execution status

This information enables reproducibility and auditing.

---

# Execution

Processors may be executed:

- Automatically
- Manually
- On a schedule
- In response to specific events

The execution model is independent of the domain model.

---

# Human-assisted Processing

Some processors may require human interaction.

Examples include:

- Manual text interpretation
- Validation of OCR results
- Classification review
- Quality assessment

Human-assisted processing follows the same traceability principles as automated processing.

---

# Failure Handling

A processor may fail without affecting stored observations.

Failures shall:

- Be recorded
- Be traceable
- Allow reprocessing
- Never corrupt observations

Knowledge is only created when processing completes successfully.

---

# Reprocessing

Observations may be processed multiple times.

Reprocessing may occur when:

- A processor is updated
- A new processor becomes available
- Processing parameters change
- Human review requests reprocessing

Each execution creates new knowledge without altering previous results.

---

# Extensibility

The platform shall support additional processors without requiring changes to the core domain model.

Examples of future processors include:

- Video analysis
- Audio transcription
- Symbol recognition
- Image enhancement
- Machine learning classifiers
- External intelligence integrations

---

# Domain Rules

The following rules apply.

- Processors never modify observations.
- Processors generate knowledge.
- Processor executions are traceable.
- Processor outputs are versioned through the Knowledge model.
- Failed executions never invalidate observations.

---

# Examples

## Example 1

An OCR processor extracts text from an image and creates a Knowledge object containing the recognised text and confidence score.

---

## Example 2

An image classification processor identifies the presence of a sticker and creates Knowledge describing the detected object.

---

## Example 3

A human review processor presents uncertain OCR results to a reviewer who validates the interpretation, resulting in a new version of the corresponding Knowledge object.

---

# Related Documents

- DOMAIN_MODEL.md
- OBSERVATION.md
- KNOWLEDGE.md
- RELATIONS.md
- ANALYSIS.md
