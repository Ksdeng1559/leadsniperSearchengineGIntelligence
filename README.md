# LeadSniper Search Growth Intelligence

A revenue-focused SEO, local-search, and AI-visibility platform for discovering growth opportunities among local service businesses.

The product combines DataForSEO intelligence with LeadSniperAI opportunity qualification. Its purpose is not merely to report rankings: it identifies where a business is missing visibility, leads, and revenue, then recommends the next commercially valuable action.

## Product vision

LeadSniper Search Growth Intelligence helps consultants, agencies, financial professionals, and local businesses answer four questions:

1. Where is the business losing search visibility?
2. Which competitors are capturing that demand?
3. Which improvements could produce qualified leads?
4. Should the opportunity be routed to SEO, website development, lead generation, or business funding?

## Current application

The initial MVP includes:

- Responsive search-growth dashboard
- Free local-business audit form
- Search Growth Score
- Keyword opportunity table
- Commercial opportunity scoring
- Revenue-opportunity presentation
- Local SEO and AI-visibility navigation
- LeadSniperAI Growth Opportunity Profile
- Clear demonstration-data disclosure
- Protected integration boundary for future DataForSEO and Serper requests
- Community Intelligence and Voice-of-Customer roadmap
- LinkedIn Topic Radar specification
- Zero Keyword Discovery feature specification

> The current interface uses demonstration data. It is not yet connected to a live DataForSEO account.

## Free Local Business Growth Audit

The public audit is designed as a useful lead-generation experience rather than a disguised contact form.

### Audit inputs

- Business website
- Primary market
- Business category
- Optional competitor
- Contact information for report delivery in a later milestone

### Audit outputs

- Overall Search Growth Score
- Technical readiness
- Organic visibility
- Commercial keyword coverage
- Local-search visibility
- Basic AI visibility
- Top competitor gap
- Three priority opportunities
- Recommended next action
- Estimated search opportunity with explicit assumptions

All results must clearly distinguish:

- DataForSEO-derived data
- Calculated estimates
- Strategic recommendations
- Missing or unavailable data

## LeadSniperAI opportunity routing

The audit creates an internal Growth Opportunity Profile for each business.

| Signal | Recommended route |
| --- | --- |
| Strong demand with weak rankings | SEO growth plan |
| Traffic with weak conversion paths | Conversion and website redesign |
| No website or materially outdated website | Local-service website package |
| Weak local presence | Google Business Profile and local SEO |
| Strong competitors with clear content gaps | Competitor-gap campaign |
| Visibility without sufficient inquiries | Lead-generation campaign |
| Expansion, equipment, or acquisition signals | Business-funding assessment |
| Multiple validated needs | Full Business Growth Assessment |

Suggested internal scores:

- Search opportunity
- Website modernization
- Local lead potential
- Competitive pressure
- Conversion readiness
- Growth signals
- Potential funding need
- Outreach priority
- Data completeness and confidence

## Opportunity scoring

The planned 100-point model is:

| Component | Weight |
| --- | ---: |
| Commercial value | 25 |
| Ranking feasibility | 20 |
| Traffic potential | 15 |
| AEO and AI-citation potential | 15 |
| Strategic fit | 15 |
| Production efficiency | 10 |

The system should recommend one of four actions:

- Create a page
- Improve an existing page
- Consolidate competing pages
- Build authority before targeting the term

## Technology

Current MVP:

- React
- Vite
- CSS
- GitHub-based development workflow

Planned production services:

- Protected server-side API
- DataForSEO REST API
- Project and audit storage
- Job queue and caching
- LeadSniperAI qualification
- Atomic CRM routing
- Email report delivery
- Analytics and conversion attribution

For a production SaaS application, the DataForSEO REST API is preferred over exposing MCP directly to browser users. MCP can remain useful for agent-driven research and internal analysis.

## Local development

Requirements:

- Node.js 20 or newer
- npm

Install and run:

```bash
npm install
npm run dev
```

Create a production build:

```bash
npm run build
```

## Environment variables

Copy `.env.example` to `.env.local`:

```env
DATAFORSEO_LOGIN=
DATAFORSEO_PASSWORD=
DATAFORSEO_API_BASE=https://api.dataforseo.com/v3
```

Security requirements:

- Never commit `.env`, `.env.local`, tokens, passwords, or API credentials.
- Never call DataForSEO directly from browser code.
- Store credentials in protected deployment environment variables.
- Proxy requests through an authenticated server-side service.
- Validate domains and reject localhost, internal IPs, and unsafe URLs.
- Rate-limit, queue, cache, and meter audit requests.
- Record API cost by project, user, and endpoint.

## Planned DataForSEO audit pipeline

1. Normalize and validate the submitted domain.
2. Discover ranked keywords and top pages.
3. Retrieve keyword volume, CPC, intent, trends, and difficulty.
4. Identify SERP and organic competitors.
5. Run a bounded technical crawl.
6. Evaluate priority local SERPs.
7. Inspect backlinks and referring-domain gaps when enabled.
8. Sample AI Overview and ChatGPT visibility when enabled.
9. Calculate visibility, opportunity, and confidence scores.
10. Produce the customer audit and internal Growth Opportunity Profile.
11. Route qualified opportunities into LeadSniperAI and Atomic CRM.

