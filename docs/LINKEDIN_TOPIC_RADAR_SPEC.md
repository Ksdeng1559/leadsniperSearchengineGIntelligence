# LinkedIn Trending Topic Intelligence — Implementation Request

## Objective

For every audited domain, identify emerging and rapidly growing LinkedIn topics that are commercially relevant to the business, its customers, services, industry, geography, and competitors.

The feature must produce evidence-backed topic intelligence and recommended SEO, AEO, content, offer, or monitoring actions. It must not claim complete access to LinkedIn.

## Product outcome

Add a **LinkedIn Topic Radar** to the Community Intelligence section of the customer audit.

The radar answers:

1. What topics are gaining attention among relevant LinkedIn authors and companies?
2. Which trends relate directly to the audited domain's products, services, customers, or geography?
3. Which competitors and industry voices are discussing them?
4. Is the apparent trend confirmed by search demand, news, or other communities?
5. What content or commercial action should the audited business take?

## Topic-universe generation

Extract and normalize the following from the audited domain:

- Brand and domain name
- Products and services
- Industries served
- Customer roles and audiences
- Problems solved and desired outcomes
- Locations and markets
- Competitors
- Executives and important entities
- Existing topic clusters, headings, FAQs, and schema entities
- DataForSEO keyword and content gaps

Expand each topic with relevant modifiers:

- trend, outlook, challenge, demand, growth
- regulation, technology, investment, funding
- hiring, expansion, acquisition, contract
- shortage, risk, declining, increasing
- best practice, case study, forecast, opinion

Store the source page or intelligence record that produced every seed topic.

## Discovery channels

### 1. Serper public-web discovery

Generate localized Google searches for publicly indexed LinkedIn content:

```text
site:linkedin.com/posts "{topic}" "{geography}"
site:linkedin.com/posts "{topic}" (trend OR outlook OR challenge)
site:linkedin.com/posts "{competitor}" "{topic}"
site:linkedin.com/pulse "{topic}"
site:linkedin.com/newsletters "{topic}"
```

Retain:

- Query
- Search locale
- Title
- Snippet
- Canonical URL
- Apparent author or company when supplied
- Published date when supplied
- SERP position
- Discovered and last-seen timestamps
- Content scope: `indexed_snippet`

### 2. LinkedIn-native analyst enrichment

Provide an analyst checklist or import workflow for authenticated LinkedIn searches using available native filters:

- Posts
- Date posted
- Latest/relevance sort
- Content type
- From member or company
- Mentioning member or company
- Author industry
- Author company

This is analyst-assisted evidence collection. Do not automate login, bypass access controls, or scrape private/member-only content.

### 3. Cross-source confirmation

Confirm candidate topics against one or more of:

- DataForSEO keyword trends and search demand
- Google News or Serper News
- Reddit, Quora, forums, YouTube, and reviews
- Google autocomplete and related searches
- Public company announcements
- Job or hiring signals when available

## Data schema

### `linkedin_topic_mentions`

- `id`
- `workspace_id`
- `audit_id`
- `topic_id`
- `query_id`
- `source_type`: indexed_linkedin, analyst_linkedin, news, search, community
- `title`
- `snippet`
- `canonical_url`
- `author_name` when publicly supplied
- `company_name` when publicly supplied
- `published_at`
- `discovered_at`
- `last_seen_at`
- `geography`
- `content_scope`
- `evidence_quality`
- `source_hash`

### `linkedin_topic_trends`

- `topic_id`
- `audit_id`
- `normalized_topic`
- `related_service`
- `related_audience`
- `current_7d_mentions`
- `current_30d_mentions`
- `previous_28d_weekly_average`
- `velocity_score`
- `unique_author_score`
- `engagement_score` when observed
- `buyer_relevance_score`
- `recency_score`
- `cross_source_score`
- `trend_score`
- `trend_stage`
- `confidence`
- `recommended_action`
- `first_seen_at`
- `last_seen_at`

## Trend scoring

Only calculate velocity when adequate historical snapshots exist.

