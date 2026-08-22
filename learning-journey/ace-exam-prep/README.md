# Associate Cloud Engineer Exam Preparation

This directory documents my preparation for the **Google Cloud Associate Cloud Engineer (ACE)** certification.

The goal is to combine official Google Cloud certification resources, hands-on learning, source-grounded AI study techniques, and structured review notes into a repeatable exam-preparation workflow.

---

## Certification Focus

The Associate Cloud Engineer exam evaluates skills across four primary areas:

1. **Set up a cloud solution environment**
2. **Plan and implement a cloud solution**
3. **Configure access and security**
4. **Ensure successful operation of a cloud solution**

These domains are used to guide both my study process and the organization of technical evidence throughout this repository.

---

## Study Materials

### Certification Overview

[ACE Certification Overview](ace-certification-overview.md)

Includes:

- ACE role responsibilities
- Exam domains
- Standard exam information
- Official Google Cloud references
- Certification preparation resources

---

### Gemini Notebook Study Workflow

[Gemini Notebook Prompts](gemini-notebook-prompts.md)

Contains reusable source-grounded prompts for:

- Finding relevant training content
- Explaining technical concepts
- Summarizing exam objectives
- Generating scenario-based practice questions
- Preventing unsupported answers
- Requiring source citations

The primary grounding rule is:

> Answer only using the provided sources. If the sources do not contain enough information to answer the question, state that clearly rather than filling in missing information.

---

## Study Notes

The [`study-notes/`](study-notes/) directory contains focused notes created while reviewing ACE exam objectives and Google Cloud services.

Topics will be added as certification preparation continues.

---

## Study Tools

- **Google Skills** — official Google Cloud learning paths and hands-on training
- **Gemini Notebook / NotebookLM** — source-grounded study and review
- **Google Cloud Documentation** — authoritative technical reference
- **Google Cloud Console** — hands-on platform experience
- **GitHub** — documentation of labs, diagrams, notes, and learning progress

---

## Study Method

The study workflow follows this cycle:

```text
ACE Exam Objective
       ↓
Review Official Source
       ↓
Locate Relevant Training
       ↓
Perform Hands-on Practice
       ↓
Document Key Concepts
       ↓
Test Understanding
       ↓
Identify Knowledge Gaps
       ↓
Return to Training as Needed
```
---

## Related Repository Areas

ACE preparation is supported by technical work throughout this repository:

| ACE Area                            | Repository Evidence                                         |
| ----------------------------------- | ----------------------------------------------------------- |
| Set up a cloud solution environment | `compute-engine/`, projects, CLI work                       |
| Plan and implement a cloud solution | `compute-engine/`, `storage/`, `networking/`, `kubernetes/` |
| Configure access and security       | `iam-security/`                                             |
| Ensure successful operation         | `operations-monitoring/`                                    |
| Hands-on practice                   | `labs/`                                                     |
| Architecture understanding          | `architecture-diagrams/`                                    |
