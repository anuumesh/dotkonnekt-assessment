## 1. Team Structure

Recommended structure:

```text
Delivery Head
  Technical Lead
    AI/LLM Engineer
    Backend Engineer
    Data Engineer
    Platform/DevOps Engineer
    QA Engineer
  Product Manager
  Client SMEs
    Commerce/Product SME
    Support Operations SME
    Security/Compliance SME
```

Recommended ownership:

| Area | Owner |
| --- | --- |
| Delivery plan, client alignment, risk management | Delivery Head |
| Architecture and engineering quality | Technical Lead |
| Retrieval, prompts, evaluation, guardrails | AI/LLM Engineer |
| APIs, orchestration, integrations | Backend Engineer |
| Data ingestion, indexing, data quality | Data Engineer |
| Infrastructure, CI/CD, monitoring, release process | Platform/DevOps Engineer |
| Test strategy, regression, release validation | QA Engineer |
| User journeys, MVP scope, acceptance criteria | Product Manager |

## 2. First 30 Days

Recommended first-month plan:

| Period | Focus | Outcome |
| --- | --- | --- |
| Days 1-5 | Onboarding, client context, system access, architecture walkthrough | Team understands problem, systems, roles, and first goals |
| Days 6-10 | Data samples, integration probes, support workflow review | Key risks visible early |
| Days 11-15 | AI feasibility spike and retrieval prototype | Baseline accuracy and data gaps understood |
| Days 16-20 | MVP planning, backlog creation, CI/CD setup | Build plan is ready |
| Days 21-30 | First sprint delivery and demo | Team ships working vertical slice |

Good first sprint goal:

Build a thin vertical slice where a user asks a product question, the system retrieves approved content, generates a grounded answer, logs the interaction, and escalates to Zendesk when confidence is low.

## 3. Engineering Standards

Recommended standards:

- Pull requests require at least one senior review for core architecture changes.
- Public APIs must be documented through OpenAPI or equivalent.
- Every integration must include timeout, retry, and fallback behavior.
- No PII should be logged unless explicitly approved and masked.
- Prompt and model changes must be versioned.
- New functionality must include tests at the right level.
- Production changes require rollback instructions.
- Technical debt should be tracked and prioritized, not hidden.

Definition of done:

- Acceptance criteria met
- Unit and integration tests passing
- Security and privacy considerations addressed
- Observability added for important flows
- Documentation updated
- Reviewed and approved
- Deployed to staging
- Demoable to the product/client team

## 4. Branching, CI/CD, and Environments

Recommended environments:

| Environment | Purpose |
| --- | --- |
| Local | Developer iteration with mocked services or sandbox credentials |
| Dev | Shared integration testing with non-production data |
| Staging | Production-like validation, load tests, security checks, client acceptance |
| Production | Customer-facing environment with controlled rollout |

Recommended CI/CD checks:

- Formatting and linting
- Unit tests
- Integration tests with mocked and sandboxed third-party APIs
- Dependency vulnerability scan
- Secret scanning
- Container build
- Infrastructure validation
- Smoke test after deploy

Recommended release process:

1. Feature branch to pull request.
2. Automated checks run.
3. Code review and approval.
4. Merge to main or staging branch.
5. Automated deploy to dev/staging.
6. Smoke tests and QA validation.
7. Manual approval for production.
8. Canary deployment.
9. Progressive rollout.
10. Post-deploy monitoring.

## 5. Testing Strategy

| Test type | What it covers | Owner |
| --- | --- | --- |
| Unit | Prompt utilities, parsing, routing rules, validation, scoring logic | Developer |
| Integration | Shopify, Salesforce, Zendesk, vector store, auth provider, database | Developer and QA |
| End-to-end | Customer asks question, gets answer, escalates if needed, ticket includes context | QA Engineer |
| Load/performance | Peak traffic, latency, rate limits, downstream service degradation | Platform/DevOps |
| Security | Auth, authorization, injection, PII handling, dependency risks | Platform/DevOps and security reviewer |
| AI quality evaluation | Groundedness, correctness, helpfulness, hallucination rate, escalation accuracy | AI Engineer and support SMEs |

Recommended AI evaluation set:

- 100 common product questions
- 100 policy and FAQ questions
- 50 edge cases requiring escalation
- 50 product recommendation scenarios
- 25 adversarial or unsafe prompts
- 25 privacy-sensitive scenarios

Every release should be checked against this evaluation set before production rollout.

## 6. Operational Readiness

Before go-live, the team should have:

- Dashboard for latency, throughput, error rate, escalation rate, accuracy, and LLM cost
- Alerts for downtime, latency spikes, error spikes, queue backlog, and API integration failures
- Runbooks for common incidents
- On-call schedule and escalation path
- Rollback procedure tested in staging
- Zendesk handoff verified with support agents
- Audit logs enabled
- Model, prompt, and knowledge-base versions traceable
- Data retention and deletion process documented

Recommended alert thresholds:

| Alert | Threshold |
| --- | --- |
| API error rate | Greater than 5% for 5 minutes |
| p95 latency | Greater than 5 seconds for 5 minutes |
| Zendesk ticket creation failure | Any sustained failure over 2 minutes |
| LLM provider error spike | Greater than 2% for 5 minutes |
| Cost anomaly | 20% above daily forecast |
| Accuracy regression | Evaluation score drops below agreed threshold |

## 7. Leadership Practices

A strong Delivery Head should:

- Make decisions with enough input, but not wait for perfect certainty.
- Keep the team focused on the MVP and protect it from uncontrolled scope growth.
- Communicate risks early, especially when timelines or assumptions change.
- Build trust with client stakeholders through frequent demos and transparent reporting.
- Encourage engineers to challenge decisions with evidence.
- Resolve disagreements by clarifying goals, constraints, and decision ownership.
- Prevent burnout by managing priorities and avoiding permanent urgency.
- Treat incidents as learning opportunities while still holding the team accountable.

## 8. Handling Realistic Challenges

### LLM accuracy is lower than expected

Recommended response:

- Review retrieval quality before blaming the model.
- Inspect source content quality and metadata.
- Tighten answer boundaries and escalation rules.
- Add support-agent review for failed cases.
- Reduce launch scope until accuracy is acceptable.

### Shopify rate limits affect response time

Recommended response:

- Move high-read data to cache or local search index.
- Use webhooks for freshness.
- Add retry and fallback behavior.
- Reserve real-time API calls for cases that truly require current state.

### Security review blocks production release

Recommended response:

- Separate must-fix issues from accepted risks.
- Assign owners and target dates.
- Communicate impact to steering committee.
- Do not launch with unresolved high-risk PII or access-control issues.

### Client asks to add returns and refunds before MVP

Recommended response:

- Explain the risk of adding high-sensitivity workflows too early.
- Offer discovery and design for phase two.
- Include limited FAQ-level returns information in MVP.
- Keep transaction-changing refund workflows out of MVP unless required by executive decision.

## 9. Recommended Operating Model

The project should run as a product delivery team, not a loose collection of technical tasks. The Delivery Head should maintain a clear roadmap, visible risks, frequent demos, strong engineering standards, and production readiness from the beginning. The goal is not just to build an AI assistant. The goal is to launch a trustworthy customer-facing capability that the client can operate, measure, and extend safely.
