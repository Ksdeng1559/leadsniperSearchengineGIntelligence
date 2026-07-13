# LinkedIn GTM Solution Bridge

## Status

Development specification only. This feature must remain disabled in production until authentication, privacy, platform-policy, human-approval, and end-to-end tests pass.

## Objective

Convert an audited domain's Search Growth, Community Intelligence, LinkedIn Topic Radar, Zero Keyword Discovery, conversion, and business-growth findings into an evidence-backed LinkedIn go-to-market solution.

The bridge should answer:

1. Which LinkedIn audiences are commercially relevant to this domain?
2. Which observable business problems, goals, and growth signals should shape the GTM motion?
3. What authority content should the business publish?
4. Which accounts and roles merit human research?
5. What permission-based conversation, personalized Vidyard video, assessment, or referral action should be recommended?
6. How did LinkedIn-influenced activity affect conversations, assessments, opportunities, and revenue?

This is a recommendation and orchestration layer. It must not become a LinkedIn scraping, mass-connection, or autonomous direct-message system.

## Product boundary

### In scope

- Translate domain-audit evidence into ICPs, buyer roles, pains, triggers, offers, content pillars, and CTAs.
- Combine search demand, zero-keyword signals, community language, competitor gaps, and LinkedIn Topic Radar evidence.
- Generate a domain-specific LinkedIn GTM Solution with source attribution and confidence.
- Recommend accounts and contacts for human research from permitted sources.
- Prepare human-reviewed connection notes, messages, follow-ups, and Vidyard video briefs.
- Deliver approved email through Unipile-connected Gmail and synchronize supported conversations.
- Send Vidyard links through approved LinkedIn, email, or consented WhatsApp conversations.
- Create and update companies, contacts, opportunities, consent, tasks, and attribution in Atomic CRM.
- Track content, conversations, video engagement, assessments, appointments, qualified opportunities, and revenue.
- Support development fixtures and simulation without external sending.

### Out of scope

- Automated LinkedIn connection requests, likes, comments, follows, profile visits, or direct messages.
- Circumventing LinkedIn limits, authentication, or access controls.
- Scraping private, login-protected, or member-only LinkedIn content.
- Sending WhatsApp, SMS, or marketing email without the required consent and identification.
- Inferring sensitive personal characteristics.
- Automated financial eligibility, lender approval, or credit decisions.
- Production credentials, production sending, or live financial representations in this PR.

## User stories

### Consultant or advisor

- As an advisor, I can audit a domain and receive a LinkedIn GTM recommendation aligned with the business's actual services and market.
- I can review the evidence behind every recommended audience, topic, offer, signal, and message.
- I can approve, revise, reject, or defer every outbound action.
- I can record a short Vidyard video from a safe, evidence-backed briefing.
- I can see which LinkedIn-influenced activities created qualified opportunities.

### Business owner

- As a business owner, I can understand why the recommended LinkedIn strategy fits my domain.
- I can choose growth objectives, regions, industries, offers, exclusions, capacity, and risk constraints.
- I can approve messaging, content themes, channel transitions, and data retention.
- I can see outcomes without fabricated reach, demand, pipeline, or revenue.

### Developer

- As a developer, I can use typed contracts, fixtures, provider adapters, feature flags, idempotency keys, and audit logs.
- I can test the complete workflow without sending a real LinkedIn message, email, or WhatsApp message.

## End-to-end flow

1. User selects a completed domain audit.
2. System loads normalized domain, service, location, audience, keyword, competitor, community, topic, and growth-signal evidence.
3. GTM Context Builder proposes objectives, offers, ICP segments, buyer roles, exclusions, sales motion, and success metrics.
4. User confirms or edits the proposed context.
5. Strategy Generator produces:
   - positioning and category
   - ICP and role matrix
   - pain, desired outcome, objection, and trigger map
   - authority-content pillars
   - 30/60/90-day publishing plan
   - account-research criteria
   - lead magnet, assessment, calculator, webinar, and Vidyard plays
   - channel and follow-up recommendations
