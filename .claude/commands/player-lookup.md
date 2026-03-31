# Player Lookup — On-Demand Data Pull

Pull current data for a specific player and produce a pre-populated data block.

The player name will be provided as the argument to this command.

## Steps

1. **Check existing entry**: Look in `database/chase-metrics-database.md` for an existing entry for this player.

2. **If the player exists**:
   - Search the web for their current ADP (FantasyPros, Underdog, ESPN)
   - Search for their current ECR positional ranking
   - Search for recent news (last 14 days) — injuries, depth chart, usage trends
   - Update all data fields in the existing entry
   - Log all changes in `database/ranking-change-log.md`
   - Add any new context to AGENT NOTES
   - Do NOT touch THE TAKE, CONFIDENCE, or CONTENT HISTORY

3. **If the player does not exist**:
   - Create a new entry using the full schema
   - Search for all data fields: ADP, ECR, target share, snap count, red zone targets
   - Search for recent news and context
   - Populate THE DATA and AGENT NOTES
   - Leave THE TAKE, CONFIDENCE, and CONTENT HISTORY blank (awaiting editorial)
   - Log the new entry in the ranking change log

4. **Produce data block**: Create `reports/player-lookup-[PLAYER_NAME]-[YYYY-MM-DD].md` containing:
   - The complete data section for this player
   - A summary of what changed since the last update (if existing entry)
   - Any flags or conflicts found
   - This file is designed to be brought into the Cowork channel for editorial work

## Constraints
- Never modify THE TAKE, CONFIDENCE, or CONTENT HISTORY
- Cite all sources
- Flag conflicts as NEEDS REVIEW
