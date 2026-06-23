# 02 - Delivery Plan

## Delivery Approach

My delivery approach is to reduce uncertainty early, ship a focused MVP, and move to production through controlled rollout rather than a single high-risk launch.

The biggest delivery risks are not only technical. They include poor source data quality, unclear ownership of business rules, delayed access to Shopify/Salesforce/Zendesk, unrealistic scope, and insufficient operational readiness. The plan therefore starts with discovery and feasibility validation before full build.

## Delivery Principles

- Validate data quality before building the full assistant.
- Prove AI accuracy with real client content early.
- Keep MVP focused on common support and product discovery.
- Escalate safely instead of guessing.
- Treat security, monitoring, and support handoff as launch requirements.
- Show progress through frequent demos.
- Use pilot rollout and clear go/no-go gates.

## Phase 1: Discovery

Recommended duration: 3 weeks.

### Objectives

- Understand the client’s support workflows and top ticket categories.
- Review available product, policy, FAQ, manual, and support data.
- Validate Shopify, Salesforce, and Zendesk access.
- Run a small AI feasibility test using real content.
- Confirm security, privacy, and compliance constraints.
- Define MVP scope and success metrics.

### Discovery Plan

| Week | Activities | Deliverables |
| --- | --- | --- |
| Week 1 | Stakeholder interviews, support workflow review, access planning, current architecture review | Current-state map, integration inventory, initial risk register |
| Week 2 | Product data audit, policy/FAQ review, AI retrieval prototype, security/compliance review | Data quality report, AI accuracy baseline, security constraints |
| Week 3 | MVP scope definition, target architecture, staffing plan, delivery roadmap, go/no-go review | MVP backlog, delivery plan, milestone plan, executive recommendation |

### Discovery Stakeholders

- CTO or engineering sponsor
- VP of Customer Experience
- Support operations lead
- Shopify owner
- Salesforce owner
- Zendesk administrator
- Security/compliance lead
- Product/catalog manager
- Data/analytics owner

### Discovery Exit Criteria

- MVP scope agreed.
- Integration access path confirmed.
- Product and policy data quality understood.
- AI baseline accuracy measured.
- Security constraints documented.
- First release risks and mitigations agreed.

## Phase 2: MVP Scope

The MVP should prove value without over-automating sensitive workflows.

### In Scope

| Capability | Reason |
| --- | --- |
| Website assistant | Fastest path to customer-facing value |
| Product and policy Q&A | Highest-value support use case |
| Shopify catalog grounding | Required for product discovery and recommendations |
| Basic product recommendations | Direct business value for retail |
| Zendesk escalation | Safe fallback and support continuity |
| Limited Salesforce context | Useful for authenticated personalization where approved |
| Monitoring and audit logs | Required for production trust |
| AI quality review | Needed to improve and govern answers |

### Out of Scope for MVP

| Capability | Reason for deferral |
| --- | --- |
| Full returns/refunds automation | High-risk transaction workflow |
| Autonomous order changes | Requires stronger controls and business approval |
| Voice/social/email channels | Adds channel complexity before core assistant is proven |
| Deep personalization | Requires more data governance and testing |
| Self-hosted LLM | Slower path to MVP and higher operational burden |

## Phase 3: Timeline and Milestones

Recommended timeline: 20 weeks.

| Phase | Duration | Milestone |
| --- | --- | --- |
| Discovery | Weeks 1-3 | Go/no-go and MVP scope signed off |
| Architecture and setup | Weeks 4-5 | Environments, CI/CD, architecture, and backlog ready |
| MVP build | Weeks 6-11 | Core assistant, retrieval, Shopify sync, Zendesk escalation complete |
| Integration and hardening | Weeks 12-14 | E2E testing, security review, performance testing, monitoring |
| Pilot rollout | Weeks 15-17 | Limited rollout with daily quality and stability review |
| Production rollout | Weeks 18-20 | Progressive rollout and operational handover |

## Team Structure

| Role | Responsibility | Allocation |
| --- | --- | --- |
| Delivery Head | Owns delivery plan, client alignment, scope, risk, and executive communication | Full-time |
| Technical Lead | Owns architecture, technical decisions, and engineering quality | Full-time |
| AI/LLM Engineer | Owns retrieval, prompts, evaluation, guardrails, and quality metrics | Full-time |
| Backend Engineer | Owns APIs, integrations, session flow, and orchestration | Full-time |
| Data Engineer | Owns ingestion, indexing, data quality, and source sync | Full-time or part-time |
| Platform/DevOps Engineer | Owns cloud, CI/CD, observability, security automation, and release process | Part-time to full-time |
| QA Engineer | Owns test strategy, regression, E2E, and release validation | Full-time |
| Product Manager | Owns requirements, user journeys, prioritization, and acceptance criteria | Part-time to full-time |
| Client SMEs | Provide product, support, compliance, and systems expertise | Part-time |