6. Evidence Engine attaches sources, timestamps, data status, confidence, and assumptions.
7. Opportunity Engine scores accounts and recommends next-best actions.
8. Human operator approves content drafts and individual conversation actions.
9. Unipile synchronizes supported conversations and sends only explicitly approved email or consented messages.
10. Vidyard hosts personalized videos and returns available engagement evidence.
11. Atomic CRM stores the complete relationship, consent, activity, and opportunity timeline.
12. Analytics attributes LinkedIn-influenced outcomes without treating correlation as guaranteed causation.

## Domain-to-GTM mapping

| Audit evidence | GTM interpretation | Possible action |
| --- | --- | --- |
| High-value keyword gaps | Buyer interest not addressed by the domain | Authority post, article, checklist, or service offer |
| Zero/emerging keyword | Early problem language | Founder viewpoint, question post, short video, monitoring |
| Community pain cluster | Voice-of-customer language | Educational post, FAQ, assessment question |
| Competitor complaint | Trust or service gap | Differentiated positioning and proof asset |
| Weak conversion path | Interest without clear next step | Assessment, calculator, resource, or appointment CTA |
| Growth/funding signal | Possible commercial transition | Human-reviewed research and permission-based conversation |
| LinkedIn breakout topic | Current professional attention | Timely content with cross-source validation |
| Local opportunity | Geographic relevance | Local business-owner or partner content |
| Evidence uncertainty | Insufficient basis | Monitor, request context, or reject recommendation |

## Core modules

### 1. GTM Context Builder

Inputs:

- domain and canonical pages
- products and services
- geography and language
- business model and typical transaction value
- target customer and excluded audience
- primary growth objective
- delivery capacity and sales-cycle assumptions
- regulated-service and claim constraints
- approved channels and consent basis

Outputs:

- confirmed GTM context
- unresolved questions
- assumptions and confidence
- versioned approval record

No strategy may be activated from inferred context alone. A human must confirm the operating context.

### 2. ICP and Buying-Committee Generator

Produce:

- company attributes
- industries
- employee/revenue bands where evidence supports them
- geography
- operating maturity
- decision-maker roles
- influencers and centres of influence
- observable trigger signals
- disqualifiers and exclusions
- likely objective, objection, and decision criteria
- recommended content and conversation entry point

Keep company fit separate from person identity confidence.

### 3. LinkedIn Authority Planner

Generate:

- profile-positioning recommendation
- content pillars and topic clusters
- weekly cadence
- document/carousel concepts
- newsletter concept
- partner-collaboration opportunities
- comment and community-participation themes
- content-to-offer mappings
- reusable intellectual-property frameworks
- 30/60/90-day content calendar

Every topic must link to audit evidence or be clearly marked as a strategic hypothesis.

### 4. Account Opportunity Radar

Account priority dimensions:

| Dimension | Weight |
| --- | ---: |
| Trigger or funding/growth signal | 25 |
| ICP fit | 20 |
| Domain-service alignment | 15 |
| Timing evidence | 15 |
| Relationship proximity | 10 |
| Decision-maker confidence | 10 |
| Evidence completeness | 5 |

The score prioritizes human research. It is not a credit, eligibility, or protected-class score.

Required output:

- account
- reason for recommendation
- supporting evidence
- relevant role
- timing hypothesis
- confidence
- recommended next-best action
- prohibited claims
- human-review status

### 5. Conversation Workbench

Prepare but do not automatically send:

- public-comment suggestion
- connection context
- post-acceptance value message
- permission request
- resource delivery
- Vidyard video invitation
- discovery invitation
- milestone follow-up
- stop/opt-out handling

Rules:

- Reference only corroborated, non-sensitive evidence.
- Never invent familiarity or claim to have observed private activity.
- One clear objective per message.
- Avoid a booking link or attachment in an unsolicited first message.
- Require approval per recipient and action.
- Respect clear declines, channel preferences, opt-outs, and suppression lists.
- Keep platform-specific rate and safety controls configurable.
- Do not advertise guaranteed outcomes.

### 6. Vidyard Sales-Interest Bridge

Use Vidyard as the personalized video engagement layer.

Video play types:

- 30–75 second signal-based introduction
- domain audit observation
- expansion or commercial-property funding explanation
- personalized readiness review
- assessment recap
- partner introduction
- milestone follow-up
- short personal introduction followed by a reusable educational playlist

