# 01 - Solution Proposal Guide

This guide explains what the solution proposal should include. Candidates may use this structure directly or adapt it, but the final response should cover every section below.

## 1. Executive Summary

Start with a short summary of the recommended direction.

A strong summary should include:

- The assistant should launch first as a website support and product discovery assistant, with human escalation through Zendesk.
- The system should use retrieval-augmented generation so answers are grounded in the retailer's product catalog, policies, FAQs, and manuals.
- Shopify should be treated as the near-real-time product and order context source.
- Salesforce should provide customer context where authorized.
- Zendesk should remain the operational fallback for complex, sensitive, or low-confidence cases.
- The first release should prioritize reliable answers, safe escalation, observability, and measurable business impact over broad channel coverage.

## 2. Recommended Architecture

The architecture should include these layers:

| Layer | Responsibility |
| --- | --- |
| Customer channel | Website chat or embedded assistant where customers ask questions and receive product recommendations |
| API/orchestration layer | Authenticates requests, manages sessions, calls retrieval and LLM services, applies business rules, and routes escalations |
| AI layer | Uses an LLM with grounded prompts, retrieval context, guardrails, confidence checks, and response formatting |
| Retrieval/data layer | Stores embeddings and searchable content from catalog, policies, FAQs, manuals, and selected CRM/support data |
| Integration layer | Connects to Shopify, Salesforce, and Zendesk using APIs, webhooks, batch syncs, retries, and failure handling |
| Operational layer | Provides logging, metrics, tracing, alerting, cost monitoring, audit trails, and incident response workflows |

The proposal should explain why each layer exists and how the layers interact.

## 3. AI and Data Strategy

Recommended approach:

- Use RAG for grounding instead of relying only on model memory.
- Keep source documents versioned so answers can be traced back to approved content.
- Use structured retrieval for product facts such as price, availability, size, return eligibility, and policy details.
- Use semantic retrieval for FAQs, manuals, buying guides, and troubleshooting content.
- Use prompt templates with clear answer boundaries: if the system cannot find supporting evidence, it should say so or escalate.
- Add confidence thresholds for escalation to Zendesk.
- Capture feedback signals from customers and support agents to improve retrieval quality over time.

The candidate should explain when fine-tuning might be useful. A reasonable answer is that fine-tuning is not required for MVP unless there is a clear style, classification, or routing need that RAG and prompting cannot satisfy.

## 4. Integration Approach

### Shopify

Use Shopify for:

- Product catalog
- Inventory status
- Pricing
- Product metadata
- Cart and browsing context where available
- Order lookup for authenticated customers

Recommended pattern:

- Use webhooks for product and inventory changes.
- Use scheduled sync for catalog backfills and search index refresh.
- Use real-time API calls only where freshness is critical.
- Cache high-read product data to reduce latency and API dependency.

### Salesforce

Use Salesforce for:

- Customer segment
- Account history
- Loyalty tier
- Recent interactions
- Business rules for high-value customers

Recommended pattern:

- Access Salesforce only for authenticated or authorized customer flows.
- Minimize PII exposure in prompts and logs.
- Use field-level permissions and audit logging.
- Define fallback behavior when Salesforce is unavailable.

### Zendesk

Use Zendesk for:

- Human escalation
- Ticket creation
- Agent handoff
- Resolution tracking
- Feedback loop for failed or escalated answers

Recommended pattern:

- Create tickets with conversation summary, customer intent, retrieved sources, confidence score, and suggested category.
- Escalate immediately for sensitive issues such as refunds, account access, legal complaints, payment failures, and low-confidence answers.
- Feed ticket outcomes into reporting and future knowledge-base improvement.

## 5. Scalability and Performance

Expected design targets:

| Metric | Recommended target |
| --- | ---: |
| Monthly active users | 500,000+ |
| p95 response latency for common questions | Under 2 seconds |
| Availability | 99.9% |
| Error rate | Under 0.1% for customer-facing API requests |
| Initial automation target | 70-80% of common support questions |
| Mature automation target | 90-95% after tuning and content improvement |

