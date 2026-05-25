# Anthropic CCA-F Certification — Study Resources

Comprehensive study materials for the **Claude Certified Architect – Foundations (CCA-F)** exam, organized by official exam domain with weighted coverage aligned to the certification blueprint.

---

## Exam Overview

The CCA-F is a scenario-based certification that evaluates architectural judgment, orchestration reasoning, system reliability, and production-safe decision making across the Anthropic/Claude ecosystem. The exam presents 4 randomized scenarios (from a pool of 6) covering real-world production contexts such as customer support agents, multi-agent research systems, CI/CD pipelines, and structured data extraction.

---

## Repository Structure

### Domain Study Guides

| File | Domain | Exam Weight | Focus Areas |
|------|--------|:-----------:|-------------|
| [`Domain1_Agentic_Architecture_Orchestration.md`](Domain1_Agentic_Architecture_Orchestration.md) | Agentic Architecture & Orchestration | **27%** | Agentic loops, orchestration patterns, stop_reason handling, multi-agent coordination, bounded execution, escalation logic, loop termination |
| [`Domain2_Tool_Design_MCP_Integration.md`](Domain2_Tool_Design_MCP_Integration.md) | Tool Design & MCP Integration | **18%** | MCP architecture, tool schemas, tool_choice behavior, idempotency, structured errors, capability isolation, authentication |
| [`Domain3_Claude_Code_Configuration_Workflows.md`](Domain3_Claude_Code_Configuration_Workflows.md) | Claude Code Configuration & Workflows | **20%** | CLAUDE.md hierarchy, instruction precedence, slash commands, hooks, plan mode, CI/CD workflows, non-interactive execution |
| [`Domain4_Prompt_Engineering_Structured_Output.md`](Domain4_Prompt_Engineering_Structured_Output.md) | Prompt Engineering & Structured Output | **20%** | XML prompting, schema-constrained outputs, validation-retry loops, prompt injection mitigation, few-shot design, deterministic extraction |
| [`Domain5_Context_Management_Reliability.md`](Domain5_Context_Management_Reliability.md) | Context Management & Reliability | **15%** | Progressive summarization, lost-in-the-middle effect, error propagation, escalation patterns, confidence calibration, provenance tracking |

### Reference Material

| File | Description |
|------|-------------|
| [`ClaudeCertifiedArchitect_Guide.pdf`](ClaudeCertifiedArchitect_Guide.pdf) | Official Anthropic exam guide — includes all 5 domain task statements, knowledge/skill requirements, and the 6 exam scenario descriptions |

---

## Domain Coverage Map

```
┌─────────────────────────────────────────────────────────┐
│              CCA-F EXAM WEIGHT DISTRIBUTION              │
├──────────────────────────────────────┬────────┬──────────┤
│ Domain 1: Agentic Architecture      │  27%   │ ████████ │
│ Domain 3: Claude Code Workflows      │  20%   │ ██████   │
│ Domain 4: Prompt Engineering         │  20%   │ ██████   │
│ Domain 2: Tool Design & MCP          │  18%   │ █████    │
│ Domain 5: Context Mgmt & Reliability │  15%   │ ████     │
└──────────────────────────────────────┴────────┴──────────┘
```

---

## Exam Scenarios

The exam draws 4 of these 6 scenarios at random. Each scenario frames multiple questions across intersecting domains:

| # | Scenario | Primary Domains |
|---|----------|-----------------|
| 1 | Customer Support Resolution Agent | D1, D2, D5 |
| 2 | Code Generation with Claude Code | D3, D5 |
| 3 | Multi-Agent Research System | D1, D2, D5 |
| 4 | Developer Productivity with Claude | D2, D3, D1 |
| 5 | Claude Code for CI/CD | D3, D4 |
| 6 | Structured Data Extraction | D4, D5 |

---

## Cross-Domain Dependencies

Domain 5, despite its lower weight, is the connective tissue of the entire exam. Understanding these cross-domain links is critical for scenario reasoning:

