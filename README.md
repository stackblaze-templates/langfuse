# Langfuse [![Version](https://img.shields.io/badge/version-3-000000)](https://github.com/stackblaze-templates/langfuse) [![Maintained by StackBlaze](https://img.shields.io/badge/maintained%20by-StackBlaze-blue)](https://stackblaze.com) [![Weekly Updates](https://img.shields.io/badge/updates-weekly-green)](https://github.com/stackblaze-templates/langfuse/actions) [![License](https://img.shields.io/github/license/stackblaze-templates/langfuse)](LICENSE) [![Deploy on StackBlaze](https://img.shields.io/badge/Deploy%20on-StackBlaze-orange)](https://stackblaze.com)

<p align="center"><img src="logo.png" alt="langfuse" width="120"></p>

LLM engineering platform for observability, metrics, evaluations, and prompt management.

> **Credits**: Built on [Langfuse](https://langfuse.com) by [Langfuse](https://github.com/langfuse). All trademarks belong to their respective owners.

## Local Development

```bash
docker compose up
```

See the project files for configuration details.

## Deploy on StackBlaze

[![Deploy on StackBlaze](https://img.shields.io/badge/Deploy%20on-StackBlaze-orange)](https://stackblaze.com)

This template includes a `stackblaze.yaml` for one-click deployment on [StackBlaze](https://stackblaze.com). Both options run on **Kubernetes** for reliability and scalability.

<details>
<summary><strong>Standard Deployment</strong> — Single-instance Kubernetes setup for startups and moderate traffic</summary>

<br/>

```mermaid
flowchart LR
    U["Customers"] -->|HTTPS| LB["Edge Network\n+ SSL"]
    LB --> B["Langfuse\nNode.js"]
    B --> DB[("PostgreSQL\nManaged DB")]

    style LB fill:#ff9800,stroke:#e65100,color:#fff
    style B fill:#0041ff,stroke:#002db3,color:#fff
    style DB fill:#4caf50,stroke:#2e7d32,color:#fff
```

**What you get:**
- Single Langfuse instance on Kubernetes
- Managed PostgreSQL database
- Automatic SSL/TLS via StackBlaze edge network
- Automated daily backups
- Zero-downtime deploys

**Best for:** Development, staging, and moderate-traffic production environments.

</details>

<details>
<summary><strong>High Availability Deployment</strong> — Multi-instance Kubernetes setup for business-critical production</summary>

<br/>

```mermaid
flowchart LR
    U["Customers"] -->|HTTPS| CDN["CDN\nStatic Assets"]
    CDN --> LB["Load Balancer\nAuto-scaling"]
    LB --> B1["Langfuse #1"]
    LB --> B2["Langfuse #2"]
    LB --> B3["Langfuse #N"]
    B1 --> R[("Redis\nSessions + Cache")]
    B2 --> R
    B3 --> R
    B1 --> DBP[("PostgreSQL Primary\nRead + Write")]
    B2 --> DBP
    B3 --> DBR[("PostgreSQL Replica\nRead-only")]
    DBP -.->|Replication| DBR

    style CDN fill:#607d8b,stroke:#37474f,color:#fff
    style LB fill:#ff9800,stroke:#e65100,color:#fff
    style B1 fill:#0041ff,stroke:#002db3,color:#fff
    style B2 fill:#0041ff,stroke:#002db3,color:#fff
    style B3 fill:#0041ff,stroke:#002db3,color:#fff
    style R fill:#f44336,stroke:#c62828,color:#fff
    style DBP fill:#4caf50,stroke:#2e7d32,color:#fff
    style DBR fill:#66bb6a,stroke:#388e3c,color:#fff
```

**What you get:**
- Auto-scaling Langfuse pods on Kubernetes behind a load balancer
- Redis for shared sessions, cache, and queue management
- PostgreSQL primary + read replica for high throughput
- CDN for static assets
- Automated failover and self-healing
- Zero-downtime rolling deploys

**Best for:** Production workloads, high-traffic applications, business-critical deployments.

</details>

---

### Maintained by [StackBlaze](https://stackblaze.com)

This template is actively maintained by StackBlaze. We perform **weekly automated checks** to ensure:

- **Up-to-date dependencies** — frameworks, libraries, and base images are kept current
- **Security scanning** — continuous monitoring for known vulnerabilities and CVEs
- **Best practices** — configurations follow current recommendations from upstream projects

Found an issue? [Open a ticket](https://github.com/stackblaze-templates/langfuse/issues).
