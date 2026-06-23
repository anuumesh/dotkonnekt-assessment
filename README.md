# DotKonnekt Delivery Head Assessment

This repository contains the complete take-home assessment for the Delivery Head role at DotKonnekt. It is ready to share with candidates as-is.

The exercise is designed to evaluate how a candidate thinks through a real enterprise AI delivery problem: architecture, delivery sequencing, team leadership, risk management, and executive communication.

## Candidate Scenario

A $500M retail business wants to launch an AI-powered Customer Support and Product Discovery Assistant.

The assistant must answer customer questions, recommend products, integrate with existing enterprise systems, and scale to 500,000+ monthly active users. The Delivery Head is responsible for taking the engagement from discovery through production rollout.

The client environment includes:

- Shopify for commerce, product catalog, cart, and order context
- Salesforce for customer profile, account, and relationship history
- Zendesk for support tickets, escalation, and agent workflows
- AWS or GCP as the preferred cloud platform
- Enterprise requirements for security, privacy, governance, auditability, and operational support

## Candidate Deliverables

Candidates should submit four files:

```text
submissions/candidate-name/
  01-solution-proposal.md
  02-delivery-plan.md
  03-engineering-leadership.md
  04-presentation-link.md
```

The submission is scored across four areas:

| Area | Weight | What reviewers evaluate |
| --- | ---: | --- |
| Solution Proposal | 30% | Architecture, AI/data approach, integrations, scale, security, governance, and tradeoffs |
| Delivery Plan | 30% | Discovery plan, MVP scope, timeline, team model, rollout approach, dependencies, and risk management |
| Engineering Leadership | 30% | Team structure, onboarding, engineering standards, CI/CD, testing, operations, and leadership judgment |
| Executive Presentation | 10% | Clarity, confidence, senior-stakeholder communication, and ability to explain tradeoffs |

## What Good Looks Like

A strong response should:

- Make clear assumptions instead of hiding unknowns
- Explain why each major design decision was made
- Show how the system avoids hallucinations and unsafe answers
- Treat Shopify, Salesforce, and Zendesk as real enterprise integrations, not simple API calls
- Include a rollout plan with pilot, go-live criteria, rollback, and operational readiness
- Discuss cost, latency, data freshness, security, and governance
- Show how the Delivery Head would lead people, not only design technology
- Communicate clearly enough for both engineering and executive audiences

## Files In This Repository

| File | Purpose |
| --- | --- |
| `ASSESSMENT.md` | Full candidate brief |
| `RUBRIC.md` | Reviewer scoring guide |
| `STRUCTURE.md` | Repository and submission structure |
| `resources/templates/solution-proposal-template.md` | Complete candidate guidance for solution design |
| `resources/templates/delivery-plan-template.md` | Complete candidate guidance for planning and rollout |
| `resources/templates/engineering-leadership-template.md` | Complete candidate guidance for leadership and execution |
| `resources/examples/sample-submission-outline.md` | Example structure showing the expected depth and style |
| `PUSH_TO_GITHUB.md` | Publishing checklist for repository owners |

## Presentation Requirement

Candidates must record a 15-minute executive walkthrough with camera and screen share enabled. The audience should be treated as:

- CTO
- VP of Customer Experience
- Director of Engineering

The presentation should summarize the recommended solution, the delivery approach, the main risks, and the decisions required from the client.

## Use of AI Tools

Candidates may use AI tools for outlining, research support, or language polishing. The final judgment, architecture choices, tradeoffs, and delivery recommendations must be their own. Candidates should be prepared to discuss and defend every major decision.

## Contact

Questions can be sent to `hr@dotkonnekt.com`.