| When You See... | Think Domain 5 Concept |
|-----------------|----------------------|
| Domain 1 question about subagent failures | Error propagation (Task 5.3) |
| Domain 1 question about missing citations | Provenance preservation (Task 5.6) |
| Domain 2 question about verbose tool output | Tool result trimming (Task 5.1) |
| Domain 3 question about session degradation | Scratchpad files & `/compact` (Task 5.4) |
| Domain 4 question about extraction accuracy | Confidence calibration (Task 5.5) |
| Any question about agent miscalibration | Explicit escalation criteria (Task 5.2) |

---

## How to Use These Materials

### 7-Day Intensive Prep Plan

| Day | Focus | Materials |
|-----|-------|-----------|
| 1–2 | Domain 1 — Agentic Architecture (highest weight) | `Domain1_*.md` + Guide scenarios 1, 3, 4 |
| 3 | Domain 2 — Tool Design & MCP | `Domain2_*.md` + Guide scenarios 1, 3, 4 |
| 4 | Domain 3 — Claude Code Workflows | `Domain3_*.md` + Guide scenarios 2, 5 |
| 5 | Domain 4 — Prompt Engineering | `Domain4_*.md` + Guide scenarios 5, 6 |
| 6 | Domain 5 — Context Management & Reliability | `Domain5_*.md` + cross-reference all domain files |
| 7 | Full mock exam + weak-area review | All materials |

### Each Study Guide Contains

Every domain file follows a consistent structure for efficient study:

- Concept overviews with production perspective
- Task statement breakdowns aligned to official exam guide
- Anti-patterns with failure mode explanations
- Decision frameworks and heuristics
- Scenario walkthroughs with architectural reasoning
- Exam-style MCQs with detailed answer explanations
- Memory anchors for rapid retention
- Revision checklists for final-day review

---

## The Seven Laws of Context Management

These principles from Domain 5 underpin correct reasoning across all domains:

1. **Information not explicitly preserved is silently lost** — summarization destroys data; extraction preserves it
2. **Errors not structurally propagated become invisible** — coordinators can only recover from failures they know about
3. **Escalation is a feature, not a failure** — well-designed systems know their boundaries
4. **Context management is systems engineering** — requires the same rigor as database design
5. **Aggregate metrics lie** — always validate by segment before trusting system-wide numbers
6. **Provenance cannot be recovered downstream** — if source attribution is lost at any stage, it's gone forever
7. **Reliability beats sophistication** — a simple system that preserves data correctly outperforms a complex one that loses information elegantly

---

## Key Architectural Principles

These ten principles recur across all domains and are critical for exam reasoning:

1. **Reliability beats raw capability** — prefer deterministic, bounded systems
2. **Explicit structure beats ambiguity** — schemas, XML tags, typed outputs
3. **Tool design matters more than prompt cleverness** — better tools > better prompts
4. **Context management is critical infrastructure** — not an afterthought
5. **Human escalation is a feature, not a weakness** — build it in from day one
6. **Deterministic workflows beat unconstrained autonomy** — bound your agents
7. **Validation loops prevent cascading failures** — always verify before acting
8. **Long-running agents require bounded execution** — max iterations, timeouts, cost caps
9. **Observability is mandatory in production** — trace, log, monitor everything
10. **Structured outputs dramatically improve reliability** — JSON schemas, typed responses

---

## Anti-Patterns to Recognize

The exam frequently presents these as tempting-but-wrong answers:

- Over-agentic designs (autonomy without guardrails)
- Uncontrolled recursive loops (no termination conditions)
- Vague tool descriptions (causes tool selection failures)
- Prompt-only reliability fixes (no structural validation)
- Excessive context stuffing (degrades model performance)
- Missing escalation logic (no human-in-the-loop fallback)
- Unstructured outputs in pipelines (breaks downstream consumers)
- Absent observability (silent failures in production)
- Progressive summarization of critical facts (loses numerical precision)
- Sentiment-based escalation triggers (unreliable vs explicit criteria)

---

## Contributing

This is a personal study repository. Feel free to fork and adapt for your own CCA-F preparation.

---

## License

Study materials are original content. The `ClaudeCertifiedArchitect_Guide.pdf` is property of Anthropic, PBC.
