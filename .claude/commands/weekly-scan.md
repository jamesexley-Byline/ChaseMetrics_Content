# Weekly Scan — Chase Metrics Database Maintenance

Run the full weekly maintenance sweep of the Player Intelligence Database.

## Steps

1. **News sweep**: Search the web for fantasy-relevant NFL news from the past 7 days. Focus on:
   - Injury reports and designations (questionable, doubtful, out, IR)
   - Trades, signings, and roster cuts
   - Depth chart changes and coaching comments on usage
   - OTA/camp reports during offseason, practice reports during season
   - Suspension news

2. **ADP pull**: Search for current ADP data from:
   - FantasyPros consensus ADP
   - Underdog Fantasy best-ball ADP
   - ESPN draft ADP
   For each player currently in `database/chase-metrics-database.md`, compare stored ADP against current values.

3. **Flag movers**: For any player whose ADP has shifted 2 or more rounds since the last stored value:
   - Update the ADP field(s) in the database
   - Log the change in `database/ranking-change-log.md`
   - Add context to AGENT NOTES explaining the likely driver

4. **Status updates**: For any player with a confirmed status change:
   - Update the STATUS field
   - Log the change
   - If the status change is ambiguous or conflicting across sources, set STATUS to NEEDS REVIEW and document the conflict in AGENT NOTES

5. **New player entries**: If a player not in the database has become fantasy-relevant (breakout candidate, trade target, rookie with rising ADP):
   - Create a new entry using the full schema from CLAUDE.md
   - Populate all data fields
   - Leave THE TAKE, CONFIDENCE, and CONTENT HISTORY blank (marked as awaiting editorial)
   - Log the new entry in the ranking change log

6. **Content gap check**: Scan for players where:
   - Byline Rank diverges from consensus ADP/ECR by 2+ rounds
   - No article exists in their Content History
   - Flag these in the weekly summary as potential content opportunities

7. **Produce weekly summary**: Create `reports/weekly-scan-[YYYY-MM-DD].md` with:
   - Total players updated
   - List of all field changes with old → new values
   - Players flagged as NEEDS REVIEW
   - Content gaps identified
   - Any new entries created

## Constraints
- Never modify THE TAKE, CONFIDENCE, or CONTENT HISTORY fields
- Every change gets a log entry in the ranking change log
- If uncertain, flag as NEEDS REVIEW — do not guess
- Cite sources for every data point
