# MAP Spec

> The open standard for AI-ready software specifications.

**mapspec.io** · [Standard v1.0.0](docs/STANDARD.md) · [Atomic Specs v1.1.0](docs/ATOMIC.md) · MIT License

---

## The Problem

Give AI a vague prompt and it makes hundreds of silent decisions — wrong database, wrong security approach, invented tables you never asked for. Every run produces different, inconsistent output.

**MAP Spec fixes this.** Write the contract once. Ship the same code every time.

---

## What is MAP Spec?

MAP Spec is an open, MIT-licensed YAML standard that defines exactly what an AI model must build — and what it must never do. Every MAP Spec project contains 7 layers:

| # | Layer | File | What It Defines |
|---|-------|------|-----------------|
| 01 | Meta | `meta.spec.yaml` | Project identity, stack declaration, constraints |
| 02 | Functional | `functional.spec.yaml` | Features, user stories, acceptance criteria + `aiNote` |
| 03 | API | `api.spec.yaml` | Every endpoint with exact request/response contracts |
| 04 | Data | `data.spec.yaml` | Complete database schema with native types |
| 05 | UI | `ui.spec.yaml` | Every component, props, state, interactions |
| 06 | Rules | `rules.spec.yaml` | Business guardrails with mandatory `aiInstruction` |
| 07 | Quality | `quality.spec.yaml` | Test suites, coverage requirements, performance targets |

Together they form a complete, unambiguous contract. If it's not in the spec, AI doesn't build it.

---

## Quick Example

```yaml
# RULE-001-password-hashing.yaml — MAP Spec v1.1.0
map-spec: "1.1.0"
layer: "rules"
atomic: true

unit:
  id: "RULE-001-password-hashing"
  severity: "critical"

rule:
  domain: "security"
  statement: "All passwords must be hashed with bcrypt before storage"
  implementation: "bcrypt cost factor 12"

aiInstruction: >
  Always call bcrypt.hash(password, 12) before any INSERT to users table.
  Never log the password value at any log level.
  Never return the password hash in any API response.

violations:
  - "Storing MD5 or SHA hash instead of bcrypt"
  - "Using bcrypt with cost factor below 10"
  - "Logging password values"
```

An AI receiving only this file knows exactly what to implement and exactly what never to do.

---

## Versions

| Version | Status | Description |
|---------|--------|-------------|
| v1.0.0 | Stable | First stable release |
| v1.1.0 | Current | Atomic spec format, aiInstruction mandatory |

---

## v1.1.0 — Atomic Specs

MAP Spec v1.1.0 introduces **Atomic Specs** — the smallest meaningful unit of specification.

> One file. One concern. Zero ambiguity.

Instead of one large spec file per layer, each atomic unit gets its own file:

```
specs/
  meta.spec.yaml                         ← always single file

  functional/
    FEAT-001-user-registration.yaml      ← just registration
    FEAT-001-user-login.yaml             ← just login
    FEAT-002-create-todo.yaml

  api/
    API-001-POST-auth-register.yaml      ← one endpoint per file
    API-002-POST-auth-login.yaml

  data/
    TABLE-users.yaml                     ← one table per file
    TABLE-todos.yaml

  rules/
    RULE-001-password-hashing.yaml       ← one rule per file
    RULE-002-jwt-expiry.yaml

  ui/
    COMP-001-RegisterForm.yaml           ← one component per file

  quality/
    SUITE-001-auth-integration.yaml      ← one test suite per file
```

**The Dumbest Model Standard:** Every atomic spec must be written so that the least capable AI model can implement it correctly without reading any other file.

Read the full [Atomic Specs standard](docs/ATOMIC.md).

---

## AI Consumption Rules

Any AI system consuming a MAP Spec must follow these rules:

1. **Never invent** fields, endpoints, tables, or components not specified
2. **Never skip** anything that is specified
3. **Always follow** `aiInstruction` fields on critical rules — no exceptions
4. **Never assume** anything not stated — halt and request clarification instead
5. **One atomic file = one implementation unit** — never mix context across files

---

## The Reference Implementation

[MyAgenticPlatform](https://github.com/Izhar3212/MyAgenticPlatform) is the reference implementation — it generates complete MAP Spec packages automatically from a plain English brief.

```
Brief → Phase 0 (Clarification + Mandate)
      → Phase 1 (6 AI agents → artifacts)
      → Phase 2 (7 spec-writers → atomic YAML files)
      → Implementation Board (Jira-style task board)
      → Phase 3 (code generation — coming soon)
```

Try it at [mapspec.io](https://mapspec.io) or run it locally from the [GitHub repo](https://github.com/Izhar3212/MyAgenticPlatform).

---

## Repository Structure

```
map-spec/
├── docs/
│   ├── STANDARD.md        — v1.0.0 full standard (7 layers, monolithic)
│   ├── ATOMIC.md          — v1.1.0 Atomic Specs standard
│   └── CONTRIBUTING.md    — How to contribute
├── examples/
│   └── todo-app/          — Example MAP Spec project
│       └── spec.manifest.json
├── README.md
└── LICENSE                — MIT
```

---

## Documentation

Full documentation is available in the docs/ folder:

- [What is MAP Spec?](docs/what-is-map-spec.md)
- [Why Spec-Driven Development?](docs/why-spec-driven-development.md)
- [AI Drift Explained](docs/ai-drift-explained.md)
- [How It Works](docs/how-it-works.md)
- [MAP Spec Layers](docs/map-spec-layers.md)
- [MAP Spec Discover](docs/map-spec-discover.md)
- [Getting Started](docs/getting-started.md)
- [12-Factor Compliance](docs/twelve-factor-compliance.md)
- [FAQ](docs/faq.md)
- [Glossary](docs/glossary.md)
- [Roadmap](docs/roadmap.md)

## Examples

See the examples/ folder for valid MAP Spec YAML files:
- [Meta spec](examples/example-meta-spec.yaml)
- [Functional spec](examples/example-functional-spec.yaml)
- [API spec](examples/example-api-spec.yaml)
- [Data spec](examples/example-data-spec.yaml)
- [UI spec](examples/example-ui-spec.yaml)
- [Rules spec](examples/example-rules-spec.yaml)
- [Quality spec](examples/example-quality-spec.yaml)

---

## Contributing

MAP Spec is an open standard. Contributions welcome:

- **Propose changes** — open an issue describing the problem and proposed solution
- **Submit examples** — add real MAP Spec projects to `examples/`
- **Build tools** — validators, generators, IDE plugins — link them in issues
- **Improve docs** — clarity fixes, better examples, new layer documentation

See [CONTRIBUTING.md](docs/CONTRIBUTING.md) for guidelines.

---

## Why Open?

The MAP Spec standard is MIT licensed because standards only work when everyone can use them freely. We make money by building the best MAP Spec generator — not by owning the format.

An open standard means:
- Anyone can implement MAP Spec in any tool
- No vendor lock-in — your specs are portable YAML files
- Community improvements benefit everyone
- AI tooling can adopt MAP Spec without licensing friction

---

## License

MIT — see [LICENSE](LICENSE)

---

*Standard maintained by [MyAgenticPlatform](https://mapspec.io) · Reference implementation at [github.com/Izhar3212/MyAgenticPlatform](https://github.com/Izhar3212/MyAgenticPlatform)*
