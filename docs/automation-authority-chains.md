# Automation Authority Chains

Traditional security reviews focus on permissions.

AgentScope focuses on authority.

Permissions answer:

> What access exists?

Authority answers:

> What can automation actually execute?

## Example

Workflow:

```yaml
permissions:
  contents: write

steps:
  - uses: aws-actions/configure-aws-credentials
  - run: terraform apply
```

AgentScope generates:

```text
github-actions
  → assume_cloud_role
  → terraform_apply
  → infrastructure
```

This authority chain provides a more complete representation of automation impact than reviewing individual permissions in isolation.

## Blast Radius

Blast radius is derived from effective authority.

Levels:

* Repository
* Cloud
* Infrastructure

The highest-impact authority chain determines the repository's blast radius classification.