Video brief contract:

- recipient and company
- approved source signal
- opening acknowledgment
- one useful observation
- one decision framework
- one permission-based CTA
- required disclaimer
- prohibited claims
- expiration/retention policy
- human approver

Delivery:

- LinkedIn: approved link in an existing/eligible conversation
- Gmail: animated or static thumbnail linking to Vidyard
- WhatsApp: link or supported attachment only in a consented conversation
- CRM: store player/video reference, not raw video bytes unless required

Engagement events should be provider-capability aware. Do not promise viewer-level or real-time events unless the selected Vidyard plan and API return them. Treat email opens as weak evidence. Page visits, meaningful watch progress, replies, assessment starts, and appointments are stronger intent signals.

### 7. Unipile Unified Communications Bridge

Supported responsibilities:

- connect and identify Google, Microsoft, IMAP, LinkedIn, WhatsApp, Instagram, Messenger, Telegram, and calendar accounts according to provider support
- send approved email with a Vidyard link and tracked CTA
- synchronize messages, replies, email threads, and supported delivery/read data
- receive webhook events
- preserve provider message, thread, chat, and account identifiers
- route events to Atomic CRM using idempotency keys

LinkedIn actions remain human-approved. Unipile integration does not override LinkedIn policy or the application's prohibition on autonomous outreach.

For email:

- use connected Gmail/Microsoft/IMAP account
- support HTML thumbnail/link and plain-text fallback
- permit attachments only when explicitly requested and within provider limits
- use open/click tracking only when lawful and disclosed as required
- attach campaign/video labels for attribution

### 8. Atomic CRM Bridge

Entities:

- Workspace
- DomainAudit
- GTMStrategy
- Company
- Contact
- Relationship
- Evidence
- Signal
- Opportunity
- Consent
- ChannelIdentity
- Conversation
- Message
- VideoAsset
- VideoEngagement
- ContentAsset
- Campaign
- Task
- Approval
- Suppression
- AttributionEvent
- AuditLog

Suggested opportunity lifecycle:

`identified -> researching -> reviewed -> approved_for_contact -> conversation -> assessment -> discovery -> qualified -> nurture -> referred_or_submitted -> won_or_funded -> lost_or_disqualified`

Required controls:

- tenant isolation
- immutable source and consent timestamps
- idempotent webhook processing
- human approval identity and timestamp
- retention/deletion workflows
- suppression across channels
- least-privilege access
- PII redaction in logs and prompts

## Data contracts

### GTM solution

```ts
type LinkedInGTMSolution = {
  id: string;
  workspaceId: string;
  domainAuditId: string;
  status: "draft" | "needs_context" | "ready_for_review" | "approved" | "archived";
  objective: string;
  market: { countries: string[]; regions: string[]; languages: string[] };
  positioning: { category: string; promise: string; differentiators: string[] };
  icpSegments: ICPSegment[];
  contentPillars: ContentPillar[];
  offers: Offer[];
  accountCriteria: AccountCriteria;
  channelPolicy: ChannelPolicy;
  metrics: MetricDefinition[];
  evidenceIds: string[];
  assumptions: string[];
  confidence: number | null;
  createdAt: string;
  approvedAt: string | null;
  approvedBy: string | null;
};
```

### Next-best action

```ts
type GTMNextBestAction = {
  id: string;
  companyId: string;
  contactId: string | null;
  type:
    | "research"
    | "engage_publicly"
    | "request_connection"
    | "send_resource"
    | "request_video_permission"
    | "send_vidyard"
    | "invite_assessment"
    | "schedule_review"
    | "do_not_contact";
  rationale: string;
  evidenceIds: string[];
  confidence: number | null;
  requiresHumanApproval: true;
  status: "proposed" | "approved" | "rejected" | "executed" | "expired";
  expiresAt: string | null;
};
```

### Communication event

```ts
type UnifiedCommunicationEvent = {
  idempotencyKey: string;
  provider: "linkedin" | "gmail" | "microsoft" | "imap" | "whatsapp" | "instagram" | "messenger" | "telegram";
  accountId: string;
  providerEventId: string;
  threadId: string | null;
  direction: "inbound" | "outbound";
  eventType: "message" | "reply" | "delivered" | "read" | "clicked" | "failed";
  contactId: string | null;
  campaignId: string | null;
  videoId: string | null;
  occurredAt: string;
  payloadReference: string | null;
};
```

