# AgentScope Automation Authority Report

## Automation Detected

* github-actions

## Authority Surface

* repo_write
* assume_cloud_role
* terraform_apply
* secret_access

## Authority Chains

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

## Blast Radius

INFRASTRUCTURE

## Findings

* FND-003 Workflow assumes AWS role
* FND-004 Workflow runs terraform apply
* FND-010 CI can modify infrastructure

## Why This Matters

Permissions are often distributed across multiple systems.

When combined, they can create automation identities capable of modifying production infrastructure with little visibility into the resulting authority.
