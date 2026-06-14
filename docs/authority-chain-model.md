# Automation Authority Chain Model

AgentScope models automation through authority chains.

## Traditional Permission Analysis

Most tools answer:

> What permissions exist?

Example:

```text
GitHub Actions
Permissions:
- contents: write
```

While useful, permissions alone do not reveal impact.

## Authority Analysis

AgentScope asks:

> What can automation actually execute?

Authority is modeled as:

```text
identity
  → capability
      → impact
```

Example:

```text
github-actions
  → repo_write
  → repository
```

Example:

```text
github-actions
  → assume_cloud_role
  → terraform_apply
  → infrastructure
```

## Components

### Identity

The automation actor.

Examples:

* GitHub Actions
* GitLab CI
* Jenkins
* Workflow engines
* AI agents

### Capability

An action the automation can perform.

Examples:

* repository write
* secret access
* role assumption
* infrastructure deployment

### Impact

The resulting system affected.

Examples:

* repository
* cloud resources
* infrastructure

## Blast Radius

The collection of authority chains determines blast radius.

Repository blast radius:

```text
github-actions
  → repo_write
  → repository
```

Infrastructure blast radius:

```text
github-actions
  → assume_cloud_role
  → terraform_apply
  → infrastructure
```

The highest-impact chain determines the effective blast radius of automation.

## Why It Matters

Permissions are rarely dangerous in isolation.

Risk emerges when permissions are combined into executable paths.

Authority chains make those paths visible.
