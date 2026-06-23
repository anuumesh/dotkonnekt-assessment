## 1. Delivery Principles

Recommended principles:

- Validate business value and data quality before committing to build scope.
- Reduce the largest unknowns during discovery.
- Keep MVP focused on reliable customer support and safe escalation.
- Ship in stages with measurable go/no-go criteria.
- Treat AI quality, security, and operations as core delivery work.
- Communicate risks early and plainly.

## 2. Discovery Phase

Recommended duration: 3 weeks.

| Week | Focus | Outputs |


| --- | --- | --- |
| Week 1 | Stakeholder interviews, system access, current support workflow review | Current-state map, integration inventory, initial risk register |
| Week 2 | Data audit, AI feasibility tests, sample retrieval pipeline, security review | Data quality report, accuracy baseline, security constraints |
| Week 3 | MVP scope, architecture decision, delivery plan, commercial assumptions | MVP definition, roadmap, staffing plan, go/no-go recommendation |

Discovery should validate:

- Top support categories by volume and business impact
- Quality and completeness of product, FAQ, manual, and policy content
- Shopify, Salesforce, and Zendesk API access patterns
- Authentication and consent requirements
- Current escalation workflows
- Latency and availability expectations
- Compliance requirements such as GDPR, CCPA, SOC 2, and data retention

## 3. MVP Scope

Recommended MVP scope:

| Capability | Include in MVP | Reason |
| --- | --- | --- |
| Product and policy Q&A | Yes | Core customer support value |
| Shopify catalog grounding | Yes | Required for product discovery and accurate answers |
| Zendesk escalation | Yes | Needed for safe fallback and support continuity |
| Basic product recommendations | Yes, limited | Valuable but should be grounded and explainable |
| Salesforce customer context | Limited | Include only approved fields and high-value use cases |
| Returns/refunds automation | No | High-risk workflow; defer until trust and controls are proven |
| Order tracking | No, unless data access is already simple | Useful follow-on feature |
| Multi-channel support | No | Start with website assistant; expand later |
| Advanced personalization | No | Defer until core accuracy is stable |

MVP success criteria:

| Metric | Target |
| --- | ---: |
| Query resolution without human escalation | 70-80% for common categories |
| p95 latency | Under 2 seconds for common queries |
| Availability | 99% during pilot, 99.9% for production |
| Human-reviewed answer accuracy | 90%+ during MVP, improving toward 95% |
| Critical security incidents | 0 |
| Zendesk escalation context completeness | 95%+ of escalated tickets include summary and source context |

## 4. Delivery Timeline

Recommended timeline: 20 weeks for production rollout.

| Phase | Duration | Outcome |
| --- | --- | --- |
| Discovery | Weeks 1-3 | Requirements, data assessment, AI baseline, MVP scope, risk plan |
| Architecture and setup | Weeks 4-5 | Architecture finalized, environments ready, CI/CD baseline established |
| MVP build | Weeks 6-11 | Assistant API, retrieval pipeline, Shopify sync, Zendesk escalation, basic UI/channel integration |
| Integration and hardening | Weeks 12-14 | End-to-end testing, security review, load testing, monitoring, runbooks |
| Pilot rollout | Weeks 15-17 | Limited user group or limited traffic, daily monitoring, feedback loop |
| Production rollout | Weeks 18-20 | Progressive rollout, executive go-live, operational handover |

Key decision gates:

- End of Week 3: Go/no-go for MVP build
- End of Week 8: Integration risk review
- End of Week 14: Production readiness review
- End of Week 17: Pilot success review
- End of Week 20: Full rollout and phase-two roadmap

## 5. Team and Ownership

Recommended core team:

| Role | Responsibility | Allocation |
| --- | --- | --- |
| Delivery Head | Owns client relationship, scope, plan, risks, stakeholder alignment, and delivery outcomes | Full-time |
| Technical Lead | Owns architecture, technical decisions, review quality, and engineering execution | Full-time |
| AI/LLM Engineer | Owns retrieval, prompt design, model evaluation, guardrails, and answer quality | Full-time |
| Backend Engineer | Owns APIs, session flow, orchestration, auth, and integration services | Full-time |
| Data Engineer | Owns ingestion, indexing, data quality, and source synchronization | Full-time or part-time |
| Platform/DevOps Engineer | Owns cloud infrastructure, CI/CD, monitoring, security automation, and release process | Part-time to full-time |
| QA Engineer | Owns test strategy, regression coverage, E2E tests, and release validation | Full-time |
| Product Manager | Owns requirements, prioritization, user journeys, and business acceptance | Part-time to full-time |
| Client SMEs | Provide product, policy, support, compliance, and system knowledge | Part-time |

## 6. Rollout Plan

Recommended rollout:

1. Internal test with DotKonnekt and client SMEs.
2. Support-agent pilot using real historical questions.
3. Limited customer pilot on low-risk categories.
4. Canary rollout to 5-10% website traffic.
5. Progressive rollout to 25%, 50%, 75%, then 100%.
6. Stabilization period with daily metric review.

Go-live criteria:

- Critical and high security findings closed or accepted by the client
- p95 latency under agreed target
- Escalation workflows verified with Zendesk
- Production dashboards and alerts active
- Rollback procedure tested
- Support team trained
- Executive sponsor approves rollout

Rollback triggers:

- Error rate above 5% for 5 minutes
- p95 latency above 5 seconds for 5 minutes
- Incorrect answer pattern affecting customer trust
- Data exposure or security incident
- Zendesk escalation failure

## 7. Risks and Mitigations

| Risk | Impact | Early signal | Mitigation | Owner |
| --- | --- | --- | --- | --- |
| Poor product data quality | Assistant gives incomplete or wrong answers | Missing fields, outdated descriptions, duplicate SKUs | Data audit in discovery, content cleanup backlog, source confidence scoring | Data Engineer |
| LLM accuracy below target | Low trust and high escalations | Human review score below 90% | Improve retrieval, add guardrails, refine prompts, escalate more conservatively | AI Engineer |
| Shopify API limits | Latency or stale product data | Rate-limit errors, slow API calls | Cache product data, use webhooks, batch sync, retry with backoff | Backend Engineer |
| Salesforce access delays | Personalization scope slips | Delayed credentials or unclear field permissions | Make Salesforce optional for MVP, define approved fields early | Delivery Head |
| Zendesk workflow mismatch | Poor handoff to agents | Agents reject or rework escalated tickets | Design escalation with support leads, test with real tickets | Product Manager |
| Security review late findings | Go-live delay | Open questions on PII, retention, vendor controls | Start threat modeling in discovery, involve security early | Platform Engineer |
| Scope growth | Timeline and quality risk | New features added before MVP freeze | Change control, phase-two backlog, steering committee decisions | Delivery Head |
| LLM cost spike | Budget overrun | Cost per conversation trending above target | Token budgets, caching, smaller models for routing, usage dashboards | AI Engineer |

## 8. Communication Plan

Recommended cadence:

| Meeting | Frequency | Purpose |
| --- | --- | --- |
| Engineering standup | Daily | Progress, blockers, technical coordination |
| Delivery risk review | Twice weekly | Scope, timeline, risks, dependencies |
| Client working session | Weekly | Decisions, demos, data/access issues |
| Executive steering | Every 2 weeks | Milestones, risks, budget, go/no-go decisions |
| Demo review | Every sprint | Show working software and collect feedback |
| Production readiness review | Before pilot and before full rollout | Confirm operational readiness |

## 9. Final Delivery Recommendation

The recommended delivery path is a focused MVP with strong grounding, safe escalation, and measurable production readiness. The first release should prove that the assistant can answer common product and support questions reliably, integrate with Shopify and Zendesk, and operate safely under real traffic. Personalization, returns, refunds, order tracking, and additional channels should follow after the initial system has proven accuracy, stability, and support-team adoption.
