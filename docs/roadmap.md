# Roadmap

## V1

* GitHub Actions parsing
* Terraform detection
* Authority chain generation
* Blast radius classification
* Findings engine
* JSON output
* Markdown reports

## V1.1

Automation Authority Graph

Example:

```text
github-actions
  → assume_cloud_role
  → terraform_apply
  → infrastructure
```

Graph export:

```bash
agentscope graph . --format dot
```

## Future

Potential future directions:

* GitLab CI support
* Jenkins support
* Multi-repository analysis
* Automation governance workflows
* Policy simulation
* Runtime visibility integrations

These are exploratory and not committed roadmap items.
