# Why AgentScope

Modern software delivery depends on automation.

GitHub Actions deploy code.
Terraform provisions infrastructure.
CI pipelines publish releases.
Workflow engines trigger operational tasks.

As organizations adopt more automation, permissions become distributed across multiple systems:

* source control
* cloud environments
* deployment tooling
* secrets managers
* infrastructure platforms

Each permission is typically reviewed independently.

The result is a blind spot.

Teams know what permissions exist.

They often do not know what automation can actually do.

For example:

```text
github-actions
  → assume_cloud_role
  → terraform_apply
  → infrastructure
```

Viewed separately:

* GitHub Actions is trusted
* AWS role assumption is trusted
* Terraform is trusted

Combined, they create an automation identity capable of modifying production infrastructure.

Most security and developer tools stop at permissions.

AgentScope focuses on authority.

AgentScope introduces the concept of Automation Authority Chains:

```text
identity → capability → impact
```

By mapping how automation identities interact with systems, AgentScope reveals:

* effective authority
* execution paths
* automation blast radius

Before organizations can govern automation, they must understand it.

Visibility comes first.
