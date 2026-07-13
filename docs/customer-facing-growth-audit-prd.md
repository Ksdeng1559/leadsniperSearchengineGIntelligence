# Customer-Facing Business Growth Audit — Product Requirements

## Objective

Build a customer-facing audit experience that translates SEO, local-search, AI-visibility, social-intelligence, website, conversion, and competitive data into a clear business-growth report.

The customer must understand:

1. How customers currently find the business.
2. Where the business is losing visibility or qualified inquiries.
3. What competitors are doing better.
4. What prospective customers discuss publicly.
5. Which three actions should be implemented first.
6. Which findings are observed facts, calculated estimates, strategic assumptions, or unavailable data.

## User stories

- As a local business owner, I can submit my domain, market, category, and optional competitor.
- As a business owner, I can see a concise executive result before technical details.
- As a customer, I can understand each score and the evidence supporting it.
- As a customer, I can distinguish live data from estimates and recommendations.
- As a customer, I can see the three most valuable next actions.
- As a consultant, I can review the internal Growth Opportunity Profile.
- As an operator, I can route a qualified opportunity into LeadSniperAI and Atomic CRM.

## Audit intake

Required fields:

- Business domain
- Primary category
- Primary city, region, or market
- Primary service
- Report-delivery email
- Consent to analyze publicly accessible business information

Optional fields:

- Competitor domain
- Average client value
- Monthly lead capacity
- Primary growth objective
- Additional services and locations

## Processing states

1. Validate domain and block unsafe or internal addresses.
2. Confirm market and category.
3. Queue audit.
4. Display progress by workstream.
5. Produce partial results when a noncritical source is unavailable.
6. Display completion and report timestamp.
7. Offer email report and consultation next steps.

Required progress labels:

- Inspecting website
- Measuring search visibility
- Finding competitors
- Reviewing local presence
- Sampling AI visibility
- Discovering public customer conversations
- Calculating opportunities
- Preparing recommendations

## Customer report sections

### 1. Executive Growth Summary

Show:

- One-sentence conclusion
- Overall Search Growth Score
- Technical readiness
- Organic visibility
- Local visibility
- Commercial content coverage
- Conversion readiness
- AI visibility
- Social Intelligence alignment
- Estimated search opportunity
- Data completeness and confidence

Every score must open an explanation containing:

- What was measured
- Evidence used
- Date observed
- Limitations
- Recommended response

### 2. Current Search Visibility

Show:

- Ranking keywords
- Estimated organic visits
- Estimated organic traffic value
- Top pages
- Top-three, top-ten, and top-100 rankings
- Branded versus non-branded coverage
- Gained and lost rankings
- Commercial keywords outside the top ten

### 3. Local Search Performance

Show:

- Service-by-location visibility
- Local-pack observations
- Google Business Profile readiness
- Review comparison
- Local competitor comparison
- Missing location/service coverage
- Geographic areas not currently visible

Do not recommend thin city-swapped pages. A local page recommendation requires distinct demand, SERP differences, or meaningful localized information.

### 4. Customer Demand

For each priority keyword show:

- Keyword
- intent
- market
- monthly volume
- CPC
- difficulty
- current ranking
- best-ranking URL
- recommended action
- evidence source and date

### 5. Competitor Comparison

Compare:

- Ranking keywords
- commercial page coverage
- local-market coverage
- estimated traffic
- backlinks and referring domains
- sampled AI citations
- content strength
- conversion paths
- Search Growth Score

Separate direct business competitors from publishers, marketplaces, banks, government sources, and forums.

### 6. Technical Website Health

Classify findings:

- Critical
- High
- Medium
- Low

Every finding must include:

- What was detected
- affected pages
- why it matters
- business or search impact
- recommended fix
- estimated effort
- whether the owner or a specialist can address it

### 7. Content and Service Gaps

Show:

- Missing services
- weak existing pages
- missing customer segments
- unanswered questions
- comparison opportunities
- calculator and assessment opportunities
- outdated information
- internal-link gaps
- cannibalization risks

Recommended action must be one of:

- Create page
- Improve page
- Consolidate pages
- Build authority first
- No action

### 8. Social Intelligence and Voice of Customer

Show:

- Public signals captured
- source coverage
- recurring themes
- frequently asked questions
- active objections
- trust requirements
- urgency and provider-search signals
- competitor complaints and praise
- evidence-confidence distribution
- monthly trend

Theme records must show:

- Theme
- audience
- market
- source count
- first and latest detection
- recurrence
- intent
- urgency
- confidence
- recommended content or offer response
- public source links

Evidence boundary:

- Public, Google-indexed sources only
- No access to private or member-only groups
- No complete reproduction of discussions
- Preserve attribution and canonical links
- Clearly label model-generated sentiment and intent
- Do not create sensitive personal profiles

### 9. AI Visibility

Show:

- Questions sampled
- brand appearances
- competitor appearances
- sources cited
- cited pages
- entity gaps
- content opportunities
- observation date

Label all results as sampled visibility because generated responses may vary.

### 10. Conversion Review

Review:

- Primary CTA
- CTA placement
- service-specific assessments
- form friction
- booking path
- mobile experience
- trust signals
- response-time expectations
- objection handling
- follow-up readiness
- conversion measurement