## Social Intelligence

The Social Intelligence component uses the Serper Google Search API to discover publicly indexed community conversations related to a business, service, market, competitor, or customer problem.

### Sources

- Public Reddit posts and comments indexed by Google
- Public Facebook pages, public group pages, and indexed discussion results
- Industry forums and community websites
- Public review pages and question-and-answer sites, including Google-indexed Quora questions
- Publicly indexed LinkedIn posts, articles, and newsletters
- Public YouTube discussion pages and other indexed social results

Serper is a real-time Google Search API with country and language localization. It is a discovery layer, not direct access to social platforms. Private Facebook groups, login-protected content, deleted posts, member-only discussions, and content excluded from Google indexing are outside scope.

### Intelligence outputs

- Recurring customer pain points
- Purchase and provider-search intent
- Urgency and funding-need signals
- Common objections and trust concerns
- Competitor praise and complaints
- Language customers use to describe problems
- Frequently requested services
- Local community topics
- Emerging demand and content ideas
- Source links and evidence timestamps

### Query strategy

The service should create bounded searches such as:

```text
site:reddit.com "<service>" "<city>"
site:reddit.com "<problem>" "<province>"
site:facebook.com/groups "<service>" "<city>"
site:facebook.com "<business category>" "<location>"
"<competitor>" reviews complaints
"<service>" recommendations "<city>"
```

Queries must be generated server-side, deduplicated, localized, cached, and attributed to the original public source.

### Social opportunity scoring

Each signal can be evaluated for:

| Component | Suggested weight |
| --- | ---: |
| Commercial intent | 25 |
| Urgency | 20 |
| Local relevance | 15 |
| Recurrence | 15 |
| Service alignment | 15 |
| Evidence confidence | 10 |

Social signals should influence the Growth Opportunity Profile but should not be treated as verified facts about an individual or business without corroboration.

### Privacy, evidence, and content rules

- Use only publicly accessible, Google-indexed results.
- Do not attempt to access private groups or bypass authentication.
- Preserve source attribution and canonical links.
- Store short evidence excerpts, structured observations, and hashes rather than copying complete discussions.
- Do not build personal profiles from sensitive information.
- Avoid outreach based on protected or highly sensitive personal characteristics.
- Provide removal and retention controls.
- Label inferred sentiment, intent, and opportunity signals as model-generated classifications.
- Respect Serper and source-platform terms, copyrights, and applicable privacy laws.

### Serper environment variables

```env
SERPER_API_KEY=
SERPER_API_BASE=https://google.serper.dev
```

The API key must be stored as a protected server-side environment variable and must never be included in browser code.

## LinkedIn Topic Radar

The LinkedIn Topic Radar identifies topics gaining attention among authors, companies, competitors, and buyer roles relevant to the audited domain.

The system derives its topic universe from the domain's services, audiences, problems, locations, entities, competitors, FAQs, and keyword gaps. It then combines:

- Serper searches for publicly indexed LinkedIn posts, articles, and newsletters
- Optional analyst-assisted LinkedIn-native search
- Seven-day and 30-day historical snapshots
- Unique-author and buyer-relevance signals
- DataForSEO trend and demand validation
- News and Community Intelligence confirmation
- Evidence-backed content and commercial recommendations

A single post cannot qualify a topic as trending. Trend labels require minimum mention, author, time-coverage, and confidence thresholds. Missing engagement or historical data must be disclosed.

Planned dashboard outputs:

- Breakout, rapidly growing, emerging, established, and declining topics
- Trend velocity and confidence
- Relevant authors, companies, competitors, services, audiences, and locations
- Cross-source confirmation
- Recommended AEO answer, FAQ, article, service page, research report, calculator, or monitoring action

Serper is an indexed-web discovery layer, not a complete LinkedIn feed API. Private content, automated login, and access-control bypasses remain out of scope.

## LinkedIn GTM Solution Bridge

The planned LinkedIn GTM Solution Bridge converts a completed domain audit into an evidence-backed LinkedIn selling strategy.

It will combine:

- Search Growth and conversion findings
- Community and Voice-of-Customer language
- LinkedIn Topic Radar evidence
- Zero Keyword and emerging-demand signals
- ICP, buying-role, trigger, offer, and content recommendations
- Human-reviewed account research and next-best actions
- Vidyard personalized-video briefs and engagement
- Unipile-connected Gmail and supported conversation synchronization
- Atomic CRM relationship, consent, approval, opportunity, and attribution records

The bridge is development-only and does not implement automated LinkedIn connection requests, likes, comments, scraping, or autonomous direct messages. Every outbound action requires recipient-level human approval. Provider integrations and production sending remain disabled behind feature flags until security, privacy, consent, platform-policy, and end-to-end tests pass.

Detailed implementation request: [LinkedIn GTM Solution Bridge](docs/LINKEDIN_GTM_SOLUTION_BRIDGE.md)

## Zero Keyword Discovery

