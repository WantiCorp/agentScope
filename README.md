# AgentScope

AgentScope helps teams understand what their automation can actually do.

Modern software delivery relies on automation systems such as GitHub Actions, CI pipelines, infrastructure provisioning workflows, deployment bots, and workflow engines. These systems accumulate permissions across repositories, cloud environments, infrastructure platforms, and deployment tooling.

While permissions are often reviewed individually, the effective authority of automation is rarely visible.

AgentScope analyzes repository configuration files and reveals:

* Automation identities
* Automation capabilities
* Automation authority chains
* Automation blast radius

## The Problem

Most teams know what permissions exist.

Few teams understand what automation can actually execute.

For example:

```text
github-actions
  → assume_cloud_role
      → terraform_apply
          → infrastructure
```

The workflow above may appear harmless when reviewed one configuration at a time.

In practice, the combined permissions allow automation to modify production infrastructure.

AgentScope exposes these authority chains and helps teams understand the true impact of automation.

## Core Concept: Automation Authority Chains

AgentScope models automation authority as:

```text
identity → capability → system impact
```

Examples:

```text
github-actions
  → repo_write
  → repository
```

```text
github-actions
  → assume_cloud_role
  → terraform_apply
  → infrastructure
```

The collection of authority chains defines the automation blast radius of a repository.

## Example Output

```text
⚠ Infrastructure-Level Automation Authority Detected

Primary Authority Chain
-----------------------
github-actions
  → assume_cloud_role
  → terraform_apply
  → infrastructure

Blast Radius
------------
INFRASTRUCTURE

Findings
--------
FND-003 CI assumes AWS role
FND-004 Workflow runs terraform apply
FND-010 CI can modify infrastructure
```

## Scope

AgentScope V1 focuses on static analysis of repository configuration files.

Supported:

* GitHub Actions workflows
* Terraform configuration detection
* Capability discovery
* Authority chain generation
* Blast radius classification
* Findings reporting

Out of Scope:

* Runtime monitoring
* Policy enforcement
* Cloud API integration
* SaaS backend
* Telemetry
* Web UI

## Vision

AgentScope is the first step toward a broader automation governance platform.

Visibility comes first.

Before organizations can govern automation, they must understand the authority automation already possesses.

## Status

AgentScope is currently an open design and research project.

The repository contains:

* Product specifications
* Architecture documents
* Detection models
* Example reports
* Roadmap and future direction

## License

MIT
