# Evaluation Rubric

We score the assessment across four areas. The best responses are clear, practical, and opinionated. They do not need to be long, but they should show real delivery judgment.

## Scoring Summary

| Category | Weight |
| --- | ---: |
| Solution Design and Tradeoffs | 30% |
| Delivery Strategy | 30% |
| Engineering Leadership and Execution | 30% |
| Executive Communication | 10% |

## 1. Solution Design and Tradeoffs

Excellent responses:

- Present an architecture that fits the scale, risk, and business context
- Explain the AI approach clearly, especially grounding, retrieval, and escalation
- Show how Shopify, Salesforce, and Zendesk fit into the system
- Include security, privacy, observability, and governance in the core design
- Discuss alternatives and explain why the selected path is appropriate
- Identify likely failure modes and design around them

Weaker responses usually:

- Rely on buzzwords without explaining system behavior
- Ignore latency, cost, data freshness, or operational complexity
- Treat security and compliance as afterthoughts
- Assume the model will be accurate without describing controls

## 2. Delivery Strategy

Excellent responses:

- Start with a strong discovery phase that validates data, integrations, users, and risk
- Define a focused MVP with a clear reason for what is in and out
- Sequence work in a way that reduces uncertainty early
- Include a credible rollout plan with pilot, canary, rollback, and go-live criteria
- Show realistic timelines, dependencies, and decision points
- Assign ownership for risks instead of simply listing them

Weaker responses usually:

- Jump straight into implementation
- Propose an MVP that is too large or too vague
- Give optimistic timelines without explaining assumptions
- Miss integration risk or client dependency management

## 3. Engineering Leadership and Execution

Excellent responses:

- Define a team structure that matches the work
- Explain how people will onboard and become productive
- Set clear engineering standards without creating unnecessary process
- Include testing, review, deployment, and incident practices
- Show how quality is protected under delivery pressure
- Demonstrate how the Delivery Head makes decisions and handles conflict

Weaker responses usually:

- Describe ceremonies without explaining outcomes
- Ignore team ramp-up and ownership
- Skip testing strategy or operational readiness
- Sound generic instead of grounded in this project

## 4. Executive Communication

Excellent presentations:

- Explain the recommendation in plain language
- Focus on business outcomes, tradeoffs, risks, and next steps
- Use visuals effectively
- Stay close to 15 minutes
- Feel confident, concise, and prepared

Weaker presentations usually:

- Read the document line by line
- Go too deep into implementation details for the audience
- Avoid hard tradeoffs
- Miss the requested camera or screen share

## Overall Interpretation


| Score | Interpretation |
| ---: | --- |
| 90-100 | Outstanding. Strong signal for senior delivery leadership. |
| 80-89 | Very strong. Clear next-round candidate. |
| 70-79 | Good. Worth continuing if experience also aligns. |
| 60-69 | Mixed. Some useful thinking, but important gaps remain. |
| Below 60 | Not yet at the expected level for this role. |


## What We Value Most

- Clear judgment
- Practical sequencing
- Honest tradeoffs
- Strong communication
- Awareness of people, process, and production realities

## Common Mistakes

- Designing a complex system before validating the data
- Assuming one LLM call solves the whole problem
- Forgetting human escalation
- Ignoring cost and latency
- Treating integrations as simple API calls
- Leaving monitoring, support, and rollback until the end
- Submitting a generic AI architecture that could apply to any of the company
