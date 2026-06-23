# 04 - Executive Presentation Link

## Recording Link

Recording link: To be added after recording

## Presentation Details

Presenter: Umesh Yadav  
Audience: CTO, VP of Customer Experience, Director of Engineering  
Target duration: 15 minutes  
Format: Camera on and screen share on  

## Presentation Flow

### 1. Opening

Thank you for the opportunity to present my recommended approach for the Customer Support and Product Discovery Assistant.

My proposal is to launch a grounded AI assistant that starts with high-value support and product discovery use cases, integrates with Shopify and Zendesk first, uses Salesforce context selectively, and scales through a controlled rollout.

### 2. Business Problem

The client is dealing with high support volume, slow response times, inconsistent answer quality, and growing customer expectations. The assistant should reduce load on support teams while improving customer experience and product discovery.

The goal is not to replace the support team on day one. The goal is to automate common, lower-risk questions safely and escalate complex or sensitive issues with better context.

### 3. Architecture Summary

The architecture has five main layers:

- Customer channel through website chat
- API and orchestration layer
- Retrieval and AI layer
- Integration layer for Shopify, Salesforce, and Zendesk
- Operational layer for monitoring, audit, quality, and cost

I recommend retrieval-augmented generation because product and policy data changes frequently. The assistant should retrieve approved content before generating an answer. If it does not have enough evidence, it should escalate rather than guess.

### 4. Integration Strategy

Shopify is the main source for product catalog, inventory, cart, and order context.

Zendesk is the fallback and human escalation system. Escalated tickets should include the conversation summary, customer intent, retrieved sources, and confidence score.

Salesforce should be used carefully for authorized customer context, not as a dependency for the first MVP unless access and permissions are clear.

### 5. MVP Scope

The MVP should include:

- Product and policy Q&A
- Shopify catalog grounding
- Basic product recommendations
- Zendesk escalation
- Limited Salesforce context where approved
- Monitoring and audit logs
- AI quality review workflow

The MVP should defer:

- Full returns and refunds automation
- Autonomous order changes
- Multi-channel launch
- Deep personalization

### 6. Delivery Plan

I recommend a 20-week path:

- Weeks 1-3: Discovery
- Weeks 4-5: Architecture and setup
- Weeks 6-11: MVP build
- Weeks 12-14: Integration and hardening
- Weeks 15-17: Pilot rollout
- Weeks 18-20: Production rollout

The key is to validate data quality and AI accuracy early before expanding scope.

### 7. Risks and Mitigations

The main risks are:

- Product data quality
- LLM accuracy
- API limits
- Security and privacy review
- Scope growth
- Support workflow mismatch
- LLM cost

My mitigation approach is early discovery, conservative escalation, clear MVP boundaries, strong monitoring, and a controlled rollout.

### 8. Engineering Leadership

I would run the team as a focused product delivery team with clear ownership:

- Delivery Head for client alignment and risk
- Technical Lead for architecture and quality
- AI Engineer for retrieval, prompts, evaluation, and guardrails
- Backend and Data Engineers for APIs and ingestion
- Platform Engineer for CI/CD and operations
- QA for testing and release confidence
- Product Manager for journeys and acceptance criteria

The team should demo frequently, test AI quality continuously, and prepare for production from the beginning.

### 9. Success Metrics

Success should be measured by:

- Query resolution rate
- Response latency
- Escalation quality
- Answer accuracy
- Support ticket reduction
- Customer satisfaction
- Cost per conversation
- Production stability

### 10. Closing

My recommendation is to launch a focused, grounded, and measurable assistant first, then expand once trust and operational stability are proven.

This gives the client early value while protecting customer experience, security, and long-term extensibility.

## Recording Checklist

- Camera on
- Screen share on
- Speak to executive audience, not only engineering audience
- Keep duration close to 15 minutes
- Cover recommendation, delivery plan, risks, and leadership approach
- Add the final Loom, Google Drive, or Teams recording link at the top of this file
