# AI Project Template

A generic AI-driven project template designed for use as a GitHub Template.

## What is this?

A foundation for building new AI-augmented software projects. It establishes:

- **AI Development Standards** — AGENTS.md defines how AI agents work within the project
- **Spec-Driven Development (SDD)** — a structured workflow from Research → Spec → Implementation → Verification
- **Documentation Templates** — for Research, Architecture, ADR, and Prototype artifacts
- **Project Infrastructure** — standard directories, GitHub Actions, and contribution guidelines

## Why use it?

When you start a new project and want AI-assisted development from day one:

1. Click **Use this template** on GitHub → creates a new repo
2. Or run `aiaikit init` in an existing directory
3. AI agents read AGENTS.md and understand how to operate in your project

## What it includes

- AGENTS.md — AI development workflow and standards
- .specify/ — Spec templates (Research, Architecture, ADR, Prototype)
- .aiaikit/project.yaml — Project configuration
- docs/ — Project documentation structure
- prototypes/ — Interactive prototype workspace
- .github/workflows/validate.yml — Template validation

## SDD Workflow

```
需求 (Requirement)
    ↓
Context (Understand)
    ↓
Research (Investigate)
    ↓
Constitution (Principles)
    ↓
Architecture (Design)
    ↓
Spec (Define)
    ↓
Prototype (Validate UI)
    ↓
Plan (Plan)
    ↓
Tasks (Break down)
    ↓
Implementation (Build)
    ↓
Testing (Verify)
    ↓
Documentation (Record)
```

## Prototype Approach

Prototypes validate UI/UX **before** implementation. They can use:

- HTML / CSS / JS
- Vue / React / Storybook
- Any interactive tool

**Figma is not required.** The goal is interactive validation, not polished deliverables.

## Directory Structure

```
.
├── .github/
│   ├── workflows/
│   ├── ISSUE_TEMPLATE/
│   └── pull_request_template.md
├── .aiaikit/
│   └── project.yaml
├── .specify/
│   ├── memory/
│   │   └── constitution.md
│   ├── specs/
│   ├── templates/
│   │   ├── research-template.md
│   │   ├── architecture-template.md
│   │   ├── adr-template.md
│   │   └── prototype-template.md
│   └── scripts/
├── docs/
│   ├── project/
│   ├── research/
│   ├── architecture/
│   ├── adr/
│   └── design/
├── prototypes/
├── AGENTS.md
├── README.md
├── CONTRIBUTING.md
├── LICENSE
├── .editorconfig
└── .gitignore
```

## Getting Started

### Use as GitHub Template

1. Click **Use this template** on this repository
2. Clone your new repository
3. Update `.aiaikit/project.yaml` with your project details
4. Start building

### Initialize an existing directory

```bash
# Coming soon: aiaikit init
git clone <template-repo> .
```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for how to contribute to this template.
