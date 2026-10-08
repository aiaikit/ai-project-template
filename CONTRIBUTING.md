# Contributing to AI Project Template

This template is the foundation for AI-driven software projects. Changes here affect every project created from it.

## How to Contribute

### Improving AI Development Standards (AGENTS.md)

AGENTS.md defines how AI agents operate. When improving it:

1. Changes should make AI behavior more predictable and reliable
2. Follow the existing structure and conventions
3. Test changes with an AI agent before merging

### Improving Documentation Templates

Templates in `.specify/templates/` are used to create new artifacts:

- `research-template.md` — Research document structure
- `architecture-template.md` — Architecture document structure
- `adr-template.md` — Architecture Decision Record structure
- `prototype-template.md` — Prototype document structure

When improving templates:

1. Keep templates concise and actionable
2. Ensure templates cover all necessary sections
3. Test templates by creating a sample artifact

### Improving Project Infrastructure

GitHub Actions, issue templates, and CI/CD:

1. Changes should validate template structure, not enforce project-specific rules
2. YAML must be valid
3. Markdown must be parseable

## PR Requirements

- All CI checks must pass
- No breaking changes without clear migration path
- Changes must work as a template (no hardcoded values)

## Template Validation

Run validation locally:

```bash
# Check structure
ls -la .github/workflows .github/ISSUE_TEMPLATE .aiaikit .specify/memory .specify/specs .specify/templates docs/project

# Validate YAML
python3 -c "import yaml; yaml.safe_load(open('.aiaikit/project.yaml'))"
```

## Questions

Open an issue for questions about contributing.