Recommended scaling approach:

- Horizontally scale stateless API services.
- Cache common product and policy retrieval results.
- Use a queue for non-interactive work such as indexing, feedback processing, and analytics.
- Keep synchronous request paths small and observable.
- Use rate limits per user/session/client to protect downstream systems.
- Track LLM usage and cost per conversation.
- Use smaller/faster models for classification and routing when appropriate.

## 6. Security, Privacy, and Governance

The proposal should include:

- TLS for data in transit.
- Encryption at rest for databases, logs, vector stores, and object storage.
- Role-based access for admin and support tools.
- PII minimization before sending data to model providers.
- Audit logs for customer data access, prompt changes, and admin actions.
- Data retention policy for conversations and derived analytics.
- GDPR/CCPA support for delete and access requests.
- Prompt and model version tracking.
- Human approval process for major knowledge-base or policy changes.
- Incident response plan for incorrect answers, data leakage, and system downtime.

## 7. Recommended Technology Choices

The candidate may choose AWS or GCP. A strong answer explains the choice based on the client's existing cloud footprint.

Example AWS-oriented stack:

| Area | Recommendation | Why |
| --- | --- | --- |
| Cloud | AWS | Mature enterprise controls, strong observability, common retail adoption |
| Runtime | ECS/Fargate or EKS | Supports containerized services and horizontal scaling |
| API layer | FastAPI, Node.js, or similar service framework | Simple API development and good integration ecosystem |
| LLM | Managed LLM provider with enterprise data controls | Faster MVP, less operational burden than self-hosting |
| Retrieval | OpenSearch, pgvector, Pinecone, or another managed vector store | Supports semantic retrieval and scalable search |
| Database | PostgreSQL | Reliable transactional store for sessions, configuration, and audit metadata |
| Cache | Redis/ElastiCache | Low-latency cache for frequent product and policy lookups |
| Queue | SQS or Pub/Sub equivalent | Decouples indexing, analytics, and retryable integration work |
| Observability | CloudWatch plus Datadog/New Relic if already used | Metrics, logs, traces, and alerting |

## 8. Key Tradeoffs

Strong proposals should cover at least these tradeoffs:

### RAG vs Fine-Tuning

Recommended MVP decision: RAG first.

Reason: Product, policy, and inventory data change frequently. RAG keeps answers grounded in current approved content. Fine-tuning can be revisited later for tone, classification, or repeated domain-specific tasks.

### Real-Time APIs vs Batch Sync

Recommended decision: Hybrid.

Reason: Product catalog and policy documents can be synced and indexed. Inventory, cart, and order information may need real-time or near-real-time access.

### Automation vs Human Escalation

Recommended decision: Conservative escalation during MVP.

Reason: Customer trust matters more than maximum automation at launch. Escalation can become more selective as accuracy improves.

### Single LLM Provider vs Multi-Provider

Recommended decision: Start with one enterprise-ready provider, design abstraction for future portability.

Reason: Multi-provider support adds complexity. The architecture should avoid deep lock-in, but MVP should stay focused.

## 9. Open Questions for Discovery

Important discovery questions:

- What is the quality and structure of the product catalog?
- How often do prices, inventory, and policies change?
- Which customer data fields are allowed in AI workflows?
- What support categories create the highest ticket volume?
- What questions must always be escalated?
- What are the client's data residency requirements?
- Which cloud platform and observability tools are already standard?
- What is the current cost per support ticket?
- What customer channels are in scope for MVP?

## 10. Recommended First Release

The first release should include:

- Website assistant for product and support Q&A
- Shopify product/catalog grounding
- Zendesk escalation
- Basic authenticated customer context where approved
- Admin-configurable escalation rules
- Monitoring dashboards
- Conversation audit trails
- Human review workflow for answer quality

Returns, refunds, order tracking, additional channels, and advanced personalization should follow after the assistant is stable and measurable in production.