The Zero Keyword Discovery feature finds commercially relevant emerging phrases before conventional keyword tools show meaningful search volume.

### Discovery sources

- Audited-domain products, services, audiences, problems, and entities
- DataForSEO Keywords for Site, Keywords for Keywords, Related Keywords, and Keyword Overview
- Google Ads search-volume history
- Google Trends and DataForSEO Trends
- Localized live SERPs
- LinkedIn, Quora, Reddit, forums, YouTube, reviews, and news
- Autocomplete, People Also Ask, and related searches
- Competitor content
- Optional Google Search Console queries and impressions

### Volume classification

Every candidate must preserve its exact data state:

- Measured zero
- Low volume
- Null volume
- Not returned
- Grouped variant
- Restricted
- Insufficient history
- New candidate
- Validated emerging
- Rejected

Null, missing, restricted, and grouped values must never be silently converted to zero. A zero-volume result alone cannot trigger a content recommendation.

### Scoring and outputs

The feature maintains two separate measures:

- **Emerging Demand Score:** domain fit, commercial intent, community signals, trend velocity, cross-source evidence, SERP weakness, and authority fit
- **Evidence Confidence:** source diversity, recency, completeness, independent authors, and search evidence

The Emerging Keyword Radar shows volume status, search history, CPC, difficulty, discovery sources, buyer relevance, SERP weakness, recommended content, evidence links, and monitoring state.

High-priority candidates may produce:

- AEO answers and FAQs
- Articles and executive viewpoints
- Service, comparison, industry, or geographic pages
- Calculators and assessments
- Research reports
- Monitor, consolidate, human-review, or reject decisions

Historical monitoring should detect movement from zero or null data to measurable demand and connect published content to impressions, rankings, leads, and attributed outcomes.

## Cost controls

A free audit must be deliberately bounded:

- Verify the user before expensive research
- Limit audits per domain and user
- Cache repeated domains and keywords
- Use database endpoints before live SERPs
- Limit competitors, crawl depth, and keyword count
- Queue audits rather than running unlimited synchronous jobs
- Reserve deeper backlink and AI analysis for qualified or paid users
- Monitor DataForSEO spend and enforce plan-level budgets

## Development roadmap

### Phase 1 — Interface MVP

- [x] Search-growth dashboard
- [x] Free-audit form
- [x] Keyword opportunity presentation
- [x] LeadSniperAI routing concept
- [x] Responsive layout
- [x] Production build validation

### Phase 2 — Live audit foundation

- [ ] Protected server-side service
- [ ] DataForSEO authentication
- [ ] Domain validation and abuse controls
- [ ] Job queue and request caching
- [ ] Live domain overview
- [ ] Live keyword and competitor results
- [ ] Audit persistence

### Phase 3 — Conversion and operations

- [ ] Email-ready audit report
- [ ] Consultation booking
- [ ] Atomic CRM lead creation
- [ ] LeadSniperAI qualification workflow
- [ ] Consent and follow-up tracking
- [ ] Organic lead and revenue attribution

### Phase 4 — Advanced intelligence

- [ ] Social Intelligence discovery through Serper
- [ ] Community pain, intent, objection, and trend clustering
- [ ] Quora Question Intelligence
- [ ] LinkedIn Topic Radar and historical trend velocity
- [ ] Zero Keyword Discovery and Emerging Keyword Radar\n- [ ] LinkedIn GTM Solution Bridge\n- [ ] Vidyard personalized video engagement\n- [ ] Unipile unified messaging and Gmail bridge\n- [ ] Atomic CRM GTM attribution and approval workflow
- [ ] DataForSEO zero/null/grouped volume-state classification
- [ ] Search Console emerging-query validation
- [ ] Technical site audit
- [ ] Local rank tracking
- [ ] Backlink and authority gaps
- [ ] AI Overview and ChatGPT visibility
- [ ] Content briefs and internal-link plans
- [ ] Scheduled 30-day growth reviews

## Data and claims

Search volumes, CPC, rankings, traffic estimates, citations, competitors, leads, and revenue must never be fabricated. Calculated opportunity estimates must show their assumptions and must not be presented as guaranteed outcomes.

## Repository workflow

Development should occur on feature branches with draft pull requests. The initial application branch is:

```text
agent/initial-application
```

## Active development

- [PR #1 — Initial Search Growth Intelligence application](https://github.com/Ksdeng1559/leadsniperSearchengineGIntelligence/pull/1)
- [PR #2 — Customer audit with Community & Social Intelligence](https://github.com/Ksdeng1559/leadsniperSearchengineGIntelligence/pull/2)
- [PR #3 — Zero Keyword Discovery Feature](https://github.com/Ksdeng1559/leadsniperSearchengineGIntelligence/pull/3)\n- LinkedIn GTM Solution Bridge — draft PR in development

## Status

The first interactive application, customer-audit specification, Community Intelligence architecture, LinkedIn Topic Radar, and Zero Keyword Discovery specification have been created. Live DataForSEO and Serper connectivity, persistence, authentication, historical monitoring, LeadSniperAI qualification, and Atomic CRM routing are the next milestones.
