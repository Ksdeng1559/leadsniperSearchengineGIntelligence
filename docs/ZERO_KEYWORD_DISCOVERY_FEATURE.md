# Zero Keyword Discovery Feature — Product Requirements

## Objective

For every audited domain, discover, validate, prioritize, and monitor commercially relevant zero-volume, low-volume, and emerging keyword opportunities before they become obvious in conventional keyword reports.

The feature must combine DataForSEO keyword and SERP intelligence with domain context, community conversations, LinkedIn topics, news, autocomplete, related searches, competitor content, and optional Search Console evidence.

## Product principle

Search volume confirms established demand. Community, market, and first-party signals can reveal demand before it becomes established.

A reported zero must never be treated automatically as no demand. A null or missing value must never be silently converted to zero.

## User stories

- As a business owner, I can see emerging questions and topics relevant to my domain.
- As a strategist, I can distinguish measured zero, low volume, null data, and newly discovered phrases.
- As a content operator, I can prioritize early-mover opportunities by commercial value and evidence.
- As an analyst, I can inspect the sources and assumptions behind every recommendation.
- As an operator, I can monitor whether a zero-volume candidate begins generating impressions, searches, rankings, or leads.

## Inputs

Required:

- Audited domain
- Primary country or market
- Primary business category
- Primary products or services

Optional:

- City, province, or state
- Competitor domains
- Customer segments and buyer roles
- Average customer value
- Google Search Console connection
- Community Intelligence results
- LinkedIn Topic Radar results

## Discovery pipeline

### 1. Domain topic extraction

Extract and normalize:

- Products and services
- Industries and customer segments
- Customer problems and desired outcomes
- Geographic markets
- Technologies and methods
- Brand, executives, and business entities
- Headings, FAQs, schema entities, and internal anchor text
- Existing content clusters
- Missing competitor topics
- High-value service and conversion paths

Every seed topic must retain its origin page or evidence record.

### 2. DataForSEO keyword expansion

Use current DataForSEO endpoints as applicable:

- Google Ads Keywords for Site
- Google Ads Keywords for Keywords
- Google Ads Search Volume
- DataForSEO Labs Related Keywords
- DataForSEO Labs Keyword Overview
- Google Trends Explore or DataForSEO Trends
- Localized Live SERP
- Autocomplete, People Also Ask, and related-search data where available

Batch requests for cost efficiency and respect provider limits. Store endpoint, location, language, request time, provider update date, and response status.

### 3. External early-signal ingestion

Create candidate phrases from:

- LinkedIn Topic Radar
- Quora Question Intelligence
- Reddit and public forums
- YouTube titles and descriptions
- Public reviews
- News headlines and announcements
- Google autocomplete
- People Also Ask
- Related searches
- Competitor content changes
- Search Console queries and impressions

Do not require a candidate to exist in a keyword database before it can enter validation.

### 4. Candidate normalization

- Lowercase and normalize whitespace
- Preserve the original phrase
- Detect close variants and likely grouped terms
- Associate entities, service, audience, geography, and intent
- Deduplicate without discarding source history
- Flag synthetic or unnatural phrases
- Preserve question form when it reflects customer language

## Volume-status taxonomy

Every candidate must have one explicit status:

| Status | Definition |
|---|---|
| `measured_zero` | Provider explicitly returned search volume of zero |
| `low_volume` | Measurable volume within the configured low-volume threshold |
| `null_volume` | Provider returned a null metric |
| `not_returned` | Submitted phrase was absent from the provider response |
| `grouped_variant` | Phrase is likely consolidated with another keyword |
| `restricted` | Data is unavailable because of provider or advertising-policy restrictions |
| `insufficient_history` | Not enough historical information to assess growth |
| `new_candidate` | Discovered externally and not yet established in the keyword database |
| `validated_emerging` | Early signals meet configured evidence thresholds |
| `rejected` | Irrelevant, synthetic, duplicated, misleading, or commercially weak |

Store the raw provider state separately from the normalized classification.

## Candidate data model

### `zero_keyword_candidates`