```text
Trend Velocity =
current 7-day mentions / previous 28-day average weekly mentions
```

Normalize all components to 0–100:

```text
LinkedIn Trend Score =
  0.25 × Velocity
+ 0.20 × Unique Authors
+ 0.20 × Observed Engagement
+ 0.15 × Buyer Relevance
+ 0.10 × Recency
+ 0.10 × Cross-Source Confirmation
```

If engagement is unavailable, redistribute its weight proportionally across the observed components and display that adjustment.

Suggested stages:

| Score | Stage |
|---:|---|
| 80–100 | Breakout |
| 60–79 | Rapidly growing |
| 40–59 | Emerging |
| 20–39 | Established |
| 0–19 | Low or declining signal |

Do not label a topic trending from a single post. Require configurable minimums for mention count, unique authors, time coverage, and confidence.

## LinkedIn Topic Radar UI

Show:

- Topic and trend stage
- Trend score and confidence
- Seven-day and 30-day mention counts
- Velocity versus previous baseline
- Unique authors and companies
- Buyer-role and service relevance
- Geographic relevance
- Associated competitors
- Recurring viewpoint, question, or concern
- Cross-source confirmations
- First seen and latest seen
- Recommended action
- Evidence links and content-scope labels

Filters:

- Date range
- Trend stage
- Service/product
- Audience
- Geography
- Company/competitor
- Source type
- Confidence threshold
- Cross-source confirmation

## Recommended actions

Each topic must resolve to one primary recommendation:

- Publish an executive viewpoint
- Create an AEO answer
- Add or update an FAQ
- Create or improve a service page
- Publish a research report
- Produce a comparison or case study
- Create a calculator or assessment
- Monitor for another collection period
- No action

The recommendation must explain its relationship to the audited domain and cite its supporting evidence.

## Evidence and compliance boundaries

- Serper discovers Google-indexed LinkedIn results; it is not a LinkedIn feed API.
- Do not state that results represent all LinkedIn activity.
- Do not access private feeds, groups, or member-only information.
- Do not bypass authentication, robots controls, or platform restrictions.
- Preserve source links and attribution.
- Do not reproduce complete third-party posts.
- Clearly distinguish snippets, analyst-observed data, model classifications, and calculated trends.
- Minimize personal information and prioritize aggregate topic/company analysis.
- Allow evidence URL suppression and retention controls.

## Empty and partial states

The UI must support:

- Insufficient history to calculate velocity
- Indexed LinkedIn results unavailable
- Engagement unavailable
- No cross-source confirmation
- Topic below minimum evidence threshold
- Partial provider failure

Use "Insufficient evidence" rather than a zero score when required inputs are missing.

## Acceptance criteria

- An audit generates a domain-derived LinkedIn topic universe with source traceability.
- The system executes bounded Serper query families by topic and geography.
- Results are normalized, canonicalized, and deduplicated.
- Every displayed trend links to supporting public evidence.
- Indexed snippets and analyst-observed results are visibly distinguished.
- Trend velocity uses stored historical snapshots and never invents a baseline.
- Single posts cannot produce a trending classification.
- Missing engagement is disclosed and scoring weights are adjusted transparently.
- DataForSEO and at least one additional source can confirm candidate topics.
- The dashboard supports topic, date, geography, audience, company, and confidence filters.
- Every recommendation explains its relevance to the audited domain.
- Private LinkedIn content and unauthorized scraping remain out of scope.
- Automated tests cover query generation, deduplication, scoring, missing data, thresholds, evidence rendering, and partial failures.

## Suggested implementation sequence

1. Build domain topic-universe extraction and normalization.
2. Add LinkedIn-specific Serper query templates.
3. Implement mention and snapshot storage.
4. Add deduplication and entity resolution.
5. Build trend scoring with insufficient-history handling.
6. Add DataForSEO and news/community confirmation.
7. Build LinkedIn Topic Radar with fixture data.
8. Add analyst evidence-import workflow.
9. Add content recommendation mapping.
10. Add monitoring schedules, alerts, analytics, and tests.
