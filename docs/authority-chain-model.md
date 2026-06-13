🧩 authority-chain-model.md
# Automation Authority Chain Model

AgentScope is built around one core abstraction:

> The Automation Authority Chain

---

## Definition

An authority chain describes how an automation identity can impact systems.


identity → capability → system impact


---

## Example Chains

### Repository-level


github-actions → repo_write → repository


---

### Cloud-level


github-actions → assume_cloud_role → cloud


---

### Infrastructure-level


github-actions → assume_cloud_role → terraform_apply → infrastructure


---

## Components

### Identity

The automation actor.

Examples:

- github-actions
- CI workflows

---

### Capability

What the automation can do.

Examples:

- repo_write
- secret_access
- assume_cloud_role
- terraform_apply

---

### System Impact

Where the capability applies.

- repository
- cloud
- infrastructure

---

## Chain Construction

AgentScope builds chains by:

1. detecting identity
2. extracting capabilities
3. mapping capabilities → impact
4. composing multi-step flows

---

## Blast Radius

The blast radius is the highest impact level reachable.

Hierarchy:


repository < cloud < infrastructure


---

## Multi-Step Chains

Capabilities can compose:


assume_cloud_role + terraform_apply → infrastructure mutation


---

## Example Full Set


github-actions → repo_write → repository
github-actions → secret_access → cloud
github-actions → assume_cloud_role → terraform_apply → infrastructure


---

## Interpretation

This implies:

- repository modification capability
- secret access potential
- infrastructure mutation capability

---

## Goal

Make automation authority:

- explicit
- inspectable
- deterministic
- explainable

---

## Future Extensions

- multi-identity graphs
- cross-repository authority mapping
- probabilistic execution paths
- runtime validation models