# Flag Review — Review All NEEDS REVIEW Entries

List all players with unresolved flags for James to triage at the start of a session.

## Steps

1. **Scan the database** for all entries where STATUS = NEEDS REVIEW.

2. **For each flagged entry**, pull:
   - Player name and position
   - Date the flag was set
   - The conflict or issue described in AGENT NOTES
   - The sources that conflict
   - Days since flagged

3. **Sort by severity**:
   - First by size of data conflict (larger ADP divergence = higher priority)
   - Then by time since flagged (older flags first)
   - Then by player ADP (higher-drafted players are more urgent)

4. **Present as a clean list** designed for quick triage. For each player:
   ```
   ### [PLAYER NAME] — [POSITION], [TEAM]
   Flagged: [DATE] ([X] days ago)
   Issue: [One-line summary of the conflict]
   Sources: [Conflicting sources listed]
   Action needed: [Resolve STATUS, update ranking, or dismiss flag]
   ```

5. **Output to console** (not a file) — this is a quick-reference tool for the start of a session.

## Constraints
- Do not resolve flags yourself — this is for James to decide which to bring into the Cowork channel
- Present the conflict clearly without recommending a resolution
