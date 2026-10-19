# NATURAL-FORMS 📐

> **Declarative Spec & Schema Engine for Human Intent**
> *The architectural bridge that transforms abstract business logic into deterministic software contracts.*

## 🎯 The Concept

If **NATURAL** represents the ecosystem and manifesto for aligning human intent with machine execution, **NATURAL-FORMS** serves as its **declarative modeling and specification engine**.

Working directly with free-text AI prompts often leads to inconsistent outcomes—hallucinations, loss of business context, and missing strict types. **NATURAL-FORMS** addresses this by introducing a standardized intent capture format—an "architectural form" that translates human vision into unambiguous rules for AI agents and code generators.

## 🧱 Anatomy of a "Form" (`.nform` / `forms.yaml`)

A **NATURAL-FORM** is a structured contract containing four fundamental layers:

```
┌────────────────────────────────────────────────────────┐
│ 1. INTENT & CONTEXT (The "Why" and Module Scope)       │
├────────────────────────────────────────────────────────┤
│ 2. DATA DOMAIN & SCHEMAS (Entities, DTOs, & Types)     │
├────────────────────────────────────────────────────────┤
│ 3. BUSINESS RULES & CONSTRAINTS (Rules & Boundaries)   │
├────────────────────────────────────────────────────────┤
│ 4. TARGET RUNTIME (Go, Postgres, Python, Docker, etc.)  │
└────────────────────────────────────────────────────────┘
```

### Theoretical Example (`sensor_monitor.nform`):

```yaml
natural_form_version: "1.0"
module: "SensorDataCorrelation"

intent:
  summary: "Ingest telemetry data from IoT sensors and correlate temperature spikes across time windows."
  target_audience: "Internal Analytics Engine"

domain:
  entities:
    - name: "SensorRead"
      fields:
        sensor_id: "UUID"
        temperature: "Float64"
        timestamp: "DateTime (UTC)"
  
constraints:
  - "Readings exceeding 85.0C must trigger an immediate alert event."
  - "The database must persist events in batches every 5 seconds."

target_stack:
  language: "Go"
  database: "PostgreSQL"
  architecture: "Clean Architecture / Hexagonal"
```

## ⚙️ Lifecycle: From Form to Code

1. **Human Definition (`.nform`):** The architect fills out or interactively constructs the *Form* defining business goals and data types.
2. **Coherence Validation (Engine):** The NATURAL-FORMS engine inspects the structure for missing types or conflicting constraints.
3. **Agent Context Injection:** The *Form* is fed into AI agents (Claude, Gemini, Cursor) as an immutable **Single Source of Truth**.
4. **Deterministic Generation & Testing:** The AI outputs code adhering 100% to declared types and rules.

## 🚀 Key Benefits

* **Determinism:** Minimizes non-deterministic output from LLMs by establishing strict scope boundaries.
* **Model Agnostic:** Serves as structured context for any modern LLM (Gemini, Claude, GPT, DeepSeek).
* **Living Documentation:** The same *Form* driving AI code generation doubles as project architectural documentation.

## 🗺️ Roadmap

- [ ] Define formal JSON Schema for validating `.nform` files
- [ ] Build an interactive CLI generator (`natural-forms init`)
- [ ] Develop automated connectors for the broader **NATURAL** ecosystem