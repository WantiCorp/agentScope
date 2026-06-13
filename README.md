# AgentScope

## Automation has become an execution layer. We can no longer see what it can do.

AgentScope is a developer tool for understanding automation authority in software systems.

It analyzes CI/CD pipelines, infrastructure-as-code, and workflow automation to determine what they can actually execute across:

- repositories
- cloud systems
- infrastructure platforms

## The Problem

Modern software systems are driven by automation:

- GitHub Actions
- CI/CD pipelines
- Terraform deployments
- workflow engines
- deployment bots

Each system is usually reviewed in isolation.

But automation does not operate in isolation.

Permissions compose.
Execution paths emerge.
Authority accumulates.

Most teams cannot answer:

> What can automation in this repository actually do?

## The Core Insight

Automation is not a set of tools.

It is a composed execution identity.

## Automation Authority Chains

AgentScope models automation as:

identity → capability → system impact

Example:

github-actions → assume_cloud_role → terraform_apply → infrastructure

Another example:

github-actions → repo_write → repository

## Blast Radius

repository / cloud / infrastructure

## Category

Automation Authority Visibility

## License

MIT
