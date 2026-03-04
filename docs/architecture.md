# QueryForge Architecture

```mermaid
flowchart TD

A[User Request] --> B[Context Manager]

B --> C[Database Schema Introspection]
B --> D[Filesystem Metadata]

C --> E[LLM Pipeline Generator]
D --> E

E --> F[Pipeline JSON]

F --> G[Pipeline Synthesizer]

G --> H[Generate SQL Scripts]
G --> I[Generate Bash Scripts]

H --> J[Sandbox Execution]
I --> J

J --> K{Execution Success?}

K -->|Yes| L[Commit Results + Logs]

K -->|No| M[Repair Loop]

M --> E
