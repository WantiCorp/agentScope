# AgentScope

## Reveal the Authority and Blast Radius of Automation

AgentScope is a developer tool that helps organizations understand what their automation can actually do.

Modern software delivery relies on automation systems such as:

* GitHub Actions
* CI/CD pipelines
* deployment workflows
* infrastructure provisioning systems
* automation bots

These systems accumulate permissions across repositories, cloud environments, infrastructure tooling, secrets stores, and deployment platforms.

Most organizations review these permissions independently.

Very few understand the combined authority they create.

AgentScope exposes the effective authority of automation and reveals how automation identities can impact systems.

---

# Problem

Modern automation is difficult to reason about.

A GitHub Actions workflow may:

* write to repositories
* access secrets
* assume cloud roles
* deploy infrastructure

Each permission appears reasonable when viewed independently.

Together they create an automation identity with significant authority.

Most teams cannot answer:

> What can automation in this repository actually modify?

AgentScope was created to answer that question.

---

# Core Concept

AgentScope introduces the concept of:

## Automation Authority Chains

An authority chain describes how an automation identity can impact systems.

Structure:

```text
identity → capability → impact
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

Authority chains represent effective automation authority.

The collection of authority chains defines automation blast radius.

---

# Design Principles

AgentScope follows five principles.

### Local First

AgentScope analyzes repositories locally.

No cloud connectivity is required.

### Explainable

Every finding must be traceable to repository configuration.

### Fast

Repository scans should complete within seconds.

### Read-Only

AgentScope never modifies infrastructure or configuration.

### Developer Friendly

Output should be understandable by engineers without security expertise.

---

# Goals

AgentScope V1 helps teams answer:

### What automation exists?

### What capabilities does automation possess?

### What systems can automation impact?

### What is the blast radius of automation?

### Which automation paths present the highest risk?

---

# Non Goals

AgentScope V1 is intentionally narrow.

The following are out of scope:

* Runtime monitoring
* Policy enforcement
* Cloud API integrations
* SaaS backend
* Telemetry collection
* Workflow execution
* Remediation automation

AgentScope is a visibility tool.

---

# Supported Platforms

## GitHub Actions

Supported directories:

```text
.github/workflows/
```

Supported file types:

```text
*.yml
*.yaml
```

## Terraform

Supported file types:

```text
*.tf
```

Terraform evaluation is not performed.

V1 only detects:

* Terraform presence
* Terraform execution references

---

# Automation Identities

V1 supports:

| Identity       | Source                |
| -------------- | --------------------- |
| github-actions | GitHub workflow files |

Future versions may support:

* GitLab CI
* Jenkins
* Argo
* AI agents
* Workflow engines

---

# Capabilities

Capabilities represent actions automation may perform.

| Capability        | Detection                 |
| ----------------- | ------------------------- |
| repo_write        | contents=write            |
| release_publish   | packages=write            |
| assume_cloud_role | configure-aws-credentials |
| terraform_apply   | terraform apply           |
| secret_access     | secrets references        |

---

# Authority Chains

AgentScope generates authority chains by combining:

* identities
* capabilities
* impact surfaces

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

Authority chains are the primary output of AgentScope.

---

# Blast Radius Model

Blast radius represents the highest-impact authority available to automation.

Levels:

| Level          | Description                         |
| -------------- | ----------------------------------- |
| Repository     | Can modify source code              |
| Cloud          | Can access cloud resources          |
| Infrastructure | Can create or modify infrastructure |

Severity order:

```text
repository
   < cloud
       < infrastructure
```

---

# Findings Engine

AgentScope includes a built-in findings engine.

Each finding contains:

* ID
* severity
* evidence
* description
* recommendation

Example:

### FND-010

Severity:

```text
CRITICAL
```

Description:

CI assumes cloud roles and executes Terraform.

Authority Chain:

```text
github-actions
  → assume_cloud_role
  → terraform_apply
  → infrastructure
```

---

# CLI Interface

## Scan

```bash
agentscope scan .
```

## JSON Output

```bash
agentscope scan . --format json
```

## Shareable Report

```bash
agentscope scan . --share
```

## Explain Finding

```bash
agentscope explain FND-010
```

---

# Example Output

```text
⚠ Infrastructure-Level Automation Authority Detected

Primary Authority Chain

github-actions
  → assume_cloud_role
  → terraform_apply
  → infrastructure

Blast Radius

INFRASTRUCTURE

Findings

FND-003 Workflow assumes AWS role
FND-004 Workflow runs terraform apply
FND-010 CI can modify infrastructure
```

---

# Future Direction

AgentScope V1 focuses on visibility.

Future versions may explore:

* authority graph visualization
* multi-repository analysis
* automation governance workflows
* policy simulation
* AI agent authority analysis
* runtime execution visibility

Visibility comes first.

Organizations cannot govern automation they cannot see.

---

# Success Criteria

AgentScope succeeds if teams can:

* discover hidden automation authority
* understand automation blast radius
* identify risky execution paths
* reason about automation systems more effectively

The goal is not enforcement.

The goal is understanding.
