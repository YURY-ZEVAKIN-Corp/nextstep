# MyRadar Lead Scoring Model v1

## Goal

Prioritize inbound and discovered opportunities for outreach to decision-makers (`CEO`, `Head of Sales`) and maximize qualified leads per month.

## Qualification Definition

A lead is "qualified" when it meets all three:

- Clear business pain or growth signal linked to idea development or IT services
- Reachable target contact in leadership (`CEO`, `Head of Sales`, or equivalent)
- Plausible service fit with near-term engagement potential (within 90 days)

## Scoring Scale

- Total score range: `0-100`
- Lead status thresholds:
- `80-100`: `Tier A` (priority outreach within 24 hours)
- `60-79`: `Tier B` (outreach within 3 business days)
- `40-59`: `Tier C` (nurture and monitor)
- `0-39`: `Tier D` (archive, no active outreach)

## Weighted Criteria

| Dimension | Weight | Scoring Rules |
|---|---:|---|
| Service Fit | 30 | 0: no fit, 15: partial fit, 30: strong fit to idea dev/IT services |
| Buying Signal Strength | 25 | 0: none, 10: weak, 18: medium, 25: strong (urgent hiring, funding, roadmap shift, RFP) |
| Decision-Maker Access | 20 | 0: unknown contact, 10: indirect access, 20: direct named contact |
| Timing Urgency | 15 | 0: no timing, 8: medium-term (3-6 months), 15: near-term (<90 days) |
| Opportunity Size Potential | 10 | 0: unclear/low, 5: moderate, 10: high potential |

## Disqualifiers

Mark as `Disqualified` regardless of score if any apply:

- No relevant service match
- Invalid or unreachable organization/contact
- Clear conflict with legal/compliance restrictions

## Source Signals (All Sources Enabled)

Track and score opportunities from all available sources, including:

- Hiring/growth signals
- Funding and company news
- Job postings
- Tech stack changes
- Tenders/RFPs
- Competitor client wins
- Social posts and public announcements
- Internal referrals/CRM hints

## Outreach Priority Rules

- Prioritize `Tier A` and `Tier B` leads first
- If score tie: prioritize newest signal date, then highest service fit
- Re-score active leads weekly during pilot

## KPI Mapping

Primary KPI:

- `Qualified Leads / Month`

Pilot success target:

- `>=10 qualified leads/month`

Supporting metrics:

- Lead-to-qualified conversion rate
- Average score of qualified leads
- Time-to-first-outreach (days)