- `id`
- `workspace_id`
- `audit_id`
- `original_phrase`
- `normalized_phrase`
- `canonical_keyword_id`
- `volume_status`
- `search_volume`
- `monthly_searches`
- `cpc`
- `paid_competition`
- `keyword_difficulty`
- `location`
- `language`
- `intent`
- `service`
- `audience`
- `geography`
- `provider`
- `provider_endpoint`
- `provider_updated_at`
- `collected_at`
- `first_seen_at`
- `last_seen_at`
- `grouped_with_keyword_id`
- `status_reason`

### `zero_keyword_signals`

- `candidate_id`
- `source_type`
- `source_url`
- `source_title`
- `evidence_excerpt`
- `author_or_company` when publicly supplied
- `published_at`
- `discovered_at`
- `content_scope`
- `signal_type`
- `signal_strength`
- `evidence_quality`
- `source_hash`

### `zero_keyword_scores`

- `candidate_id`
- `domain_fit`
- `commercial_intent`
- `community_signal`
- `trend_velocity`
- `cross_source_evidence`
- `serp_weakness`
- `authority_fit`
- `emerging_demand_score`
- `evidence_confidence`
- `recommended_action`
- `score_version`
- `scored_at`

## Validation workflow

For every viable candidate:

1. Request localized search-volume and historical metrics.
2. Assign the exact volume-status classification.
3. Check Google/DataForSEO Trends when sufficient data exists.
4. Inspect a localized live SERP.
5. Measure result relevance, freshness, authority, and commercial coverage.
6. Check community and LinkedIn evidence.
7. Check news and competitor evidence.
8. Check Search Console impressions when connected.
9. Calculate opportunity and confidence separately.
10. Recommend publish, monitor, consolidate, reject, or request human review.

## SERP weakness analysis

Measure:

- Exact-intent match
- Quality and freshness of top results
- Presence of forums or Q&A results
- People Also Ask and related searches
- Commercial page coverage
- Geographic match
- Weak, outdated, or mismatched answers
- Domain authority of ranking competitors
- Whether the audited domain can provide a materially better answer

Do not recommend content merely because volume is zero. Require relevant demand evidence and a credible ability to satisfy the intent.

## Scoring

Normalize all inputs to 0–100.

```text
Emerging Demand Score =
  0.20 × Domain Fit
+ 0.20 × Commercial Intent
+ 0.15 × Community Signals
+ 0.15 × Trend Velocity
+ 0.10 × Cross-Source Evidence
+ 0.10 × SERP Weakness
+ 0.10 × Authority Fit
```

Keep evidence confidence separate:

```text
Evidence Confidence =
  0.30 × Source Diversity
+ 0.25 × Recency
+ 0.20 × Data Completeness
+ 0.15 × Independent Authors
+ 0.10 × Search Evidence
```

When an input is unavailable, show it as unavailable. Do not silently substitute zero. Only redistribute scoring weight when the scoring version explicitly permits it and disclose the adjustment.

## Qualification rules

Default configurable thresholds for entering the opportunity queue:

- Domain Fit: at least 70
- Commercial Intent or Strategic Value: at least 50
- At least two independent signals
- At least one recent signal
- SERP is weak, outdated, fragmented, or mismatched
- Audited business has credible experience or expertise
- Evidence Confidence meets the configured minimum

High-priority accelerators:

- Search Console impressions already exist
- LinkedIn or community mentions are accelerating
- Google/DataForSEO Trends show growth
- CPC exists despite negligible reported volume
- Multiple independent buyer-role authors use related language
- Competitors recently introduced related products or content
- Candidate maps directly to a high-value service or tool

## Zero Keyword Discovery dashboard

### Executive cards

- Total candidates
- Validated emerging opportunities
- Measured-zero candidates
- Low-volume candidates
- Unknown/null candidates
- Social-first discoveries
- Search-first discoveries
- High-priority content opportunities
- New candidates since previous audit

### Emerging Keyword Radar

For every candidate show:

