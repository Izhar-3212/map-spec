# MAP Spec

> **The open industry standard that transforms random AI prompting and unpredictable code generation into structured, precise, and universally acceptable software specifications.**

**Stop prompting. Start specifying.**

---

## The Problem

AI code generation is powerful but unpredictable. Give an AI a vague prompt and it makes hundreds of micro-decisions on your behalf — choosing databases, designing APIs, structuring components, inventing business logic — all without knowing what you actually want.

The result drifts from your vision. Every time.

This isn't an AI problem. It's a specification problem.

---

## The Solution

MAP Spec (MyAgenticPlatform Specification) is a structured, stack-aware, AI-optimised specification standard that defines **exactly** what software should do, look like, and behave — before a single line of code is written.

When AI is given a MAP Spec, it has no room to deviate. No assumptions. No drift. Just accurate, predictable output that matches what was specified.

---

## Key Principles

- **Structured** — every project follows the same 7-layer format
- **Stack-aware** — specs adapt to your declared technology choices
- **AI-optimised** — written so AI models parse with zero ambiguity
- **Human-readable** — developers can read and write it without tooling
- **Validatable** — every spec can be checked for completeness automatically
- **Versioned** — specs evolve formally with full change history
- **Open** — the standard is free; the best generator is MyAgenticPlatform

---

## The 7 Layers

Every MAP Spec project contains 7 layers, each in its own file:

| Layer | File | Purpose |
|-------|------|---------|
| 1. Meta | `meta.spec.yaml` | Project identity, stack declaration, versioning |
| 2. Functional | `functional.spec.yaml` | Features, user stories, acceptance criteria |
| 3. API | `api.spec.yaml` | Endpoints, request/response contracts, auth |
| 4. Data | `data.spec.yaml` | Database schema, tables, relationships, indexes |
| 5. UI | `ui.spec.yaml` | Components, props, states, behaviours, routing |
| 6. Rules | `rules.spec.yaml` | Business logic guardrails, constraints, policies |
| 7. Quality | `quality.spec.yaml` | Test cases, coverage requirements, benchmarks |

Plus one master index:

| File | Purpose |
|------|---------|
| `spec.manifest.json` | Master index, approval status, phase gating |

---

## Quick Example

```yaml
# meta.spec.yaml
map-spec: "1.0.0"
project:
  id: "proj-001"
  name: "Offline-First Todo App"
  version: "1.0.0"
stack:
  frontend: "Next.js 14"
  backend: "Node.js + Express"
  database: "PostgreSQL"
  auth: "JWT"
  hosting: "Vercel"
  styling: "Tailwind CSS"
```

```yaml
# rules.spec.yaml
map-spec: "1.0.0"
rules:
  - id: "RULE-001"
    domain: "auth"
    rule: "Never store plain text passwords"
    implementation: "bcrypt rounds=12"
    severity: "critical"
    aiInstruction: "Always hash passwords before INSERT. Never log password values."
```

---

## File Structure

```
my-project/
└── specs/
    ├── spec.manifest.json
    ├── meta.spec.yaml
    ├── functional.spec.yaml
    ├── api.spec.yaml
    ├── data.spec.yaml
    ├── ui.spec.yaml
    ├── rules.spec.yaml
    └── quality.spec.yaml
```

---

## Validate Your Specs

```bash
npm install -g map-spec
map-spec validate ./specs/
```

---

## Generate MAP Specs Automatically

[MyAgenticPlatform](https://github.com/Izhar3212/MyAgenticPlatform) is the reference implementation — the fastest and most accurate way to generate MAP Spec compliant specifications from your product idea.

---

## Contributing

MAP Spec is open. Contributions, proposals, and discussions welcome.

- Read the [Contributing Guide](./docs/CONTRIBUTING.md)
- Open a [Discussion](https://github.com/Izhar-3212/map-spec/discussions)
- Propose changes via [Pull Request](https://github.com/Izhar-3212/map-spec/pulls)

---

## Versioning

MAP Spec follows semantic versioning. Current version: **v0.1.0 (draft)**

| Version | Status | Notes |
|---------|--------|-------|
| v0.1.0 | Draft | Initial standard definition |
| v1.0.0 | Planned | First stable release |

---

## License

The MAP Spec standard is released under the [MIT License](./LICENSE) — free to use, implement, and build upon.

---

*MAP Spec is created and maintained by [MyAgenticPlatform](https://github.com/Izhar3212/MyAgenticPlatform)*

