# AgentScope

AgentScope helps teams understand what their automation can actually do.

Modern software delivery relies on automation systems such as GitHub Actions, CI pipelines, infrastructure provisioning workflows, deployment bots, and workflow engines.

AgentScope analyzes repository configuration files and reveals:

- Automation identities
- Automation capabilities
- Automation authority chains
- Automation blast radius

## Core Concept

identity → capability → system impact

Example:

github-actions
  → assume_cloud_role
  → terraform_apply
  → infrastructure

## Status

Documentation-first open source project.