## Delivery Workstreams

### AI and Knowledge

- Source content audit
- Retrieval pipeline
- Prompt design
- Guardrails
- Evaluation dataset
- Quality review workflow

### Integrations

- Shopify catalog sync and selected real-time lookup
- Salesforce approved customer context
- Zendesk ticket creation and handoff
- Retry, timeout, and fallback handling

### Platform and Operations

- Environments
- CI/CD
- Monitoring
- Logging and audit
- Cost tracking
- Runbooks
- Deployment and rollback

### Product and QA

- Customer journeys
- Acceptance criteria
- E2E scenarios
- Regression tests
- Pilot feedback
- Go-live readiness

## Rollout Plan

### Step 1: Internal Validation

Use internal DotKonnekt and client SMEs to test common and edge-case questions.

Exit criteria:

- Major known categories tested
- Escalation flow verified
- No critical defects
- Initial accuracy target met

### Step 2: Support-Agent Pilot

Allow support agents to test the assistant using real historical tickets and current knowledge content.

Exit criteria:

- Agents confirm ticket summaries are useful
- Wrong-answer categories identified
- Knowledge gaps captured

### Step 3: Limited Customer Pilot

Expose the assistant to a small percentage of traffic or a low-risk customer group.

Exit criteria:

- p95 latency within target
- Error rate below threshold
- Escalation working reliably
- Customer feedback acceptable

### Step 4: Progressive Rollout

Move from 5-10% traffic to 25%, 50%, 75%, and 100%, with monitoring at each stage.

Rollback triggers:

- API error rate above 5% for 5 minutes
- p95 latency above 5 seconds for 5 minutes
- Zendesk ticket creation failure
- Security or data exposure incident
- Repeated harmful or incorrect answer pattern

## Risks and Mitigations

| Risk | Impact | Mitigation | Owner |
| --- | --- | --- | --- |
| Product data quality is poor | Wrong or incomplete answers | Audit early, create cleanup backlog, score source confidence | Data Engineer |
| LLM accuracy is below target | Low trust, high escalation | Improve retrieval, refine prompts, add guardrails, reduce MVP scope if needed | AI Engineer |
| Shopify API limits cause latency | Slow or failed responses | Cache, use webhooks, batch sync, restrict real-time calls | Backend Engineer |
| Salesforce access is delayed | Personalization slips | Keep Salesforce optional for MVP and use general support flow | Delivery Head |
| Zendesk workflow does not match support operations | Poor handoff | Design ticket fields and routing with support leads | Product Manager |
| Security review finds late issues | Launch delay | Start threat modeling in discovery and review architecture early | Platform Engineer |
| Scope expands before MVP | Timeline and quality risk | Use steering committee change control and phase-two backlog | Delivery Head |
| LLM cost exceeds forecast | Budget pressure | Token budgets, caching, usage dashboards, smaller models for routing | AI Engineer |

## Communication Plan

| Cadence | Audience | Purpose |
| --- | --- | --- |
| Daily | Delivery team | Progress, blockers, coordination |
| Twice weekly | Delivery Head, Tech Lead, Product, QA | Risk and dependency review |
| Weekly | Client working group | Demo, decisions, access issues, feedback |
| Every 2 weeks | Executive steering committee | Milestones, risks, timeline, budget, go/no-go decisions |
| During pilot | Delivery and support teams | Daily metric review and incident handling |

## Success Metrics

### Technical Metrics

- p95 latency under 2 seconds for common questions
- Availability of 99.9% at production scale
- Error rate under 0.1%
- Zendesk escalation success above 99%
- LLM cost per conversation within agreed budget

### AI Quality Metrics

- 90%+ human-reviewed accuracy during MVP
- Clear reduction in unsupported or hallucinated answers
- Escalation for sensitive categories
- Continuous improvement from support feedback

### Business Metrics

- 70-80% resolution for common support questions during MVP
- Reduced support ticket volume in targeted categories
- Improved customer response time
- Improved product discovery engagement
- Positive support-agent feedback on escalated ticket context

## Final Recommendation

The delivery should proceed through a focused MVP, not a broad automation program. The right first milestone is a grounded assistant that answers common support and product questions, recommends products safely, escalates to Zendesk with context, and gives the client strong monitoring and governance.

Once this system is stable, the roadmap can expand into order tracking, returns, refunds, deeper personalization, and additional customer channels.
