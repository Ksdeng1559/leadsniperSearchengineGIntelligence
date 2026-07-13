# LeadSniper SGI — Community & Social Intelligence Specification

**Status:** Implementation-ready product and data specification  
**Date:** July 13, 2026  
**Primary discovery provider:** Serper.dev  
**Supporting intelligence:** DataForSEO, permitted page retrieval, LLM classification

## 1. Product objective

Add a Community Intelligence module to LeadSniper SGI that discovers publicly indexed questions, discussions, reviews, complaints, comparisons, and business-growth signals. Convert this evidence into:

- Voice-of-customer themes
- SEO and AEO content opportunities
- Competitor weaknesses
- Product and service demand signals
- Evidence-backed business-development opportunities

Serper is the public-web discovery layer. It is not represented as a direct Quora, Reddit, Facebook, LinkedIn, or YouTube API.

## 2. Supported source classes

| Source | Discovery method | Primary use | Important limitation |
|---|---|---|---|
| Quora | `site:quora.com` Google queries | Questions, objections, comparisons | Indexed snippets; not complete answers or engagement |
| Reddit | `site:reddit.com` and subreddit queries | Candid problems, experiences, recommendations | Google coverage is incomplete |
| Public forums | Domain-specific and generic forum queries | Niche expertise and long-tail problems | Source formats vary |
| YouTube | Video search and `site:youtube.com` | Topics, descriptions, creator narratives | Comments are not reliably returned |
| Facebook | Publicly indexed page/group URLs | Public mentions and community topics | No private groups or authenticated content |
| LinkedIn | Publicly indexed post/company URLs | B2B announcements and professional topics | No private feed or complete engagement data |
| Reviews | Search, Maps, Places and review domains | Reputation, praise, complaints | Review text availability varies |
| News | Serper News | Growth events, contracts, expansion | News is not customer opinion |

## 3. Query engine

Create reusable query templates combining a topic, customer condition, geography, source and intent modifier.

### Quora templates

```text
site:quora.com "{topic}" "{geography}"
site:quora.com "{topic}" (best OR compare OR alternative)
site:quora.com "{topic}" (declined OR rejected OR qualify)
site:quora.com "{topic}" (cost OR rate OR fee)
site:quora.com "{topic}" (problem OR complaint OR experience)
```

### Cross-community templates

```text
(site:quora.com OR site:reddit.com) "{topic}" "{geography}"
"{topic}" (forum OR discussion OR community) "{geography}"
"{competitor}" (reviews OR complaint OR alternative OR experience)
"{business}" (expanding OR hiring OR renovation OR new location)
```

Query records must include locale, language, device when applicable, execution time, template version, and campaign/domain association.

## 4. Normalized data model

### `community_mentions`

| Field | Type | Description |
|---|---|---|
| `id` | UUID | Internal record identifier |
| `workspace_id` | UUID | Tenant boundary |
| `audit_id` | UUID | Associated domain audit |
| `query_id` | UUID | Originating query |
| `platform` | enum | quora, reddit, forum, youtube, facebook, linkedin, review, news, other |
| `source_domain` | text | Canonical source domain |
| `title` | text | Search-result title |
| `snippet` | text | Search-result excerpt |
| `url` | text | Canonical evidence URL |
| `published_at` | timestamp? | Supplied publication date |
| `discovered_at` | timestamp | First collection time |
| `last_seen_at` | timestamp | Most recent collection time |
| `serp_position` | integer? | Ranking at collection time |
| `content_scope` | enum | snippet_only, public_page_retrieved |
| `source_hash` | text | Deduplication fingerprint |
| `raw_payload_ref` | text? | Reference to retained provider payload |

### `community_insights`

| Field | Type | Description |
|---|---|---|
| `mention_id` | UUID | Evidence record |
| `intent_stage` | enum | awareness, research, comparison, eligibility, purchase, post_purchase |
| `insight_type` | enum | question, pain_point, objection, desired_outcome, praise, complaint, competitor, growth_signal |
| `topic_cluster` | text | Normalized subject |
| `entity_name` | text? | Company, product, or competitor |
| `geography` | text? | Inferred or explicit market |
| `sentiment` | decimal | -1.0 to +1.0 |
| `commercial_intent` | integer | 0–100 |
| `urgency` | integer | 0–100 |
| `relevance` | integer | 0–100 |
| `evidence_quality` | integer | 0–100 |
| `confidence` | integer | 0–100 |
| `reasoning_summary` | text | Short classification explanation |
| `recommended_action` | text? | Content, sales, product, or monitoring action |
| `model_version` | text | Classifier version for auditability |

## 5. Classification taxonomy

Every mention may receive multiple labels, but one primary insight type.

### Voice-of-customer

- Problem or pain point
- Question or knowledge gap
- Eligibility concern
- Price/rate/fee concern
- Trust or credibility objection
- Speed or convenience concern
- Desired business outcome
- Positive experience
- Negative experience
- Product comparison

### Business growth signals

