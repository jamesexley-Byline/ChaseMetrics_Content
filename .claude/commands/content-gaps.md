# Content Gaps — Find Under-Covered Divergences

Identify players where Byline has a strong data signal but no published content.

## Steps

1. **Scan the database** for every player entry in `database/chase-metrics-database.md`.

2. **Flag content gaps** where any of the following are true:
   - Byline Rank diverges from consensus ADP or ECR by 2+ rounds AND Content History is empty or has no article in the last 30 days
   - STATUS is NEEDS REVIEW and no editorial action has been noted for 7+ days
   - AGENT NOTES contain unresolved flags older than 7 days
   - A major news event (trade, injury return, coaching change) has occurred but no corresponding content exists

3. **Prioritise the list**:
   - Tier 1: Large divergence (3+ rounds) with no content — these are Byline's strongest potential takes
   - Tier 2: Moderate divergence (2 rounds) or stale NEEDS REVIEW flags
   - Tier 3: Recent news events without content coverage

4. **Produce report**: Create `reports/content-gaps-[YYYY-MM-DD].md` with:
   - Prioritised list of content gap players
   - For each: the data divergence, the news context, and why it matters
   - Suggested angle (data-only — not an editorial take, just what the data says)

## Constraints
- Do not recommend what Byline's position should be — that is editorial
- Present the gap, not the conclusion
- This report feeds the Cowork channel's editorial planning