## UI requirements

Add a top-level **LinkedIn GTM** workspace reachable from a completed audit.

Views:

1. **GTM Executive Brief**
   - objective, positioning, ICP, offer, top evidence, unresolved context
2. **Audience & Signal Map**
   - segments, roles, triggers, exclusions, evidence confidence
3. **Authority Planner**
   - pillars, topics, posts, newsletter, collaborations, calendar
4. **Account Opportunity Radar**
   - prioritization, evidence, role, timing, next-best action
5. **Conversation Workbench**
   - drafts, resources, video briefs, approvals, suppression
6. **Vidyard Engagement**
   - sent, started, completion where available, CTA, reply, appointment
7. **GTM Funnel**
   - content -> profile/conversation -> resource/video -> assessment -> meeting -> opportunity
8. **Evidence Drawer**
   - source, query, excerpt, URL, collection time, data status, confidence
9. **Settings & Governance**
   - connections, channel permissions, feature flags, rate limits, retention, consent, test mode

Every screen must distinguish:

- measured provider data
- calculated metrics
- model-generated recommendations
- user-confirmed context
- estimates and assumptions
- unavailable data

## API boundaries

Suggested protected server routes:

```text
POST /api/gtm-solutions
GET  /api/gtm-solutions/:id
POST /api/gtm-solutions/:id/context/confirm
POST /api/gtm-solutions/:id/generate
POST /api/gtm-solutions/:id/approve
GET  /api/gtm-solutions/:id/accounts
POST /api/gtm-actions/:id/approve
POST /api/gtm-actions/:id/reject
POST /api/videos/vidyard/briefs
POST /api/videos/vidyard/link
POST /api/webhooks/vidyard
POST /api/webhooks/unipile
POST /api/communications/email/send
POST /api/communications/message/send
GET  /api/gtm-solutions/:id/analytics
```

All mutating routes require authentication, authorization, validation, audit logging, idempotency, and tenant scoping.

## Provider adapters

Define interfaces so vendors can be replaced:

- `SearchIntelligenceProvider`
- `CommunityIntelligenceProvider`
- `LinkedInEvidenceProvider`
- `VideoProvider`
- `UnifiedMessagingProvider`
- `CRMProvider`
- `AnalyticsProvider`

Do not call provider APIs from browser code. Store credentials only in protected server-side configuration.

## Feature flags

```text
LINKEDIN_GTM_ENABLED=false
LINKEDIN_GTM_FIXTURE_MODE=true
LINKEDIN_OUTBOUND_ENABLED=false
UNIPILE_SYNC_ENABLED=false
UNIPILE_SEND_ENABLED=false
VIDYARD_ENABLED=false
ATOMIC_CRM_WRITE_ENABLED=false
```

Production sending must require both the relevant environment flag and an explicit in-product human approval.

## Analytics

North-star metric:

**Qualified opportunities created from LinkedIn-influenced relationships**

Supporting measures:

- relevant follower and profile engagement where available
- target-account conversations
- permission-to-send-video rate
- Vidyard start and meaningful completion rate
- reply rate
- assessment starts and completions
- appointments
- qualified opportunities
- opportunity value
- won/funded or referred outcomes
- time from first evidence to qualified opportunity
- opt-out and complaint rate
- evidence and consent completeness

Attribution states:

- direct
- influenced
- assisted
- unknown

Never present attributed revenue as guaranteed causation.

## Security, privacy, and compliance

- Use public or properly authorized data only.
- Do not bypass access controls or automate prohibited LinkedIn activity.
- Do not place secrets, financial documents, government identifiers, or high-risk PII in prompts, analytics, video titles, thumbnails, or URLs.
- Encrypt credentials and sensitive stored data.
- Verify webhook signatures or equivalent provider authenticity controls where supported.
- Use opaque internal identifiers in links.
- Apply CASL, applicable privacy rules, provider policies, consent, identification, and opt-out requirements.
- Require human review for regulated or financial-service claims.
- Maintain cross-channel suppression.
- Provide retention, export, correction, and deletion controls.
- Store short attributed evidence and structured observations rather than copying protected source material.
- Log every approval, send, status change, and material recommendation.

