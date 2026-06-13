# Architecture

AgentScope is a local analysis engine.

Input:

```text
Repository
├── .github/workflows/
├── terraform/
└── application code
```

Processing:

```text
Repository Scanner
        ↓
Workflow Parser
        ↓
Capability Detection Engine
        ↓
Authority Chain Generator
        ↓
Blast Radius Classifier
        ↓
Findings Engine
```

Output:

```text
Human Report
JSON Report
Markdown Share Report
```

AgentScope intentionally performs no live cloud discovery.

All analysis is derived from repository configuration files.