- Keyword
- Volume status
- Search volume and collection date
- 12-month history when available
- CPC, competition, and difficulty
- Discovery sources
- Mention velocity
- Domain and buyer relevance
- Commercial intent
- SERP weakness
- Emerging Demand Score
- Evidence Confidence
- Recommended asset
- Monitoring state
- Evidence links

### Filters

- Volume status
- Discovery source
- Service/product
- Audience
- Geography
- Intent
- Score range
- Confidence range
- First seen
- Recommended action
- Workflow state

### Candidate evidence drawer

Show:

- Original and normalized phrase
- Originating domain page or seed topic
- All provider responses and classifications
- Location, language, endpoint, and collection date
- Monthly search history
- Community and market sources
- SERP evidence
- Grouped-variant relationship
- Score explanation
- Limitations
- Recommended action

## Recommended actions

Each candidate receives one primary action:

- Create AEO answer
- Add or update FAQ
- Create article
- Create or improve service page
- Create comparison page
- Create industry or geographic resource
- Build calculator or assessment
- Publish research or executive viewpoint
- Consolidate with an existing topic
- Monitor
- Human review
- Reject

## Monitoring loop

- Store historical keyword metrics and topic snapshots.
- Revalidate high-priority candidates weekly or monthly based on configuration.
- Record Search Console impressions, clicks, average position, and query variants when connected.
- Detect transitions from zero/null to measurable volume.
- Track content created for each candidate.
- Measure indexing, rankings, impressions, leads, and attributed outcomes.
- Use results to recalibrate query templates and scoring weights.

## Customer audit output

The customer report should explain:

- Which emerging topics are relevant to the business
- Why traditional tools may report zero or no data
- What independent evidence suggests demand
- Which current search results fail to satisfy the intent
- What the business should publish or monitor
- Confidence, limitations, and expected learning period

Never promise future rankings or state that a candidate will definitely gain search volume.

## Cost and security controls

- Keep DataForSEO credentials server-side.
- Batch volume requests efficiently.
- Use audit-level keyword and endpoint budgets.
- Cache identical keyword/location/language requests.
- Prefer standard task methods for noninteractive jobs where cost-effective.
- Log cost by audit, endpoint, and candidate.
- Isolate tenant data.
- Validate all evidence URLs.
- Minimize personal data.
- Support retention, deletion, and evidence suppression.

## Empty and partial states

Support:

- No candidates discovered
- Search volume unavailable
- Trends data unavailable
- No Search Console connection
- SERP provider failure
- Community evidence unavailable
- Insufficient historical baseline
- Candidate below evidence threshold

Use "Insufficient evidence" instead of a misleading score of zero.

## Acceptance criteria

- An audit produces a traceable domain topic universe.
- DataForSEO expands domain and seed topics into candidate phrases.
- External community, LinkedIn, news, autocomplete, and Search Console candidates can enter the same pipeline.
- Every candidate has an explicit volume status.
- Null, missing, grouped, restricted, and zero values remain distinguishable.
- DataForSEO location, language, endpoint, collection date, and update date are retained.
- Candidates are canonicalized and deduplicated without losing evidence history.
- Every opportunity includes evidence links and separate opportunity/confidence scores.
- A zero-volume result alone cannot trigger a content recommendation.
- SERP weakness and domain authority fit are assessed.
- Search Console evidence is incorporated when authorized.
- The dashboard supports filtering and evidence inspection.
- Historical monitoring detects movement from zero/null to measurable demand.
- Automated tests cover provider response states, normalization, grouping, deduplication, scoring, missing data, thresholds, cost limits, and rendering.
- Credentials never reach browser code.

## Suggested implementation sequence

1. Define candidate, signal, score, and snapshot schemas.
2. Build domain topic extraction.
3. Add DataForSEO expansion and batch volume adapters.
4. Implement exact volume-status classification.
5. Add normalization, variant grouping, and deduplication.
6. Add Trends and localized SERP validation.
7. Ingest Community Intelligence and LinkedIn Topic Radar signals.
8. Add optional Search Console evidence.
9. Implement opportunity and confidence scoring.
10. Build fixture-backed Emerging Keyword Radar.
11. Add content recommendation workflow.
12. Add monitoring, cost controls, analytics, and automated tests.
