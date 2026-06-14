# AgentScope Architecture

AgentScope is a local-first static analysis engine.

The system analyzes repository configuration files and produces authority chains, blast radius classifications, and findings.

## High-Level Flow

```text
Repository
    ↓
Repository Scanner
    ↓
Workflow Parser
    ↓
Capability Detection
    ↓
Authority Chain Engine
    ↓
Blast Radius Engine
    ↓
Findings Engine
    ↓
Reports
```

## Repository Scanner

Responsible for discovering supported configuration files.

Current V1 scope:

```text
.github/workflows/*.yml
.github/workflows/*.yaml
*.tf
```

## Workflow Parser

Extracts:

* workflow triggers
* permissions
* referenced actions
* execution steps

Example:

```yaml
permissions:
  contents: write

steps:
  - uses: aws-actions/configure-aws-credentials
  - run: terraform apply
```

## Capability Detection Engine

Maps workflow signals into capabilities.

Example:

```text
contents: write
    →
repo_write
```

Example:

```text
configure-aws-credentials
    →
assume_cloud_role
```

## Authority Chain Engine

Builds execution paths.

Example:

```text
github-actions
  → assume_cloud_role
  → terraform_apply
  → infrastructure
```

Authority chains are the primary data model of AgentScope.

## Blast Radius Engine

Evaluates authority chains and assigns impact levels.

Levels:

```text
repository
cloud
infrastructure
```

The highest-impact chain determines blast radius.

## Findings Engine

Evaluates authority chains against predefined rules.

Example:

```text
FND-010

CI assumes cloud role
AND
CI runs terraform apply

Severity:
CRITICAL
```

## Outputs

AgentScope supports:

* console reports
* JSON output
* markdown reports

All outputs derive from the same authority graph and findings engine.

## Design Principles

* Local-first
* Read-only
* Explainable
* Fast
* Minimal dependencies
