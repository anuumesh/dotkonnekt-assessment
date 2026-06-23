# Sample Submission Outline

This file shows the expected depth and structure of a strong submission. It is not a model answer to copy. It is a reference for how specific and practical the response should feel.

## 01 - Solution Proposal

### Executive Summary

Recommend a RAG-based AI assistant that starts with website support and product discovery. The MVP should ground answers in approved product, policy, FAQ, and manual content, use Shopify as the product and commerce source, escalate uncertain cases to Zendesk, and add limited Salesforce context only where permissions are clear.

### Architecture

The proposal should include:

- Web chat or embedded support widget
- API/orchestration service
- Retrieval service with vector and keyword search
- LLM service with guardrails and answer validation
- Shopify sync and real-time lookup paths
- Salesforce customer context access
- Zendesk ticket creation and handoff
- Observability, audit logging, and admin controls

### Key Decisions

| Decision | Recommended direction |
| --- | --- |
| AI approach | RAG first, fine-tuning later only if there is a clear need |
| MVP channel | Website assistant |
| Escalation | Conservative escalation to Zendesk for low confidence or sensitive topics |
| Data freshness | Hybrid sync: webhooks and batch jobs for catalog, real-time calls for critical state |
| Cloud | Use the client's existing AWS or GCP standard |
| Security | Minimize PII, log safely, encrypt data, audit access, version prompts and knowledge sources |

### Tradeoffs

The answer should explain tradeoffs such as:

- RAG vs fine-tuning
- Real-time APIs vs cached/indexed data
- Fast MVP vs broad feature scope
- Automation rate vs customer trust
- Single-provider simplicity vs long-term portability

## 02 - Delivery Plan

### Discovery

Discovery should run for approximately three weeks and produce:

- Current-state workflow map
- Support category and ticket-volume analysis
- Product and policy data quality report
- Integration feasibility review
- AI accuracy baseline
- Security and compliance constraints
- MVP scope and delivery roadmap

### MVP

MVP should include:

- Product and policy Q&A
- Shopify catalog grounding
- Zendesk escalation
- Basic product recommendations
- Monitoring and audit logs
- Human review loop for quality

MVP should defer:

- Full returns/refunds automation
- Order tracking unless simple
- Multi-channel launch
- Deep personalization
- Complex autonomous actions

### Timeline

| Phase | Duration |
| --- | --- |
| Discovery | 3 weeks |
| Architecture and setup | 2 weeks |
| MVP build | 6 weeks |
| Integration and hardening | 3 weeks |
| Pilot rollout | 3 weeks |
| Production rollout | 3 weeks |

### Risks

The plan should include specific risks, owners, and mitigations. Examples:

- Data quality is poor: run early audit, create content cleanup backlog, score source confidence.
- LLM accuracy is low: improve retrieval, tighten prompts, escalate conservatively.
- Shopify API rate limits: use webhooks, cache common data, avoid unnecessary real-time calls.
- Scope grows: hold MVP boundary and move extras to phase two.

## 03 - Engineering Leadership

### Team

Recommended core team:

- Delivery Head
- Technical Lead
- AI/LLM Engineer
- Backend Engineer
- Data Engineer
- Platform/DevOps Engineer
- QA Engineer
- Product Manager
- Client SMEs for commerce, support, security, and compliance

### Engineering Practices

Expected practices:

- Pull request reviews
- CI/CD with automated tests and security scans
- Environment separation
- Versioned prompts and knowledge sources
- Integration tests for Shopify, Salesforce, and Zendesk
- AI quality evaluation set
- Production runbooks
- On-call and escalation process

### Operational Readiness

Before launch, the team should have:

- Dashboards for latency, errors, escalation, accuracy, and cost
- Alerting thresholds
- Rollback tested
- Zendesk handoff tested
- Support team trained
- Audit logging enabled
- Incident response process ready

## 04 - Presentation Link

The presentation file should include:

```text
Presentation link: https://loom.com/share/example
Recording date: 2026-06-23
Presenter: Candidate Name
Notes: Camera and screen share enabled. Recording is approximately 15 minutes.
```

The presentation should cover:

- Recommended architecture
- Why this is the right MVP
- Delivery timeline
- Key risks
- Decisions required from executives
- What happens in the first 30 days
