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
- Protected integration boundary for future DataForSEO requests

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

## Status

The first interactive application has been built and validated successfully. Live DataForSEO connectivity, persistence, authentication, and CRM routing are the next milestones.