- New location
- Hiring or workforce expansion
- Equipment requirement
- Renovation or construction
- Contract or purchase-order award
- Acquisition or ownership transition
- Inventory requirement
- Working-capital pressure
- Refinancing need
- Technology investment

Growth signals are hypotheses requiring corroboration. The UI must never state that a business definitively needs financing based only on a public mention.

## 6. Scoring

Normalize each component to 0–100.

```text
Community Opportunity Score =
  0.25 × Relevance
+ 0.20 × Commercial Intent
+ 0.15 × Recurrence
+ 0.15 × Recency
+ 0.15 × Evidence Quality
+ 0.10 × Content Gap
```

For content prioritization, enrich the topic with DataForSEO:

```text
Content Priority Score =
  Community Opportunity Score
  × Demand Multiplier
  × CPC Multiplier
  × Conversion-Intent Multiplier
  × Difficulty Adjustment
```

Recommended confidence caps:

- Search snippet only: maximum 70
- Public page retrieved and text supports classification: maximum 90
- Two independent public sources corroborate the signal: maximum 95
- Missing date or ambiguous entity: subtract 10–25 points

## 7. Dashboard requirements

### Executive overview

- Community Opportunity Score
- Total mentions and unique sources
- Questions discovered
- Pain points and objections
- High-intent topics
- Competitor complaints
- Growth signals requiring review
- New insights since the previous audit

### Quora Question Intelligence

- Top indexed Quora questions
- Question clusters and recurring language
- Intent stage and commercial-intent score
- Existing-site coverage status
- Competitor coverage status
- Recommended page or FAQ
- Evidence URL, snippet, date and confidence

### Voice-of-Customer Explorer

Filters:

- Date range
- Platform
- Topic cluster
- Insight type
- Sentiment
- Intent stage
- Geography
- Confidence threshold
- Competitor/entity

### Content Opportunity Queue

For each opportunity show:

- Proposed title and target question
- Recommended format: FAQ, AEO answer, article, landing page, comparison, calculator
- Source evidence count
- Search volume, CPC and competition when available
- Content-gap status
- Priority score
- Draft/approved/published workflow state

### Evidence drawer

Every insight must provide the original query, title, snippet, source URL, collection time, content scope, and classification confidence. Clearly label search snippets as snippets.

## 8. Audit customer output

The customer-facing audit should answer:

1. What are customers publicly asking about this market?
2. Which problems and objections recur most often?
3. Which of these questions does the audited website fail to answer?
4. Which competitors appear for these conversations?
5. What content should be created first?
6. Are there credible public growth signals worth human review?

Recommended report blocks:

- Social Listening Snapshot
- Top Customer Questions
- Voice-of-Customer Themes
- Reputation and Competitor Findings
- SEO/AEO Content Gaps
- 30/60/90-Day Content Actions

## 9. Processing workflow

1. Generate queries from topic, competitor, geography and intent libraries.
2. Submit localized requests to Serper with retry and quota controls.
3. Normalize results and canonicalize URLs.
4. Deduplicate by canonical URL plus normalized title/snippet hash.
5. Retrieve only permitted public pages; otherwise retain snippet-only evidence.
6. Classify intent, theme, sentiment, urgency and confidence.
7. Aggregate recurring topics across sources and collection periods.
8. Enrich selected topics with DataForSEO metrics.
9. Generate dashboard recommendations with citations to evidence records.
10. Require human review before exporting a growth signal to a CRM workflow.

## 10. API and operational controls

- Store the Serper API key only in server-side secrets.
- Enforce tenant isolation and role-based access.
- Add per-workspace daily query budgets and global rate limiting.
- Cache identical query/locale combinations for a configurable period.
- Retain first-seen and last-seen timestamps for trend analysis.
- Respect source access restrictions and avoid bypassing authentication or robots controls.
- Minimize personal data; focus analysis on topics, organizations and aggregate patterns.
- Provide removal/suppression controls for individual evidence URLs.
- Preserve source attribution and do not republish full third-party answers.

## 11. Acceptance criteria

- Users can run an audit by domain, topic, geography and competitor set.
- Quora, Reddit, forums, reviews, YouTube and public social results share one normalized schema.
- Each displayed insight links to evidence and shows a confidence score.
- Quora results are explicitly labelled as Google-indexed results.
- The system does not claim access to private or complete platform data.
- Duplicate results are consolidated without losing source history.
- Topics can be enriched with DataForSEO metrics.
- High-priority insights produce actionable SEO/AEO content recommendations.
- Growth signals require human approval before CRM activation.
- Historical snapshots support trend and new-since-last-audit comparisons.

## 12. Suggested delivery phases

### Phase 1 — Discovery MVP

Serper query templates, normalized storage, source filters, evidence drawer, Quora/Reddit question views.

### Phase 2 — Intelligence

LLM classification, clustering, scoring, sentiment, content-gap mapping and DataForSEO enrichment.

### Phase 3 — Activation

Content briefs, audit exports, monitoring schedules, alerts and human-approved Atomic CRM opportunity creation.

### Phase 4 — Learning loop

Measure which insights become published content, rankings, leads and funded opportunities; use results to recalibrate query templates and scoring weights.

