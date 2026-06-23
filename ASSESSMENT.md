# Assessment Brief

## Role

Delivery Head, DotKonnekt

## Situation

DotKonnekt has been asked to lead the delivery of an AI-powered Customer Support and Product Discovery Assistant for a $500M retail enterprise.

The client has a large digital commerce footprint and an established support operation. Customer questions are currently handled across several channels, with long response times during busy periods and inconsistent answer quality across agents.

The client wants to use AI to improve customer experience, reduce support load, and make product discovery easier.

## Business Goals

The solution should:

- Answer customer questions using product catalogs, policies, FAQs, and manuals
- Recommend products based on customer intent and browsing or cart context
- Integrate with Shopify, Salesforce, and Zendesk
- Support 500,000+ monthly active users
- Keep response latency low enough for live customer interactions
- Meet enterprise expectations for security, governance, and compliance
- Leave room for future capabilities such as returns, refunds, and order tracking
- Run on AWS or GCP

## Current Client Environment

Assume the client has:

- Shopify as the primary commerce platform
- Salesforce as the customer and account system of record
- Zendesk for support ticketing and escalation
- A small internal engineering team that can support implementation
- Existing cloud infrastructure on either AWS or GCP
- Standard enterprise requirements for auditability, access control, privacy, and operational support

Where details are missing, state your assumptions.

## Expected Deliverables

### 1. Solution Proposal

Prepare a solution proposal that covers:

- High-level architecture
- AI and data architecture
- Integration approach for Shopify, Salesforce, and Zendesk
- Scalability design for 500,000+ monthly active users
- Security, compliance, and governance considerations
- Technology choices and rationale
- Important tradeoffs and alternatives considered

### 2. Delivery Plan

Prepare a delivery plan that explains:

- What you would validate during discovery
- MVP scope and why those capabilities ship first
- Timeline and major milestones
- Team structure and responsibilities
- Production rollout strategy
- Risks, dependencies, and mitigation plans

### 3. Engineering Leadership and Execution

Describe how you would run the team from day one:

- Team structure and onboarding
- Engineering standards
- Branching and release process
- CI/CD and environments
- Testing strategy
- Monitoring and operational readiness
- How you would handle common delivery challenges

### 4. Executive Presentation

Record a 15-minute presentation for client executives. The goal is not to read your documents aloud. The goal is to explain the recommended plan clearly enough that a senior stakeholder can make a decision.

## Success Measures

A strong submission should make it easy to see:

- What problem you are solving first
- Why your architecture is appropriate for the client
- How you avoid hallucinations and bad recommendations
- How the system scales and fails safely
- How the team gets from discovery to production
- What risks you see early and how you would manage them
- How you communicate tradeoffs without hiding uncertainty

## Helpful Assumptions

You may use these assumptions if you need a starting point:

- MVP target: 4 to 6 months
- Year-one budget: $1M to $2M
- Internal client team: 3 to 4 engineers available part-time
- Target p95 response time: under 2 seconds for common questions
- Target availability: 99.9%
- Initial channels: website chat and support handoff
- Future channels: email, SMS, social, and voice

You are free to challenge these assumptions if you explain why.