## Failure states

Support:

- partial audit evidence
- missing domain context
- low-confidence recommendation
- disconnected provider account
- expired authorization
- provider rate limit
- unsupported attachment or message type
- duplicate webhook
- stale approval
- suppressed recipient
- withdrawn consent
- failed CRM write
- video unavailable
- unavailable viewer analytics

No failure may silently fall back to sending through another channel.

## Development milestones

### Milestone 1 — Contracts and fixture experience

- domain-to-GTM mapping schema
- typed contracts
- fixture-backed Executive Brief, Audience Map, Authority Planner, and Account Radar
- evidence and confidence disclosures
- feature flags defaulting to disabled
- no external sending

### Milestone 2 — Strategy engine

- context confirmation
- evidence normalization
- ICP, positioning, offer, content, and signal generation
- deterministic scoring
- human approval workflow
- strategy export

### Milestone 3 — CRM foundation

- Atomic CRM adapter
- companies, contacts, opportunities, evidence, consent, tasks, approvals, suppression
- idempotent writes and audit trail
- fixture and contract tests

### Milestone 4 — Vidyard bridge

- video brief and asset model
- Vidyard link/player references
- thumbnail/link email rendering
- supported analytics ingestion
- human-approved video actions
- plan/capability detection

### Milestone 5 — Unipile bridge

- hosted account connection
- Gmail/email send and reply synchronization
- supported LinkedIn/WhatsApp conversation synchronization
- webhooks and idempotency
- consent and suppression enforcement
- LinkedIn sending remains disabled until separately reviewed

### Milestone 6 — Attribution and QA

- funnel analytics
- direct/influenced/assisted attribution
- failure and reconciliation queues
- accessibility and responsive QA
- security and privacy review
- development pilot with test accounts
- documented production-readiness checklist

## Acceptance criteria

- A completed domain audit can generate a fixture-backed LinkedIn GTM Solution.
- The strategy shows positioning, ICPs, roles, pains, triggers, offers, content, and recommended actions.
- Every material recommendation has evidence, confidence, or an explicit hypothesis label.
- A user must confirm inferred business context before activation.
- An account recommendation cannot directly trigger a send.
- All outbound actions require recipient-level human approval.
- LinkedIn automation is disabled by default and prohibited actions are not implemented.
- Vidyard video briefs can be generated without exposing private or sensitive information.
- Gmail rendering supports a tracked Vidyard thumbnail/link and plain-text fallback.
- Unipile and Vidyard events are idempotently normalized when enabled.
- Atomic CRM retains consent, approvals, suppression, evidence, and relationship history.
- Fixtures cover missing data, low confidence, disconnected provider, withdrawn consent, duplicates, stale approvals, and failures.
- No browser bundle contains provider secrets.
- No demonstration value is presented as live provider data.
- No financial approval, revenue, reach, or conversion outcome is guaranteed.
- The feature remains development-only behind disabled feature flags.

## Validation

Before marking ready for review:

- lint and typecheck
- unit tests for scoring, evidence states, consent, suppression, idempotency, and attribution
- component tests for all GTM views
- contract tests for provider adapters
- webhook replay and duplicate-event tests
- end-to-end fixture workflow with zero external sends
- accessibility checks
- responsive checks
- dependency and secret scanning
- manual verification that production flags remain false

## References

- Unipile Getting Started: https://developer.unipile.com/docs/getting-started
- Unipile Send Email: https://developer.unipile.com/docs/send-email
- Unipile Send Messages: https://developer.unipile.com/docs/send-messages
- Vidyard Video Sales: https://www.vidyard.com/video-sales/
- Vidyard LinkedIn sharing: https://knowledge.vidyard.com/hc/en-us/articles/360009992133-How-to-share-Vidyard-videos-in-LinkedIn-direct-messages
- Vidyard developer API: https://developer.vidyard.com/
- LinkedIn account restrictions: https://www.linkedin.com/help/linkedin/answer/a1340522