### 11. Estimated Search Opportunity

Provide conservative, base, and upside scenarios.

Display assumptions for:

- Addressable demand
- expected CTR
- ranking probability
- website conversion rate
- lead-to-client rate
- average customer value

Use:

```text
Estimated visits = search demand × expected CTR × ranking probability
Estimated leads = estimated visits × website conversion rate
Estimated clients = estimated leads × lead-to-client rate
Estimated value = estimated clients × average customer value
```

Use the label Estimated Search Opportunity. Never present projections as guaranteed or as verified lost revenue.

### 12. Top Three Recommendations

Each recommendation must include:

- Priority
- finding
- supporting evidence
- business reason
- required actions
- expected impact
- estimated effort
- responsible role
- related CTA

### 13. 30-Day Action Plan

The free audit provides a bounded action plan containing up to five actions.

Suggested categories:

- Technical correction
- Core commercial-page improvement
- Local presence improvement
- Conversion asset
- Evidence-backed FAQ or content resource

### 14. Full 180-Day Roadmap

The expanded report supports:

| Phase | Days | Purpose |
| --- | ---: | --- |
| Foundation | 1–45 | Correct critical gaps and establish credibility |
| Growth | 46–90 | Expand visibility, content, and lead capture |
| Amplify | 91–135 | Build authority, partnerships, and AI visibility |
| Convert | 136–180 | Connect CRM, follow-up, attribution, and revenue |

### 15. Next step

Use context-specific CTAs:

- Build my 30-day growth plan
- Fix critical website issues
- Create my local SEO roadmap
- Review missed search opportunities
- Book a Business Growth Assessment
- Explore business-funding options

## Free and expanded report boundary

### Free audit

- One domain
- One primary market
- One competitor
- Top keyword and technical findings
- Basic local and social snapshot
- Three opportunities
- Five-action 30-day plan
- Summary estimate
- Consultation CTA

### Expanded analysis

- Multiple markets and competitors
- Full keyword universe
- Full technical crawl
- Backlink gaps
- Advanced AI and social monitoring
- Production content briefs
- Internal-link plan
- Full 180-day roadmap
- CRM attribution and monthly monitoring

## Internal Growth Opportunity Profile

Create an internal record containing:

- Search opportunity score
- website-modernization score
- local-lead score
- competitive-pressure score
- conversion-readiness score
- Social Intelligence score
- potential funding-need score
- estimated client value
- outreach priority
- confidence and data completeness
- recommended LeadSniperAI route

Potential routes:

- SEO
- Website redesign
- Local visibility
- Lead-generation campaign
- Reputation improvement
- Business-funding assessment
- Full Business Growth Assessment

## Data integrations

### DataForSEO

- Domain keywords and pages
- Search volume, CPC, trends, and intent
- Live localized SERPs
- Competitors
- Backlinks
- Technical crawl
- AI visibility where enabled

### Serper

- Public Reddit results
- Public Facebook results indexed by Google
- Forums and Q&A
- Public reviews
- Competitor discussions
- Emerging local topics

### LeadSniperAI

- Qualification
- opportunity prioritization
- recommended service
- confidence
- outreach readiness

### Atomic CRM

- Contact and company
- audit results
- consent
- assigned owner
- opportunity type
- follow-up stage
- booked consultation
- closed outcome and revenue

## Security and cost controls

- Server-side credentials only
- Domain and URL validation
- CAPTCHA and rate limits
- Email verification before expensive jobs
- Audit quotas by user and domain
- Request caching
- Bounded crawl and keyword counts
- Database endpoints before live endpoints
- Per-audit API cost logging
- Retention and deletion controls
- Partial-result handling
- No secrets in browser bundles or GitHub

## Analytics events

Track:

- Audit started
- domain validated
- audit completed
- section viewed
- recommendation expanded
- report emailed
- CTA clicked
- assessment started
- booking completed
- CRM opportunity created
- client outcome recorded

## Acceptance criteria

- A customer can submit a valid domain and market.
- Unsafe URLs are rejected.
- Progress is displayed by workstream.
- Partial source failures do not destroy the full report.
- Every metric shows its source type and observation date.
- Facts, estimates, assumptions, and unavailable data are visibly distinct.
- The report is readable on desktop and mobile.
- The top-three recommendations are visible without technical knowledge.
- Opportunity calculations expose assumptions.
- Social Intelligence displays only public evidence.
- AI visibility is labelled as sampled.
- The customer can request the report and choose a next step.
- A qualified audit can create an internal LeadSniperAI opportunity.
- DataForSEO and Serper credentials never reach browser code.
- Automated tests cover validation, scoring, partial failures, and report rendering.

## Implementation sequence

1. Define audit and report schemas.
2. Build the customer report route using fixture data.
3. Build reusable score, evidence, table, and recommendation components.
4. Add intake and progress states.
5. Add server-side DataForSEO adapter.
6. Add server-side Serper adapter.
7. Add scoring and estimate services.
8. Add LeadSniperAI routing.
9. Add Atomic CRM integration.
10. Add email-ready report generation.
11. Add analytics and error monitoring.
12. Validate accessibility, responsiveness, security, and cost controls.
