# AgentScope Roadmap

## Vision

AgentScope aims to become the system of record for understanding automation authority.

The long-term goal is to help organizations answer:

> What can automation actually do?

Across repositories, cloud environments, workflow systems, and AI-driven automation.

---

# V1

Focus:

Repository-level authority discovery.

Capabilities:

* GitHub Actions parsing
* Terraform detection
* Capability detection
* Authority chain generation
* Blast radius classification
* Findings engine
* JSON output
* Markdown reports

Goal:

Reveal automation authority from repository configuration alone.

---

# V1.1

Automation Authority Graph

New command:

```bash
agentscope graph .
```

Example:

```text
github-actions
  → assume_cloud_role
  → terraform_apply
  → infrastructure
```

Optional export:

```bash
agentscope graph --format dot
```

Purpose:

Visualize execution paths and authority chains.

---

# V2

Expanded Automation Discovery

Potential additions:

* GitLab CI
* Jenkins
* Argo Workflows
* CircleCI

Goal:

Support multiple automation platforms.

---

# V3

Multi-Repository Analysis

Potential capabilities:

* organization-wide scans
* authority aggregation
* shared execution paths

Goal:

Understand automation authority across systems rather than individual repositories.

---

# Future Exploration

Potential research areas:

* automation governance
* policy simulation
* runtime visibility
* execution provenance
* AI agent authority analysis
* delegated automation workflows

These areas are exploratory and not committed roadmap items.

---

# Success Criteria

AgentScope succeeds if teams can:

* identify hidden automation authority
* understand automation blast radius
* discover risky execution paths
* improve visibility into CI/CD systems

The first step toward governance is understanding.
